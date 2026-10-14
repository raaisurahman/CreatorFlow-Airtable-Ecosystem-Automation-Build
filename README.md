# CreatorFlow: Airtable Ecosystem & Automation Build
 
A centralized "Single Source of Truth" for a TikTok creator management agency, managing 2,000+ creators. The system replaces fragmented tools (Lark, Google Sheets, Discord, WhatsApp) with an integrated Airtable base, Fillout forms, Make.com scenarios, and the WhatsApp Cloud API.
 
![CreatorFlow Airtable base](./docs/reference-photo.png)
 
## Overview
 
| | |
|---|---|
| **Client** | TikTok Creator Management Agency |
| **Category** | Social Media / Creator Economy |
| **Date** | May 2026 |
| **Author** | Sadi Rahman |
 
## The Problem
 
- **No single source of truth:** Creator data was split across Google Sheets and Lark, with no real-time view of business health.
- **Manual onboarding:** Collecting IDs, preferences, and contact info was slow and error-prone.
- **Scalability limits:** Tagging 2,000+ creators individually on Discord and WhatsApp was unsustainable.
- **Revenue risk:** TikTok binding dates were tracked by hand, so renewals were sometimes missed.
- **High operational cost:** Routine tagging and engagement messages consumed hours of staff time daily.
## Objectives
 
1. Migrate all workflows into one centralized Airtable system.
2. Automate onboarding with multi-step dynamic forms that collect structured data.
3. Alert admins to binding deadlines to eliminate revenue leakage.
4. Broadcast vouchers and offers to targeted creators at scale.
5. Keep private WhatsApp groups active without manual effort.
## Architecture
 
| Layer | Tool | Role |
|---|---|---|
| Database | Airtable | Single source of truth for creator data, statuses, and timelines |
| Data collection | Fillout | Multi-step onboarding and admin forms |
| Automation logic | Make.com, Airtable Scripting | Webhook processing, conditional logic, data integrity scripts |
| Communication | WhatsApp Cloud API, Discord API | Direct messages, group automation, community posts |
| Scheduling | Calendly | Strategy call bookings and reminder sequences |
 
## Key Workflows
 
### 1. Onboarding & Data Integrity
- Creators complete a multi-step Fillout form covering strategy calls and product interests.
- Submissions reach Airtable instantly via webhooks.
- Creators often change TikTok usernames, so the system extracts the immutable numeric TikTok ID. A script periodically uses it to refresh the current username, so records never go stale.
### 2. TikTok Binding Management
TikTok has no public API for binding management, so the system works around it:
1. Airtable calculates the Binding End Date from contract start dates and renewal cycles.
2. An automation monitors these dates.
3. At 60 days remaining, a WhatsApp message goes to the admin team with the creator's details and a direct link to update the binding date.
### 3. Voucher Distribution (Discord & WhatsApp)
1. An admin submits a form in Airtable with the product, voucher code, and target segments.
2. Make.com receives the request via webhook.
3. The system posts to Discord, tagging each creator individually rather than using a blanket `@here`.
4. Creators with a WhatsApp number on file receive the same offer by direct message.
### 4. Appointment No-Show Prevention
Calendly bookings trigger reminders over WhatsApp and Discord at 24 hours, 30 minutes, and 5 minutes before each call.
 
### 5. WhatsApp Ice-Breaker Automation
- The system tracks the last incoming message in each creator's WhatsApp group.
- After 72 hours of silence, it sends a personalized check-in message.
- Runs through Airtable Scripting and Make.com across hundreds of active groups.
## Technical Efficiency
 
- **Webhooks over polling:** Replaced 15-minute Make.com polling with custom webhooks. Automations run instantly and use far fewer operations.
- **Airtable Scripting:** Complex logic that native Airtable automations couldn't handle is written in JavaScript inside Airtable. This reduces reliance on paid middleware and keeps logic close to the data.
## Results
 
| Metric | Before | After |
|---|---|---|
| Platforms in use | 4 (Lark, Sheets, Discord, WhatsApp) | 1 integrated ecosystem |
| Creator data visibility | Fragmented, manual lookup | Real-time, centralized dashboard |
| Voucher distribution | Hours of manual tagging | Instant, automated |
| Binding date tracking | Manual, error-prone | Automated 60-day alerts |
| WhatsApp engagement | Manual, inconsistent | Automated 72-hour ice-breakers |
| Data accuracy | Degraded by username changes | Auto-synced via numeric TikTok ID |
 
The agency can now scale past 2,000 creators without adding administrative headcount.
 
## Tech Stack
 
`Airtable` · `Fillout` · `Make.com` · `Airtable Scripting (JavaScript)` · `WhatsApp Cloud API` · `Discord API` · `Calendly`
 

```
 
## Author
 
**Md Raaisur Rahman**: Freelance automation specialist (Airtable, Make.com)
 
