# 🎓 University of Dubai — Conference Registration System (CRS)
## Screen Layout & Design Specification Document · v1.0

---

> **Document Status:** Draft — For Review
> **Version:** 1.0
> **Date:** May 2025
> **Prepared by:** Research Affairs
> **Audience:** IT Development Team · UI/UX Team
> **Classification:** Confidential — Internal Use Only
> **Reference PRD:** CRS PRD v2.0

---

## 📋 Table of Contents

1. [Design System & Global Standards](#1-design-system--global-standards)
2. [Global Shell & Navigation](#2-global-shell--navigation)
3. [Screen 01 — Login Page](#3-screen-01--login-page)
4. [Screen 02 — Faculty: Home Dashboard](#4-screen-02--faculty-home-dashboard)
5. [Screen 03 — Faculty: New Application Form](#5-screen-03--faculty-new-application-form)
6. [Screen 04 — Faculty: Application Status & Detail View](#6-screen-04--faculty-application-status--detail-view)
7. [Screen 05 — Faculty: PRF Review & Confirm](#7-screen-05--faculty-prf-review--confirm)
8. [Screen 06 — Faculty: PRF Status Tracker](#8-screen-06--faculty-prf-status-tracker)
9. [Screen 07 — Faculty: Post-Conference Compliance Checklist](#9-screen-07--faculty-post-conference-compliance-checklist)
10. [Screen 08 — Research Committee: Home & Review Queue](#10-screen-08--research-committee-home--review-queue)
11. [Screen 09 — Approver: Home Dashboard (Dean / Director / VP / President)](#11-screen-09--approver-home-dashboard-dean--director--vp--president)
12. [Screen 10 — Approver: Pending Approvals Queue](#12-screen-10--approver-pending-approvals-queue)
13. [Screen 11 — Approver: Single Application Review](#13-screen-11--approver-single-application-review)
14. [Screen 12 — Approver: All Applications View](#14-screen-12--approver-all-applications-view)
15. [Screen 13 — Approver: PRF Approvals Queue](#15-screen-13--approver-prf-approvals-queue)
16. [Screen 14 — Executive Dashboard (VP & President)](#16-screen-14--executive-dashboard-vp--president)
17. [Screen 15 — Finance: Home & PRF Approvals](#17-screen-15--finance-home--prf-approvals)
18. [Screen 16 — Finance: Budget Overview](#18-screen-16--finance-budget-overview)
19. [Screen 17 — Procurement: Home & Approved PRFs](#19-screen-17--procurement-home--approved-prfs)
20. [Screen 18 — HR: Home & Conference Leave Notifications](#20-screen-18--hr-home--conference-leave-notifications)
21. [Screen 19 — System Admin: Home & User Management](#21-screen-19--system-admin-home--user-management)
22. [Screen 20 — System Admin: Workflow Configuration](#22-screen-20--system-admin-workflow-configuration)
23. [Screen 21 — System Admin: Audit Log](#23-screen-21--system-admin-audit-log)
24. [Screen 22 — System Admin: Academic Year Management](#24-screen-22--system-admin-academic-year-management)
25. [Screen 23 — Notifications Centre (All Roles)](#25-screen-23--notifications-centre-all-roles)
26. [Screen 24 — Profile & Settings (All Roles)](#26-screen-24--profile--settings-all-roles)
27. [Component Library Reference](#27-component-library-reference)
28. [Role-to-Screen Access Matrix](#28-role-to-screen-access-matrix)

---

## 1. Design System & Global Standards

### 1.1 Colour Palette

| Token | Hex | Usage |
|---|---|---|
| `--ud-navy` | `#1B3A6B` | Sidebar background, primary headings, header text |
| `--ud-gold` | `#C8972A` | Accent borders, active states, CTA highlights, dividers |
| `--ud-blue-mid` | `#2563A8` | Links, secondary buttons, icon fills |
| `--ud-blue-light` | `#EBF3FB` | Table row hover, card backgrounds, info banners |
| `--ud-white` | `#FFFFFF` | Page background, card backgrounds |
| `--ud-grey-bg` | `#F5F7FA` | Page canvas background, alternate table rows |
| `--ud-grey-border` | `#D1D9E6` | All borders, dividers, input outlines |
| `--ud-text-dark` | `#1A1A2E` | Primary body text |
| `--ud-text-mid` | `#4A4A6A` | Secondary text, labels, captions |
| `--ud-text-light` | `#8A8AAA` | Placeholder text, disabled states, timestamps |

**Status Colours (always used with a matching text label — never colour alone):**

| Status | Background | Text / Border | Usage |
|---|---|---|---|
| Draft | `#F0F0F0` | `#6B6B6B` | Application saved, not submitted |
| Pending (any stage) | `#FFF8E1` | `#B8860B` | Awaiting approver action |
| Approved | `#E8F5E9` | `#1A7A4A` | Final approval complete |
| Rejected | `#FDEDED` | `#C0392B` | Rejected at any stage |
| Returned | `#FFF3E0` | `#E65100` | Sent back to faculty for revision |
| PRF In Progress | `#E3F2FD` | `#1565C0` | PRF workflow active |
| PRF Approved | `#E0F4F1` | `#00796B` | PRF fully approved |
| Overdue | `#FDEDED` | `#C0392B` | SLA exceeded (+ red left border on table row) |

---

### 1.2 Typography

| Style | Font | Size | Weight | Usage |
|---|---|---|---|---|
| Page Title | Calibri / Inter | 24px | 700 | Main screen heading |
| Section Heading | Calibri / Inter | 18px | 600 | Section titles within a page |
| Sub-heading | Calibri / Inter | 15px | 600 | Card titles, table section headers |
| Body | Calibri / Inter | 14px | 400 | All body text, form labels |
| Caption | Calibri / Inter | 12px | 400 | Timestamps, helper text, annotations |
| Button | Calibri / Inter | 14px | 600 | All button labels |
| Monospace | Courier New | 13px | 400 | Reference numbers (e.g. CRS-2025-CEIT-0042) |

---

### 1.3 Spacing & Layout Grid

- **Canvas background:** `--ud-grey-bg` (`#F5F7FA`) — the page sits on a light grey canvas
- **Content area:** White cards on the grey canvas, `16px` padding inside cards
- **Card border radius:** `8px`
- **Card shadow:** `0 1px 4px rgba(0,0,0,0.08)` — subtle, not heavy
- **Grid:** 12-column grid, `24px` gutters
- **Standard content max-width:** `1280px`, centred in the content area
- **Section spacing:** `24px` between major sections on a page
- **Form field height:** `40px` (inputs, selects, date pickers)
- **Button height:** `36px` standard, `40px` primary CTA

---

### 1.4 Button System

| Type | Style | Usage |
|---|---|---|
| **Primary** | Navy fill (`#1B3A6B`), white text, gold `2px` bottom border on hover | Main CTA — Submit, Approve, Save |
| **Secondary** | White fill, navy border, navy text | Supporting actions — Save Draft, Cancel, Back |
| **Danger** | Red fill (`#C0392B`), white text | Destructive — Reject, Delete |
| **Warning** | Orange fill (`#E65100`), white text | Return for Revision |
| **Ghost** | Transparent, navy text, navy border on hover | Tertiary — Export, View, Download |
| **Icon button** | Icon only, no label, navy icon, light grey hover circle | Compact actions in table rows |

---

### 1.5 Form Elements

- **Input fields:** White background, `1px` solid `--ud-grey-border`, `8px` border radius, `14px` font, gold left border `2px` on focus
- **Required field indicator:** Red asterisk `*` after the label
- **Inline validation error:** Red text below the field (`12px`), red border on the field
- **Inline validation success:** Green checkmark icon inside the field (right side)
- **Helper text:** Grey caption below the field (`12px`), appears always (not just on error)
- **Auto-populated fields:** Light blue tint background (`--ud-blue-light`), padlock icon on the right, tooltip: "Auto-filled from your profile"
- **Disabled fields:** `#F5F7FA` background, `--ud-text-light` text

---

### 1.6 Table Standards (applies to all tables across the platform)

- **Column headers:** `--ud-navy` background, white text, `14px` bold, `12px` padding
- **Rows:** Alternating white / `--ud-grey-bg`, `48px` row height
- **Hover state:** `--ud-blue-light` background on hover
- **Row click:** Entire row is clickable and navigates to the detail view
- **Column sorting:** Up/down arrow icon in header; active sort shown with gold filled arrow
- **Column filtering:** Filter icon (funnel) in header; clicking opens a small dropdown or text input below the header
- **Global search bar:** Positioned above the table, full width of the table, with a search icon on the left
- **Pagination:** Bottom of the table — "Showing 1–20 of 47 results" on the left, page navigation buttons on the right (Previous · 1 · 2 · 3 · Next), page size selector (20 / 50 / 100 per page)
- **Overdue rows:** Red left border `4px` on the row + amber background
- **Empty state:** Centred icon + one-line message + primary action button (see Section 1.7)

---

### 1.7 Empty State Standard

When a table, list, or queue has no data:

```
[Icon — relevant to context, e.g. clipboard for applications]
No applications found.
[Primary action button if applicable — e.g. "Start New Application"]
```

- Icon: `48px`, `--ud-text-light` colour
- Message: `16px`, `--ud-text-mid`, centred
- Button: Primary style, centred below message

---

### 1.8 Status Badge Component

All status badges follow this pattern:

```
[● Coloured dot] [Status Label Text]
```

- Container: `4px` border radius, `6px 10px` padding
- Background and text colour per status table in Section 1.1
- Font: `12px`, `600` weight
- Always includes a text label — never colour alone

---

## 2. Global Shell & Navigation

### 2.1 Layout Structure

The global shell is the persistent wrapper around all authenticated screens. It has three regions:

```
┌──────────────────────────────────────────────────────────────┐
│  TOP HEADER BAR                                              │
├──────────┬───────────────────────────────────────────────────┤
│          │                                                   │
│  LEFT    │   MAIN CONTENT AREA                               │
│ SIDEBAR  │                                                   │
│          │                                                   │
│          │                                                   │
└──────────┴───────────────────────────────────────────────────┘
```

---

### 2.2 Top Header Bar

**Height:** `56px`
**Background:** `--ud-white`
**Bottom border:** `2px` solid `--ud-gold`

**Left section (from left):**
- Sidebar collapse/expand toggle button — hamburger icon (`20px`), `--ud-navy`, `16px` left margin. Clicking toggles the sidebar between expanded (`240px`) and icon-only (`64px`) modes.
- UD Logo — horizontal lockup (logo + "University of Dubai" wordmark), `140px` wide, links to Home

**Centre section:**
- System name label: `"Conference Registration System"`, `14px`, `--ud-text-mid`, non-clickable

**Right section (from right, `16px` right margin):**
- **User avatar + name:** Circular avatar (`32px`), user's full name (`14px`, `--ud-text-dark`), role label below name (`11px`, `--ud-text-light`). Clicking opens a small dropdown: My Profile · Sign Out
- **Divider:** `1px` vertical `--ud-grey-border`
- **Notification bell icon:** `22px`, `--ud-navy`. If unread notifications exist, a red badge with the count is shown (max "9+"). Clicking opens the notification dropdown (last 5, with "See all" link to full notifications page)
- **Divider**
- **Academic Year selector:** Dropdown showing current academic year (e.g. "2024–2025"). Admin can change this; other roles see it read-only as context.

---

### 2.3 Left Sidebar

**Expanded width:** `240px`
**Collapsed width:** `64px` (icon-only mode)
**Background:** `--ud-navy`
**Transition:** `200ms ease` width animation

**Expanded state — each menu item:**
```
[Icon 20px]  [Label text 14px]         [Optional badge]
```
- Item height: `44px`
- Padding: `12px 16px`
- Text: white, `400` weight
- Icon: white, `20px`
- Hover: `rgba(255,255,255,0.08)` background
- Active (current page): gold left border `3px` + `rgba(200,151,42,0.15)` background + white bold text
- Optional badge: small pill (e.g. "3" pending approvals), gold background, navy text, `10px` font

**Collapsed state — each menu item:**
- Icon only, centred in `64px` width
- Tooltip on hover: shows the label in a small navy tooltip to the right

**Bottom of sidebar (always visible, expanded and collapsed):**
- Separator line
- Help & Support link (question mark icon)
- System version number (`v1.0`, `11px`, white at 40% opacity)

---

### 2.4 Sidebar Menu Items by Role

#### Faculty Member
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Faculty Home Dashboard |
| 📋 | My Applications | Count of active apps | My Applications list |
| ➕ | New Application | — | Application Form (Step 1) |
| 📄 | My PRFs | Count of active PRFs | PRF Status Tracker |
| ✅ | Post-Conference Tasks | Count of overdue/pending tasks | Post-Conference Checklist |
| 👤 | Profile | — | Profile & Settings |

#### Research Committee
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | RC Home Dashboard |
| 🔍 | Pending Reviews | Count of pending | Pending Reviews Queue |
| 📁 | All Applications | — | All Applications View (RC scope) |
| 👤 | Profile | — | Profile & Settings |

#### Dean / Director of Research / VP of Academic Affairs
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Approver Home Dashboard |
| ⏳ | Pending Approvals | Count of pending | Pending Approvals Queue |
| 📁 | All Applications | — | All Applications View |
| 📄 | PRF Approvals | Count of pending PRFs | PRF Approvals Queue |
| 📊 | Dashboard & Analytics | — | Analytics Dashboard |
| 👤 | Profile | — | Profile & Settings |

#### UD President
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Approver Home Dashboard |
| ⏳ | Pending Approvals | Count of pending | Pending Approvals Queue |
| 📁 | All Applications | — | All Applications View |
| 📄 | PRF Approvals | Count of pending PRFs | PRF Approvals Queue |
| 📊 | Executive Dashboard | — | Executive Dashboard |
| 👤 | Profile | — | Profile & Settings |

#### Finance Department
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Finance Home Dashboard |
| 📄 | PRF Approvals | Count of pending | PRF Approvals Queue |
| 💰 | Budget Overview | — | Budget Overview Screen |
| 👤 | Profile | — | Profile & Settings |

#### Procurement Department
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Procurement Home Dashboard |
| 📦 | Approved PRFs | Count of new | Approved PRFs List |
| 🛒 | Purchase Orders | — | Purchase Orders Tracker |
| 👤 | Profile | — | Profile & Settings |

#### HR Department
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | HR Home Dashboard |
| 📅 | Conference Leave | Count of new notifications | Leave Notifications Feed |
| 👥 | Faculty Directory | — | Faculty Directory (read-only) |
| 👤 | Profile | — | Profile & Settings |

#### System Administrator
| Icon | Label | Badge | Links to |
|---|---|---|---|
| 🏠 | Home | — | Admin Home Dashboard |
| 👥 | User Management | — | User Management Screen |
| ⚙️ | Workflow Config | — | Workflow Configuration |
| 📋 | Audit Log | — | Audit Log Viewer |
| 📅 | Academic Year | — | Academic Year Management |
| 👤 | Profile | — | Profile & Settings |

---

### 2.5 Notification Dropdown (Bell Icon)

**Triggered by:** Clicking the bell icon in the top header bar
**Dimensions:** `360px` wide, max `480px` tall, scrollable
**Position:** Drops below the bell icon, right-aligned to the header right edge
**Shadow:** `0 4px 20px rgba(0,0,0,0.12)`

**Header of dropdown:**
```
Notifications                    [Mark all as read]
```

**Each notification item:**
```
[● Unread dot / empty]  [Title — bold 14px]                  [Timestamp]
                        [Body — 13px, --ud-text-mid, 2 lines max]
                        [Reference: CRS-2025-CEIT-0042]
```
- Unread items: white background, left border `3px --ud-gold`
- Read items: `--ud-grey-bg` background
- Hover: `--ud-blue-light` background
- Clicking a notification: marks as read + navigates to the relevant application/PRF

**Footer:**
```
[See all notifications →]
```
- Centred link, `14px`, `--ud-blue-mid`, navigates to full Notifications page

---

## 3. Screen 01 — Login Page

### 3.1 Purpose
Entry point for all users. Authenticates via UD Microsoft 365 SSO. No password field in the system itself.

### 3.2 Layout

**Background:** `--ud-white` full page

**Centred login card:**
- Width: `420px`
- Border radius: `12px`
- Shadow: `0 4px 24px rgba(0,0,0,0.10)`
- Padding: `48px`
- Border top: `4px` solid `--ud-gold`

**Inside the card (top to bottom):**

```
[UD Logo — centred, 160px wide]

[Vertical space: 24px]

University of Dubai
[16px, --ud-text-mid, centred]

Conference Registration System
[22px, bold, --ud-navy, centred]

[Vertical space: 8px]

[Horizontal divider — --ud-gold, 40px wide, centred]

[Vertical space: 32px]

Welcome. Please sign in with your
University of Dubai account.
[14px, --ud-text-mid, centred, 2 lines]

[Vertical space: 24px]

[         Sign in with Microsoft 🔷        ]
[Primary button, full width, 44px height]
[Microsoft logo icon on left, "Sign in with Microsoft" text]
[Navy background, white text]

[Vertical space: 16px]

Having trouble signing in? Contact IT Support
[12px, --ud-text-light, centred, "IT Support" is a link]
```

**Below the card (page footer):**
```
© 2025 University of Dubai · Confidential — Internal Use Only
[12px, --ud-text-light, centred]
```

### 3.3 States

| State | Behaviour |
|---|---|
| Default | Card as above |
| Loading (after click) | Button shows spinner + "Signing in…" text, disabled |
| Error (SSO failure) | Red alert banner above the button: "Sign-in failed. Please try again or contact IT Support." |
| Session expired | Same page with an amber banner: "Your session has expired. Please sign in again." |

### 3.4 Annotations
- The page has no sidebar or header — it is a standalone pre-auth screen
- After successful SSO, the system checks the user's role in Active Directory and redirects to the appropriate Home Dashboard
- First-time login triggers a profile confirmation step before reaching the dashboard (see Section 26)

---

## 4. Screen 02 — Faculty: Home Dashboard

### 4.1 Purpose
The Faculty member's primary view after login. Shows their application activity, pending tasks, and quick actions. This IS their home — no separate landing page.

### 4.2 Layout

**Page title:** `Home` (in breadcrumb area below header)

**Top area — Welcome bar:**
```
Good morning, Dr. Sarah Ahmed 👋
[24px, --ud-navy, bold]
Here is your current activity overview.
[14px, --ud-text-mid]
                                    [+ New Application]  [primary button, top-right]
```

---

**Row 1 — KPI Summary Cards (4 cards, equal width, across full content area):**

Each card:
- White background, `8px` border radius, `1px` border `--ud-grey-border`
- Gold top border `3px`
- `16px` padding
- Left: large number (`32px`, bold, `--ud-navy`), label below (`13px`, `--ud-text-mid`)
- Right: relevant icon (`32px`, `--ud-blue-light` circle background)

| Card 1 | Card 2 | Card 3 | Card 4 |
|---|---|---|---|
| Total Applications | Pending Approval | Approved | PRFs Active |
| This academic year | Currently in workflow | This academic year | Awaiting completion |

---

**Row 2 — Two columns:**

**Left column (65% width) — My Recent Applications:**
- Section heading: `My Applications` + `[View all →]` link on the right
- Table with 5 most recent applications:

| Reference | Conference | Submitted | Status | Action |
|---|---|---|---|---|
| CRS-2025-CEIT-0042 | ICAI 2025, London | 14 May 2025 | [Pending Dean] | View |

- Columns: Reference (monospace), Conference Name, Submitted Date, Status (badge), Action (ghost button "View")
- All table standards from Section 1.6 apply
- "View all" link below the table

**Right column (35% width) — Tasks & Reminders:**

Card titled `Action Required`:
- List of items needing attention, each item:
  ```
  [!] Post-conference tasks due — ICAI 2024
      2 items overdue · Due: 20 May 2025
      [Complete Now →]
  ```
  - Orange left border `3px` for overdue items
  - Amber for due-soon items (within 3 days)
- If no tasks: Empty state — "No pending tasks. You're all caught up!"

---

**Row 3 — Application Pipeline Visual:**
- Section heading: `Approval Progress`
- For each active application, show a horizontal stepper:
  ```
  Application: ICAI 2025 — London  [CRS-2025-CEIT-0042]
  ●━━━━●━━━━●━━━━●━━━━●━━━━○━━━━○
  RC   Dean  Dir.  VP  Pres. PRF  Done
  [Completed in green ●] [Current in gold ●] [Upcoming in grey ○]
  ```
- Each dot is labelled below
- Current stage has a pulsing gold dot animation
- Up to 3 active applications shown; "View all" link if more

---

**Row 4 — Recent Notifications strip:**
- Section heading: `Recent Notifications`
- 3 most recent notification items (compact, no full dropdown)
- Each: icon · message · timestamp · "View" link
- `[See all notifications →]` link at the end

---

### 4.3 Sidebar Active State
`Home` item is active (gold left border, bold white text).

---

## 5. Screen 03 — Faculty: New Application Form

### 5.1 Purpose
Multi-step wizard for faculty to submit a conference attendance application. 7 sections (A–G), one section per step.

### 5.2 Layout — Wrapper

**Page title area (below header):**
```
Breadcrumb: Home  >  My Applications  >  New Application
Page Title: New Conference Application
[14px caption below]: Reference will be assigned upon submission.
```

**Two-column layout:**
- **Left: Step Navigator (240px fixed, sticky)** — stays in place as the user progresses
- **Right: Active Step Content (fills remaining width)**

---

### 5.3 Left — Step Navigator Panel

White card, `8px` border radius, full page height sticky.

**Header:**
```
Application Progress
[14px, --ud-text-mid]
[Progress bar: thin gold bar, fills as steps complete]
Step 2 of 7 — Conference Details
[12px, --ud-text-light]
```

**Step list (each step is a row):**
```
[Connector line]
[●] A  Applicant Information     ✓ Complete
[●] B  Conference Details        ← Current (gold, bold)
[○] C  Paper & Presentation
[○] D  Eligibility Checklist
[○] E  Document Uploads
[○] F  Financial Estimate
[○] G  Substitution & Leave
```

Each step row:
- Height: `52px`
- Left: circle indicator (filled green ✓ = complete, filled gold = current, empty grey = upcoming)
- Vertical connector line between steps (grey, turns green as steps complete)
- Step letter + step name (`14px`)
- Completed steps show a green checkmark icon

**Below step list:**
```
[Save as Draft]  [secondary button, full width]
```
Annotation: Saves current progress without submitting. Auto-save also triggers every 60 seconds.

---

### 5.4 Right — Step Content Area

Each step occupies this area. Navigation buttons are always at the bottom.

**Bottom action bar (sticky at bottom of content area):**
```
[← Back]          Step 2 of 7          [Save Draft]  [Next: Document Uploads →]
```
- Back: secondary button (hidden on Step 1)
- Next: primary button
- On Step 7 (final): Next becomes `[Submit Application]` primary button

---

### 5.5 Step A — Applicant Information

**Section heading:** `A. Applicant Information`
**Caption:** `These fields are automatically populated from your university profile. Please verify and confirm.`

All fields are auto-filled and locked (read-only with blue tint + padlock icon):

| Field | Value | Notes |
|---|---|---|
| Full Name | Dr. Sarah Ahmed | From Active Directory |
| Employee ID | UD-FAC-1042 | From Active Directory |
| College | College of Engineering & IT | From Active Directory |
| Academic Rank | Associate Professor | From Active Directory |
| Email Address | s.ahmed@ud.ac.ae | From Active Directory |
| Submission Date | 16 May 2025 | System auto-set |

**Below fields:**
```
[i] Not correct? Contact HR to update your profile details.
[14px, --ud-text-mid, info icon, --ud-blue-mid]
```

---

### 5.6 Step B — Conference Details

**Section heading:** `B. Conference Details`

| Field | Type | Required | Notes |
|---|---|---|---|
| Conference Full Name | Text input | ✱ | AI assistant suggests as user types (dropdown of SCOPUS conferences) |
| Conference Acronym / Short Name | Text input | ✱ | e.g. "ICAI 2025" |
| Conference Website URL | URL input | ✱ | Validated as valid URL format |
| Host City | Text input | ✱ | |
| Host Country | Dropdown | ✱ | Searchable country list |
| Conference Start Date | Date picker | ✱ | Must be future date |
| Conference End Date | Date picker | ✱ | Must be after start date |
| Conference Type | Radio buttons | ✱ | International · National |
| Organising Body / Institution | Text input | ✱ | |

**AI Assistant panel** (right side, collapsible panel `280px`):
```
🤖 Application Assistant
━━━━━━━━━━━━━━━━━━━━━━
💡 Suggestion: Based on your discipline
(Computer Science), here are upcoming
SCOPUS-indexed conferences:

• ICAI 2025 — London, Aug 2025
• IEEE ICCV — Paris, Oct 2025
• NeurIPS 2025 — Vancouver, Dec 2025

[Select]  [Browse all]

⚠️ Cost Estimate: Based on London,
estimated total ≈ AED 12,400
(Flights + Hotel 4 nights + Fees)

📋 Policy Check
[View R 10.3 Summary]
```

---

### 5.7 Step C — Paper & Presentation Details

**Section heading:** `C. Paper & Presentation Details`

| Field | Type | Required | Notes |
|---|---|---|---|
| Paper Title | Text input | ✱ | |
| Co-Authors | Repeatable field group | — | Each entry: Name + Affiliation. [+ Add Co-Author] button |
| Presentation Type | Radio buttons | ✱ | Oral Presentation · Poster · Keynote / Invited Talk |
| SCOPUS Indexing Status | Radio + live badge | ✱ | See below |
| Link to Conference Proceedings | URL input | — | Optional, Scimago/Scopus listing URL |

**SCOPUS Verification widget:**
```
Is this conference SCOPUS-indexed?
○ Yes  ○ No  ○ I'm not sure

[Verify Now — Enter conference name above to check]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
After clicking Verify:
✅ SCOPUS Verified  [green badge]
   Confirmed in Scimago Journal Rankings
   [View listing ↗]
```
- States: ✅ SCOPUS Verified (green) · ❌ Not Found (red) · ⏳ Verifying… (amber) · ⚠️ Predatory Conference Warning (red alert)

**Predatory conference alert:**
```
⚠️  WARNING: This conference appears on the Beall's List
    of potentially predatory publishers.
    Submitting this application may result in rejection.
    [Learn more]  [I understand, proceed anyway]
```

---

### 5.8 Step D — Eligibility Checklist

**Section heading:** `D. Eligibility Checklist`
**Caption:** `All four criteria must be confirmed Yes to proceed. If any is No, your application cannot be submitted at this time.`

Four eligibility items, each displayed as a large card:

```
┌────────────────────────────────────────────────────────┐
│  1.  Have you completed your probationary period?      │
│      [Policy Ref: R 10.3 §2.1]                        │
│                              ○ Yes    ○ No             │
└────────────────────────────────────────────────────────┘
```

If any answer is **No** → card turns red with explanation:
```
┌─ ❌ ─────────────────────────────────────────────────────┐
│  1.  Have you completed your probationary period?        │
│      ❌ You answered: No                                  │
│      You must complete your probationary period before   │
│      applying for conference attendance.                 │
│      Please contact HR for details.                      │
└──────────────────────────────────────────────────────────┘
```

If all 4 are **Yes** → green banner appears:
```
✅  All eligibility criteria met. You may proceed to the next step.
```

The "Next" button is disabled until all 4 are confirmed Yes.

---

### 5.9 Step E — Document Uploads

**Section heading:** `E. Document Uploads`

Each upload field is displayed as a card:

```
┌────────────────────────────────────────────────────────────┐
│  📎  Acceptance Letter / Email                    REQUIRED │
│      Upload the official acceptance from the conference.   │
│                                                            │
│  ┌──────────────────────────────────────────┐             │
│  │  Drag & drop your file here, or Browse   │             │
│  │  Accepted: PDF only · Max size: 10MB     │             │
│  └──────────────────────────────────────────┘             │
│                                                            │
│  After upload:                                             │
│  📄  acceptance_letter_ICAI2025.pdf  [✕ Remove]           │
└────────────────────────────────────────────────────────────┘
```

| Document | Required |
|---|---|
| Acceptance Letter / Email | ✱ Required |
| Conference Paper Draft | ✱ Required |
| Conference Registration Form | ✱ Required |
| Conference Agenda / Programme | Optional |
| Proof of Entry Visa | Optional |

The Next button is disabled until all 3 required documents are uploaded.

**Progress note:** Shows "3 of 3 required documents uploaded ✅"

---

### 5.10 Step F — Financial Estimate

**Section heading:** `F. Financial Estimate`
**Caption:** `Provide your best estimates in AED. These will pre-fill your PRF if approved.`

**Left column — fields:**

| Field | Type | Required | Notes |
|---|---|---|---|
| Conference Registration Fee | Number input (AED) | ✱ | |
| Estimated Flights (return) | Number input (AED) | ✱ | AI suggests based on destination country |
| Accommodation — Cost per Night | Number input (AED) | ✱ | |
| Number of Nights | Number input | ✱ | |
| Accommodation Total | Calculated display | — | Auto: per night × nights |
| Per Diems | Number input (AED) | ✱ | System shows UD per-diem rate as reference |
| Is advance payment required? | Radio | ✱ | Yes · No |
| Is faculty substitution required? | Radio | ✱ | Yes · No |

**Right column — Live Cost Summary card (sticky):**
```
┌─────────────────────────────────────┐
│  💰  Estimated Total Cost           │
│  ─────────────────────────────────  │
│  Registration Fee        AED 2,200  │
│  Flights                 AED 4,800  │
│  Accommodation           AED 3,600  │
│  Per Diems               AED 1,400  │
│  ─────────────────────────────────  │
│  TOTAL             AED 12,000       │
│  [large, --ud-navy, bold]           │
│                                     │
│  [i] UD per-diem rate: AED 350/day  │
└─────────────────────────────────────┘
```

---

### 5.11 Step G — Substitution & Leave

**Section heading:** `G. Substitution & Leave`

| Field | Type | Required | Condition |
|---|---|---|---|
| Conference Leave Start Date | Date picker | ✱ | Auto-suggests conference start date |
| Conference Leave End Date | Date picker | ✱ | Auto-suggests conference end date |
| Substitution Plan | Textarea (400 chars) | ✱ | Describe how classes will be covered |
| Substituting Faculty Member | Text input (name) | Conditional | Only if "Yes" in Step F |
| Additional Notes | Textarea | — | Optional |

**Declaration checkbox (bottom of step):**
```
☐  I confirm that all information provided in this application
   is accurate and complete. I understand that submitting a
   false or incomplete application may result in rejection
   and disciplinary action.
```
The Submit button on this step is disabled until this checkbox is checked.

---

### 5.12 Submission Confirmation Screen

After clicking "Submit Application":

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│              ✅  Application Submitted Successfully             │
│                                                                 │
│   Your application has been submitted and assigned:            │
│                                                                 │
│         CRS-2025-CEIT-0042                                      │
│         [monospace, 20px, --ud-navy, centred]                   │
│                                                                 │
│   The Research Committee has been notified and will            │
│   review your application within 2 working days.               │
│                                                                 │
│   You will receive email notifications at each stage.          │
│                                                                 │
│   [View Application Status]    [Submit Another Application]    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 6. Screen 04 — Faculty: Application Status & Detail View

### 6.1 Purpose
Faculty member views the full details of a submitted application and tracks its progress through the approval chain.

### 6.2 Layout

**Breadcrumb:** `Home  >  My Applications  >  CRS-2025-CEIT-0042`

**Page title area:**
```
ICAI 2025 — International Conference on Artificial Intelligence
London, United Kingdom · 12–14 August 2025
[Status badge: Pending Dean]           [CRS-2025-CEIT-0042 — monospace]
```

**Page-level action bar (top right):**
```
[Download Application PDF]  [ghost button]
```
If status is "Returned": `[Edit & Resubmit]` primary button also appears here.

---

**Full page scroll layout — sections top to bottom:**

**Section 1 — Approval Pipeline (prominent, at the top):**

Horizontal stepper spanning full width:
```
  ✅          ✅         ⏳           ○           ○           ○          ○
  RC       Dean       Director     VP        President    PRF       Done
Approved  Approved   In Review   Waiting    Waiting    Waiting   Waiting
13 May    14 May     [Current]
```

Below each completed stage:
- Approver name: `Dr. Khalid Al Mansoori`
- Date & time: `14 May 2025, 10:32`
- Comment (if any): shown in a small speech bubble on hover

---

**Section 2 — Application Details (tabbed):**

Three tabs:
- **Application Details** (default active) — read-only render of all 7 form sections (A–G), displayed cleanly, grouped by section
- **Uploaded Documents** — list of uploaded files with name, size, upload date, and a download icon button each
- **Approval Comments Thread** — chronological thread of all approver comments, returns, and Q&A exchanges

**Application Details tab layout:**
Each section (A–G) is a collapsible card:
```
▼  A. Applicant Information                             [Expand / Collapse]
   ──────────────────────────────────────────────────
   Full Name          Dr. Sarah Ahmed
   Employee ID        UD-FAC-1042
   College            College of Engineering & IT
   ...
```

**Approval Comments Thread tab layout:**
```
[RC — Research Committee]                            13 May 2025, 09:15
  "Application reviewed. SCOPUS indexing confirmed. Approved to proceed."
  — Dr. Fatima Hassan, Research Committee Chair

[Dean — College of Engineering & IT]                 14 May 2025, 10:32
  "Approved. Ensure substitution plan is confirmed with the HOD."
  — Prof. Mohammed Al Rashid, Dean CEIT

[Director of Research]                               Current Stage
  ⏳ Awaiting review...
```

---

**Section 3 — PRF Status (shown only after conference approval):**

Card:
```
┌──────────────────────────────────────────────────────┐
│  📄  Purchase Requisition Form                       │
│  PRF-2025-CEIT-0042                                  │
│  Status: [PRF In Progress badge]                     │
│  Currently at: Finance Department (Stage 4 of 6)     │
│  [View PRF Details →]                                │
└──────────────────────────────────────────────────────┘
```

**Section 4 — Post-Conference Tasks (shown only after conference dates have passed):**

Card with task summary. Links to the full Post-Conference Checklist screen.

---

## 7. Screen 05 — Faculty: PRF Review & Confirm

### 7.1 Purpose
After conference approval, faculty sees the auto-generated PRF pre-filled from their application. They verify, optionally adjust, and submit to start the PRF approval chain.

### 7.2 Layout

**Breadcrumb:** `Home  >  My PRFs  >  PRF-2025-CEIT-0042`

**Page title:**
```
Purchase Requisition Form — Conference Registration
PRF-2025-CEIT-0042
[Status: Draft — Awaiting Your Confirmation]
```

**Top banner (gold background, navy text):**
```
⚡  This form has been automatically pre-filled from your approved conference
    application CRS-2025-CEIT-0042. Fields highlighted in blue were auto-populated.
    Please review carefully before submitting.
```

---

**Form layout — two column:**

**Left column (main form, 65%):**

**PRF Header Section:**
| Field | Value | Auto-filled? |
|---|---|---|
| Date | 16 May 2025 | ✅ Auto |
| PRF Category | Conference Registration | ✅ Auto — locked |
| College / Department | College of Engineering & IT | ✅ Auto |
| Requester Name | Dr. Sarah Ahmed | ✅ Auto — locked |
| Organisation Code | Research | ✅ Auto — locked |
| Purpose | Conference Registration — ICAI 2025 | ✅ Auto |

**Items Table:**

```
┌────┬──────────────────────────────┬──────────┬──────────┬──────────────┐
│ #  │ Item Description             │ Qty      │ Unit     │ Total (AED)  │
├────┼──────────────────────────────┼──────────┼──────────┼──────────────┤
│ 1  │ Conference Registration Fee  │ 1        │ AED 2,200│ 2,200        │
│ 2  │ Return Flights               │ 1        │ AED 4,800│ 4,800        │
│ 3  │ Accommodation (4 nights)     │ 4        │ AED 900  │ 3,600        │
│ 4  │ Per Diems (4 days)           │ 4        │ AED 350  │ 1,400        │
├────┴──────────────────────────────┴──────────┴──────────┼──────────────┤
│                                                  TOTAL  │ AED 12,000   │
└─────────────────────────────────────────────────────────┴──────────────┘
```

All rows are auto-filled (blue tint). Any row can be edited — clicking a cell makes it editable and adds a "Reason for change" field below that row (required if edited).

**Recommended Supplier Section:**
```
Supplier:  ICAI 2025 Conference Organising Committee
Website:   www.icai2025.org
Quotation attached:  ○ Yes  ○ No
[If items exceed AED 5,000, quotation is required]
```

**Right column (sticky summary, 35%):**

```
┌──────────────────────────────────────┐
│  📋  Auto-fill Source                │
│  ─────────────────────────────────── │
│  Application: CRS-2025-CEIT-0042     │
│  Conference:  ICAI 2025              │
│  Approved by: UD President           │
│  Date:        15 May 2025            │
│                                      │
│  💰  Total: AED 12,000               │
│                                      │
│  ⚠️  Items above AED 5,000 require   │
│     a vendor quotation attached.     │
│                                      │
│  [Submit PRF for Approval]           │
│  [primary button, full width]        │
│                                      │
│  [Save as Draft]                     │
│  [secondary button, full width]      │
└──────────────────────────────────────┘
```

---

## 8. Screen 06 — Faculty: PRF Status Tracker

### 8.1 Purpose
Faculty tracks the progress of their submitted PRF through the 6-stage approval chain.

### 8.2 Layout

**Breadcrumb:** `Home  >  My PRFs`

**Page title:** `My Purchase Requisition Forms`

**Table of all faculty PRFs:**

| PRF Reference | Linked Application | Category | Total (AED) | Submitted | Current Stage | Status |
|---|---|---|---|---|---|---|
| PRF-2025-CEIT-0042 | CRS-2025-CEIT-0042 | Conference | 12,000 | 16 May 2025 | Finance Dept. (4/6) | [PRF In Progress] |

Clicking a row opens the PRF Detail view:

**PRF Detail — full page scroll:**

**PRF Approval Pipeline (horizontal stepper, 6 stages):**
```
  ✅          ✅         ✅          ⏳           ○            ○
  Dean     Director     VP       Finance     President  Procurement
Approved  Approved   Approved   In Review   Waiting     Waiting
14 May    14 May     15 May     [Current]
```

Below the stepper: same comment thread format as Application Status (Section 6).

**PRF form details:** Read-only render of the PRF form items and totals.

---

## 9. Screen 07 — Faculty: Post-Conference Compliance Checklist

### 9.1 Purpose
After the conference end date passes, faculty must complete 5 compliance obligations. This screen manages those tasks.

### 9.2 Layout

**Breadcrumb:** `Home  >  Post-Conference Tasks  >  ICAI 2025`

**Page title:**
```
Post-Conference Compliance
ICAI 2025 — London · Conference ended: 14 August 2025
[Status badge: 2 of 5 tasks complete]
```

**Top alert (if overdue items exist):**
```
⚠️  You have 2 overdue tasks. Please complete them as soon as possible.
    Your Dean has been notified.
[Orange banner, full width]
```

**Task Cards — stacked vertically, one per obligation:**

Each card:
```
┌── [Status colour left border: orange=overdue, amber=due soon, green=complete] ─┐
│                                                                                 │
│  [Status badge]                    Due: 19 Aug 2025    [● Overdue / ✓ Done]   │
│                                                                                 │
│  Task 1: Submit conference schedule showing your name and paper details         │
│          to your College Dean.                                                  │
│                                                                                 │
│  [📎 Upload Evidence]              [i] Policy: R 10.3 §6.1                     │
│                                                                                 │
│  Completed tasks show:                                                          │
│  ✅  Uploaded: schedule_ICAI2025.pdf  ·  20 Aug 2025, 14:22                    │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

**5 tasks displayed in order:**

| # | Task | Deadline | Evidence |
|---|---|---|---|
| 1 | Submit conference schedule to College Dean | D+5 | File upload |
| 2 | Submit published paper to Library | D+10 | File upload |
| 3 | Provide proceedings copy to College RC and UD-RC | D+10 | Confirm + optional upload |
| 4 | Submit expense receipts to Finance (if advance issued) | D+5 | File upload |
| 5 | Complete conference feedback/report form | D+10 | Text form + optional upload |

**Task 5 expands to show a feedback form inline:**
```
Conference Feedback Report
━━━━━━━━━━━━━━━━━━━━━━━━━
Overall conference quality:  ★★★★☆  (star rating)
Key learnings / highlights:  [Textarea, 600 chars]
Recommendations for UD:      [Textarea, 400 chars]
[Upload supporting material: optional]
[Submit Feedback]
```

**Bottom — completion summary:**
```
[Progress bar showing 2/5 complete — gold fill]
All 5 tasks must be completed within 15 working days of your return.
```

---

## 10. Screen 08 — Research Committee: Home & Review Queue

### 10.1 Purpose
Research Committee members review applications at the first stage of the approval chain before the Dean. They can approve, add pending issues, or request information from the faculty member.

### 10.2 Layout — Home Dashboard

**Page title:** `Research Committee — Review Dashboard`

**KPI cards row (3 cards):**
| Card 1 | Card 2 | Card 3 |
|---|---|---|
| Pending Reviews | Reviewed This Month | Avg. Review Time |
| [Count, --ud-navy] | [Count] | [X working days] |

**Main content — Pending Reviews table:**

Section heading: `Applications Awaiting RC Review`

Table columns:
| Reference | Faculty Name | College | Conference | Submitted | SCOPUS | Days Waiting | Action |
|---|---|---|---|---|---|---|---|
| CRS-2025-CEIT-0042 | Dr. S. Ahmed | CEIT | ICAI 2025 | 14 May | ✅ | 2 | Review |

- SCOPUS column: shows ✅ / ❌ / ⏳ badge inline
- Days Waiting: turns amber at 1 day, red at 2+ days (approaching SLA)
- Action: "Review" ghost button opens the application review screen

**Below pending table:** `Completed Reviews` table (same columns, read-only, paginated)

---

## 11. Screen 09 — Approver: Home Dashboard (Dean / Director / VP / President)

### 11.1 Purpose
Primary landing screen for all approver roles. Shows pending queue, analytics summary, and quick actions. Layout adapts slightly per role (e.g. Dean sees only their college; President sees all).

### 11.2 Layout

**Welcome bar:**
```
Good morning, Prof. Mohammed Al Rashid
Dean — College of Engineering & IT
                                    [Go to Pending Approvals →] [primary button]
```

**KPI Cards row (4 cards):**
| Card 1 | Card 2 | Card 3 | Card 4 |
|---|---|---|---|
| Pending My Approval | Approved This Year | Rejected This Year | Avg. Decision Time |
| [Count — gold if > 0] | [Count] | [Count] | [X days] |

**Overdue alert (if applicable):**
```
🔴  3 applications are overdue for your review.
    Escalation notices have been sent to your office.
    [Review Now →]
[Red banner, full width]
```

**Main table — Pending Approvals (top 10, with "View all" link):**

Table columns — same as full Pending Approvals Queue (Section 12), showing top 10 by SLA urgency.

**Bottom row — two columns:**

**Left: Recent Decisions (last 5 actions I took):**
```
Section heading: My Recent Decisions
[Table: Reference · Conference · Decision · Date · Comments snippet]
```

**Right: Quick Stats chart:**
```
Section heading: This Academic Year
[Small donut chart: Approved vs Rejected vs Pending — UD colours]
[Below chart: total applications this year from my college/all]
```

---

## 12. Screen 10 — Approver: Pending Approvals Queue

### 12.1 Purpose
Full list of applications currently awaiting the logged-in approver's action. Primary workhorse screen for approvers.

### 12.2 Layout

**Page title:** `Pending Approvals`
**Caption:** `Applications currently awaiting your review and decision.`

**Top action bar:**
```
[Global search bar — "Search by name, conference, reference..."]
[Filter: College ▾] [Filter: Status ▾] [Filter: Date Range ▾]  [Clear filters]
                                        Showing 12 applications  [Table / Card ▾]
```

**View toggle (top right):**
- **Table view** (default) — standard table layout
- **Card view** — each application shown as a horizontal card, groupable by status

**Table view columns:**

| # | Reference | Faculty Name | College | Conference Name | Country | Submitted | Days Waiting | SLA | Status | Action |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | CRS-2025-CEIT-0042 | Dr. S. Ahmed | CEIT | ICAI 2025 | UK | 14 May | 2d | 🟡 | [Pending Dean] | Review |

**SLA column:**
- 🟢 Green dot: within SLA (< 50% elapsed)
- 🟡 Amber dot: approaching SLA (50–99% elapsed), shows tooltip with hours remaining
- 🔴 Red dot: overdue, row has red left border

**Card view — each card:**
```
┌─────────────────────────────────────────────────────────────────┐
│  CRS-2025-CEIT-0042                          [Pending Dean] 🟡  │
│  Dr. Sarah Ahmed · College of Engineering & IT                  │
│  ICAI 2025 — London, United Kingdom · 12–14 Aug 2025           │
│  Submitted: 14 May 2025 · Waiting: 2 days · Est. AED 12,000    │
│                          [Review Application]  [Quick Approve]  │
└─────────────────────────────────────────────────────────────────┘
```

**Quick Approve** — opens a small modal without leaving the queue:
```
┌─────────────────────────────────────┐
│  Quick Decision                     │
│  CRS-2025-CEIT-0042                 │
│  Dr. Sarah Ahmed — ICAI 2025        │
│                                     │
│  Comment (optional):                │
│  [Textarea]                         │
│                                     │
│  [✅ Approve]  [⚠️ Return]  [❌ Reject] │
└─────────────────────────────────────┘
```

---

## 13. Screen 11 — Approver: Single Application Review

### 13.1 Purpose
Full review screen for a single application. Approver reads all details and takes an action. A fixed action bar at the bottom is always visible.

### 13.2 Layout

**Breadcrumb:** `Home  >  Pending Approvals  >  CRS-2025-CEIT-0042`

**Page title area:**
```
ICAI 2025 — International Conference on Artificial Intelligence
Dr. Sarah Ahmed · College of Engineering & IT
[Status: Pending Your Approval]              [CRS-2025-CEIT-0042 — monospace]
```

---

**Full page scroll — sections:**

**Section 1 — Approval Pipeline** (same horizontal stepper as Faculty view, Section 6)
Current stage is highlighted. Previous approvers' names and dates are shown.

**Section 2 — Application Summary strip:**
Quick-read horizontal strip with key facts:
```
📍 London, UK  ·  📅 12–14 Aug 2025  ·  📝 Oral Presentation
✅ SCOPUS Verified  ·  💰 Est. AED 12,000  ·  👥 2 Co-Authors
```

**Section 3 — Tabbed Detail (3 tabs):**
Same three tabs as faculty view (Application Details / Documents / Approval History). See Section 6.2.

Documents tab: Files are downloadable via icon buttons. Approvers cannot delete or replace documents.

**Section 4 — Previous Approver Comments (always visible, not in tab):**
Below the tabs, always visible:
```
Comments from Previous Approvers
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[RC · Dr. Fatima Hassan · 13 May 2025, 09:15]
"Application reviewed. SCOPUS indexing confirmed. Approved."
```

---

**Fixed bottom action bar (always visible, sticky at bottom of viewport):**

```
┌────────────────────────────────────────────────────────────────────────────────┐
│                                                                                │
│  Add a comment (required if Returning or Rejecting):      [Character: 0/500]  │
│  ┌────────────────────────────────────────────────────────────────────────┐   │
│  │  Type your comments, instructions, or reason here...                  │   │
│  └────────────────────────────────────────────────────────────────────────┘   │
│                                                                                │
│  [← Back to Queue]   [Request Information]   [⚠️ Return]  [❌ Reject]  [✅ Approve] │
│                                                                                │
└────────────────────────────────────────────────────────────────────────────────┘
```

**Button behaviours:**
- **Approve:** Opens confirmation modal → "Confirm Approval — This will advance the application to the Director of Research." [Confirm] [Cancel]. On confirm: digital signature captured (timestamp + name), application moves to next stage, notifications sent.
- **Return:** Comment is required. Modal: "Return to Faculty — The faculty member will be notified to revise and resubmit." [Confirm Return] [Cancel]
- **Reject:** Comment is required. Modal (red): "Reject Application — This action is final. The application will be archived and the faculty member notified." [Confirm Rejection] [Cancel]
- **Request Information:** Opens an information request thread where the approver types a question. The faculty member is notified and responds in-system. The thread appears in the Approval History tab.

---

## 14. Screen 12 — Approver: All Applications View

### 14.1 Purpose
Full searchable, filterable view of all applications within the approver's scope (college-filtered for Dean, university-wide for Director/VP/President).

### 14.2 Layout

**Page title:** `All Applications`
**Caption (Dean view):** `Showing all applications from College of Engineering & IT`

**Top — KPI summary strip (above the table):**
```
[Total: 84]  [Approved: 52]  [Pending: 18]  [Rejected: 9]  [Returned: 5]
```
Each number is a clickable filter — clicking "Pending: 18" filters the table to show only pending.
Academic year selector on the right: `2024–2025 ▾`

**View toggle:** Table ▾ / Card view toggle (top right), same as Pending Approvals Queue.

**Full table — all applications:**

Columns: Reference · Faculty Name · College · Conference Name · Country · Start Date · Submitted Date · Final Status · Action

All table standards apply (search, sort, filter, pagination, row click).

**Status filter dropdown options:** All · Draft · Pending RC · Pending Dean · Pending Director · Pending VP · Pending President · Approved · Rejected · Returned · PRF In Progress · PRF Approved

---

## 15. Screen 13 — Approver: PRF Approvals Queue

### 15.1 Purpose
Approvers see PRFs awaiting their specific approval stage in the PRF chain.

### 15.2 Layout

**Page title:** `PRF Approvals`
**Caption:** `Purchase Requisition Forms awaiting your review.`

**Structure:** Same layout pattern as Pending Approvals Queue (Section 12), adapted for PRFs.

**Table columns:**
| PRF Reference | Linked Application | Faculty Name | College | Purpose | Total (AED) | Submitted | SLA | Action |
|---|---|---|---|---|---|---|---|---|
| PRF-2025-CEIT-0042 | CRS-2025-CEIT-0042 | Dr. S. Ahmed | CEIT | Conference Reg. | 12,000 | 16 May | 🟢 | Review |

**PRF Review Screen** (opened from "Review" action): Same fixed bottom action bar pattern as application review. Approver sees the full PRF form (read-only), the auto-fill source summary, all previous stage decisions, and takes: Approve / Return / Reject.

Finance-specific additions on the PRF review screen:
- Budget availability indicator: `Budget remaining for Research Travel 2024–2025: AED 48,200`
- Ability to adjust approved amounts with a mandatory reason field
- Quotation required warning if items exceed AED 5,000 and no quotation is attached

---

## 16. Screen 14 — Executive Dashboard (VP & President)

### 16.1 Purpose
High-level real-time view of the entire conference application ecosystem. Designed for VP of Academic Affairs and UD President. Data-dense but visually clear.

### 16.2 Layout

**Page title:** `Executive Dashboard`
**Right side:** `Academic Year: 2024–2025 ▾` · `[Export PDF Report]` [ghost button] · `[Last updated: 2 mins ago]` (caption)

---

**Row 1 — KPI Counter Cards (5 cards, equal width):**

Each card:
- White, gold top border `3px`, `16px` padding
- Large number (`36px`, bold, `--ud-navy`)
- Label below (`13px`, `--ud-text-mid`)
- Trend indicator: small up/down arrow with % vs. last year (`12px`, green/red)

| Card 1 | Card 2 | Card 3 | Card 4 | Card 5 |
|---|---|---|---|---|
| Total Applications | Approved | Pending | Rejected | Budget Committed |
| YTD count | YTD count | In workflow | YTD count | AED amount |
| ↑ 12% vs last year | ↑ 8% | — | ↓ 3% | AED 240,000 of AED 400,000 |

---

**Row 2 — Two charts, side by side:**

**Left chart (60%) — Applications by Month (bar chart):**
- X-axis: months (Sep–Aug, academic year)
- Y-axis: count
- Bars: navy for approved, gold for pending, red for rejected, stacked
- Hover tooltip: exact counts per status per month

**Right chart (40%) — Applications by College (donut chart):**
- Three segments: CEIT · Business · Law
- UD colour variants used
- Centre: total count
- Legend below with count and percentage per college

---

**Row 3 — Three columns:**

**Column 1 (33%) — Approval Cycle Time:**
Line chart — average days per stage across the current academic year.
```
Avg. Days per Stage — Academic Year 2024–2025
[Line chart: RC · Dean · Director · VP · President on X-axis, days on Y-axis]
```
Annotation: Any stage > SLA target is highlighted in red.

**Column 2 (33%) — Top Conferences:**
Ranked list:
```
Top 5 Conferences by Faculty Participation
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. IEEE ICAI 2025          ████████ 8 faculty
2. ACM SIGCHI 2025         ██████   6 faculty
3. ICML 2025               █████    5 faculty
4. ABA Law Conference 2025 ████     4 faculty
5. HBAA Forum 2025         ██       2 faculty
```

**Column 3 (33%) — Budget Committed vs. Spent Gauge:**
```
Research Travel Budget 2024–2025
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Semi-circular gauge — gold arc fill, navy arc remaining]
AED 240,000 committed
AED 163,000 actual spent
AED 400,000 total budget
[75% alert threshold — dotted line on gauge]
```

---

**Row 4 — College Comparison Table:**

```
College Comparison — Academic Year 2024–2025
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

| College | Applications | Approved | Rejected | Pending | SCOPUS Papers | Budget Used (AED) |
|---|---|---|---|---|---|---|
| Engineering & IT | 42 | 31 | 5 | 6 | 28 | 112,000 |
| Business | 28 | 19 | 4 | 5 | 15 | 84,000 |
| Law | 14 | 9 | 2 | 3 | 7 | 44,000 |
| **Total** | **84** | **59** | **11** | **14** | **50** | **240,000** |

---

**Row 5 — Research Impact Tracker (Director of Research + VP + President):**

```
Research Output — SCOPUS-Indexed Papers Presented
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Bar chart: year-on-year comparison, current year vs last 3 years]
[Below: Table — Top 10 Faculty by Papers Presented this year]
```

---

## 17. Screen 15 — Finance: Home & PRF Approvals

### 17.1 Purpose
Finance staff review PRFs at Stage 4 of the PRF approval chain, check budget availability, and approve or adjust amounts.

### 17.2 Layout — Home Dashboard

**Page title:** `Finance Dashboard`

**KPI Cards (4):**
| PRFs Pending Review | PRFs Approved This Month | Total Value Approved YTD | Budget Remaining |
|---|---|---|---|
| [Count] | [Count] | AED [amount] | AED [amount] |

Budget remaining card: turns amber at < 25% remaining, red at < 10%.

**Main table — PRFs Pending Finance Approval:**
Same structure as PRF Approvals Queue (Section 15.2).

Finance-specific table columns added:
- **Quotation**: ✅ Attached / ⚠️ Missing
- **Budget Impact**: shows remaining budget after this PRF if approved

---

## 18. Screen 16 — Finance: Budget Overview

### 18.1 Purpose
Finance team views full budget consumption across all colleges for the current academic year.

### 18.2 Layout

**Page title:** `Research Travel Budget Overview`

**Top — Budget Summary bar:**
```
Total Budget 2024–2025: AED 400,000
[████████████████████████░░░░░░░░░░░░░░]  60% committed
Committed: AED 240,000    Spent: AED 163,000    Remaining: AED 160,000
```

**Forecast Widget (gold card):**
```
💰  Budget Forecast
Based on 14 pending applications (est. AED 68,000),
projected year-end commitment: AED 308,000 (77% of budget).

⚠️  Alert threshold (75%): AED 300,000 — approaching.
[Set Alert Thresholds]  [ghost button]
```

**By-college breakdown table:**
Same as College Comparison table in Executive Dashboard but finance-focused, adding: Committed, Actual Spent, Variance, PRFs pending.

**Monthly expenditure trend chart:**
Bar chart by month (committed and spent, side by side).

---

## 19. Screen 17 — Procurement: Home & Approved PRFs

### 19.1 Purpose
Procurement receives fully-approved PRFs (all 5 approval stages complete) and manages the vendor engagement and purchase order process.

### 19.2 Layout

**Page title:** `Procurement Dashboard`

**KPI Cards (3):**
| New PRFs Received | Purchase Orders Active | Completed This Month |
|---|---|---|
| [Count — highlighted gold if > 0] | [Count] | [Count] |

**Main table — Approved PRFs (awaiting PO):**
| PRF Reference | Faculty | College | Purpose | Total (AED) | President Approved | Days Since Approval | PO Status | Action |
|---|---|---|---|---|---|---|---|---|
| PRF-2025-CEIT-0042 | Dr. S. Ahmed | CEIT | ICAI 2025 Reg. | 12,000 | 15 May 2025 | 1 | Not Started | Process |

**Clicking "Process"** opens the PRF detail (read-only) with a Procurement Action panel at the bottom:
```
Procurement Actions
━━━━━━━━━━━━━━━━━━
PO Number:     [Input — enter when raised]
Vendor:        [Input / pre-filled from PRF supplier]
PO Date:       [Date picker]
Status:        [Dropdown: Not Started · PO Raised · Payment Processed · Closed]
Notes:         [Textarea]
[Update Status]  [primary button]
```

Status updates are logged and faculty receives a notification when PO is raised.

---

## 20. Screen 18 — HR: Home & Conference Leave Notifications

### 20.1 Purpose
HR receives read-only notifications of approved conference attendance that affects faculty leave. No approval authority — observation and record-keeping only.

### 20.2 Layout

**Page title:** `Conference Leave Notifications`
**Caption:** `Read-only view. Approved conference attendances affecting faculty leave.`

**Top — current period summary:**
```
Active Conference Leave — May 2025
3 faculty members currently on approved conference leave.
```

**Main table — Conference Leave Feed:**
| Faculty Name | College | Conference | Country | Leave Start | Leave End | Substitution Arranged | Approved By |
|---|---|---|---|---|---|---|---|
| Dr. Sarah Ahmed | CEIT | ICAI 2025 | United Kingdom | 12 Aug 2025 | 14 Aug 2025 | Yes — Dr. Karim | UD President |

- All rows are read-only. No action buttons.
- Export to Excel available (top right).

**Faculty Directory tab:**
Simple searchable read-only list of all faculty members with their college and current leave status.

---

## 21. Screen 19 — System Admin: Home & User Management

### 21.1 Purpose
System Administrator manages all users, roles, and access across the platform.

### 21.2 Layout — Admin Home

**Page title:** `System Administration`

**KPI Cards (4):**
| Total Active Users | New This Month | Pending Role Assignment | System Alerts |
|---|---|---|---|
| [Count] | [Count] | [Count — gold if > 0] | [Count — red if > 0] |

**Quick links grid (2×3):**
Large icon cards linking to each admin section:
- User Management · Workflow Config · Audit Log · Academic Year · Notification Templates · System Health

### 21.3 Layout — User Management

**Page title:** `User Management`

**Top action bar:**
```
[Search users...] [Filter: Role ▾] [Filter: College ▾] [Filter: Status ▾]
                                                        [+ Add New User]  [primary button]
```

**User table:**
| Name | Employee ID | Email | Role | College | Status | Last Login | Actions |
|---|---|---|---|---|---|---|---|
| Dr. Sarah Ahmed | UD-FAC-1042 | s.ahmed@ud.ac.ae | Faculty | CEIT | Active | 16 May 2025 | Edit · Deactivate |

**Edit User panel (opens as a right-side drawer, `400px` wide):**
```
Edit User
━━━━━━━━━━━━━━━━━━━━━━━━━
Full Name:      [Text input — read from AD, editable]
Employee ID:    [Read-only]
Email:          [Read-only — from AD]
Role:           [Dropdown: all roles]
College:        [Dropdown — if applicable]
Status:         [Toggle: Active / Inactive]

Delegation Settings:
Auto-delegate after: [Number] hours to [User search]

[Save Changes]  [Cancel]
```

---

## 22. Screen 20 — System Admin: Workflow Configuration

### 22.1 Purpose
Admin configures SLA thresholds, approval chain structure, and email notification templates.

### 22.2 Layout

**Page title:** `Workflow Configuration`

**Two tabs:**

**Tab 1 — SLA & Approval Settings:**

```
Conference Approval Chain — SLA Thresholds
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Editable table]
```
| Stage | Approver | SLA (working days) | Escalation Recipient | Edit |
|---|---|---|---|---|
| RC | Research Committee | 2 | Director of Research | ✏️ |
| 1 | Dean | 2 | Director of Research | ✏️ |
| 2 | Director of Research | 2 | VP Academic Affairs | ✏️ |
| 3 | VP Academic Affairs | 1 | UD President | ✏️ |
| 4 | UD President | 1 | — | ✏️ |

Same table for PRF Approval Chain (6 stages).

**Draft retention period:** `[Number] days` (default: 90)
**Post-conference compliance window:** `[Number] working days` (default: 15)

**Tab 2 — Notification Templates:**

List of all notification types (e.g. "Application Submitted", "Approver Action Required", "SLA Overdue", "PRF Created", etc.).

Clicking a template opens an editor:
```
Template: Application Submitted — Faculty Notification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Subject: [Text input — supports {{variables}}]
Body:    [Rich text editor]
         Available variables: {{applicant_name}}, {{reference}},
         {{conference_name}}, {{current_stage}}, {{deep_link}}
[Preview] [Save Template]
```

---

## 23. Screen 21 — System Admin: Audit Log

### 23.1 Purpose
Immutable, searchable record of all system events for compliance and security review.

### 23.2 Layout

**Page title:** `Audit Log`
**Caption:** `Immutable record of all system events. Retained for 7 years.`

**Top filter bar:**
```
[Search by user, action, entity...] [Date Range picker] [Filter: Action Type ▾] [Filter: Role ▾]
                                                                            [Export CSV] [Export PDF]
```

**Audit log table:**
| Timestamp | User | Role | Action | Entity Type | Entity Reference | IP Address | Details |
|---|---|---|---|---|---|---|---|
| 16 May 2025 10:32:14 | Dr. Sarah Ahmed | Faculty | SUBMITTED | Application | CRS-2025-CEIT-0042 | 10.0.1.42 | View |

"View" opens a detail modal showing old value vs. new value (JSON diff for changed records).

No edit or delete actions — this table is read-only by design.

---

## 24. Screen 22 — System Admin: Academic Year Management

### 24.1 Purpose
Admin opens and closes academic year cycles and manages historical data archiving.

### 24.2 Layout

**Page title:** `Academic Year Management`

**Current year card:**
```
┌─────────────────────────────────────────────────────────────┐
│  CURRENT ACADEMIC YEAR                                      │
│  2024–2025                              Status: 🟢 Active  │
│  Applications: 84 total                                     │
│  Opened: 1 September 2024                                   │
│                                                             │
│  [Close Academic Year]  [danger button]                     │
└─────────────────────────────────────────────────────────────┘
```

Closing the year triggers a confirmation modal explaining consequences (no new submissions, data archived as read-only).

**[+ Open New Academic Year]** button — opens setup wizard:
1. Set year label (e.g. 2025–2026)
2. Set budget allocation per college
3. Confirm SLA settings carry over
4. Activate

**Previous years table:**
| Year | Applications | Approved | Total Spend | Status | Action |
|---|---|---|---|---|---|
| 2023–2024 | 71 | 54 | AED 198,000 | Closed | View Archive |

---

## 25. Screen 23 — Notifications Centre (All Roles)

### 25.1 Purpose
Full notifications page accessible to all roles. Shows complete history of all notifications, grouped and filterable.

### 25.2 Layout

**Page title:** `Notifications`

**Top action bar:**
```
[Filter: All ▾ / Unread / Read]   [Filter: Type ▾]      [Mark all as read]
```

**Notifications list — grouped by date:**

```
TODAY — 16 May 2025
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[● Unread] 🔔 Application Approved by Dean                      10:32
            CRS-2025-CEIT-0042 — ICAI 2025 has been approved
            by Prof. Mohammed Al Rashid and advanced to the
            Director of Research.
            [View Application →]

[● Unread] ⚠️  Post-Conference Task Overdue                     09:00
            Task 1 for ICAI 2024 is overdue (due: 19 Aug 2024).
            [Complete Now →]

YESTERDAY — 15 May 2025
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Read]    ✅ Application Fully Approved                         14:15
            CRS-2025-CB-0038 has been approved by the
            UD President. Your PRF has been auto-generated.
            [View PRF →]
```

Each notification:
- Left: unread indicator dot (gold) or empty (read)
- Icon indicating type
- Title (bold), body (2 lines), reference link
- Right: timestamp
- Full row is clickable — marks as read and navigates to context

---

## 26. Screen 24 — Profile & Settings (All Roles)

### 26.1 Purpose
User views and updates their personal profile, notification preferences, and delegation settings.

### 26.2 Layout

**Page title:** `My Profile`

**Two tabs:**

**Tab 1 — Profile Information:**
```
[Avatar — circular, 80px]  [Change Photo]

Full Name:         Dr. Sarah Ahmed        [Read-only — from AD]
Employee ID:       UD-FAC-1042            [Read-only]
Email:             s.ahmed@ud.ac.ae       [Read-only]
College:           CEIT                   [Read-only]
Academic Rank:     Associate Professor    [Read-only]

Editable fields:
Specialisation:    [Text input]
ORCID ID:          [Text input, validated format]
Google Scholar:    [URL input]

[Save Changes]
```

**Note at bottom:** "To update read-only fields, please contact HR or the System Administrator."

**Tab 2 — Notification Preferences:**
Table of notification types with toggles (Email / In-App / Both / Off):
| Notification Type | Email | In-App |
|---|---|---|
| Application status changed | ✅ | ✅ |
| Approver comment received | ✅ | ✅ |
| Post-conference task due | ✅ | ✅ |
| PRF status changed | ✅ | ✅ |
| SLA reminder (approvers only) | ✅ | ✅ |

**Tab 3 — Delegation Settings (Approver roles only):**
```
Out-of-Office Delegation
━━━━━━━━━━━━━━━━━━━━━━━━
Auto-delegate pending approvals to:
[User search input — search by name or employee ID]

Delegate after:  [Number] hours without action

Active from:  [Date picker]   to:  [Date picker]
              (leave blank for indefinite)

[Save Delegation Settings]

Current Delegation:
Delegating to: Prof. Ahmad Al Sayed
Active: 20 May – 28 May 2025
[Cancel Delegation]
```

---

## 27. Component Library Reference

Summary of all reusable components defined in this specification.

### 27.1 Navigation Components
- `<TopHeader>` — global header bar (Section 2.2)
- `<LeftSidebar>` — role-aware sidebar, expanded/collapsed states (Section 2.3)
- `<Breadcrumb>` — page location trail, used on all inner pages
- `<NotificationDropdown>` — bell icon dropdown (Section 2.5)

### 27.2 Data Display Components
- `<KPICard>` — counter card with label, trend indicator, icon (Section 4.2)
- `<StatusBadge>` — coloured status pill (Section 1.8)
- `<DataTable>` — full-featured table with search, sort, filter, pagination (Section 1.6)
- `<ApprovalStepper>` — horizontal pipeline tracker (Section 6.2)
- `<CommentThread>` — chronological approver comments (Section 6.2)
- `<NotificationItem>` — individual notification row (Section 25.2)

### 27.3 Form Components
- `<FormSection>` — labelled collapsible section wrapper
- `<AutoFilledField>` — read-only field with blue tint + padlock icon
- `<FileUploadCard>` — drag-drop upload area with post-upload file name display
- `<ScopeVerificationWidget>` — SCOPUS live check with badge (Section 5.7)
- `<EligibilityCard>` — yes/no card with inline error state (Section 5.8)
- `<FinancialSummaryCard>` — sticky live cost total (Section 5.10)
- `<AIAssistantPanel>` — collapsible right-side AI helper (Section 5.6)

### 27.4 Action Components
- `<ActionBar>` — sticky bottom bar with approve/return/reject buttons (Section 13.2)
- `<QuickApproveModal>` — compact in-queue decision modal (Section 12.2)
- `<ConfirmationModal>` — used for all destructive or irreversible actions
- `<EmptyState>` — icon + message + optional CTA (Section 1.7)
- `<AlertBanner>` — full-width contextual alert (red/amber/gold/green)

### 27.5 Dashboard Components
- `<BarChart>` — applications by month (Section 16.2)
- `<DonutChart>` — applications by college (Section 16.2)
- `<LineChart>` — approval cycle time trend (Section 16.2)
- `<GaugeChart>` — budget committed vs total (Section 16.2)
- `<RankedList>` — top conferences by faculty count (Section 16.2)
- `<CollegeComparisonTable>` — multi-college data table (Section 16.2)
- `<BudgetForecastWidget>` — Finance forward-looking projection (Section 18.2)

### 27.6 Task Components
- `<TaskCard>` — post-conference obligation card with status, due date, upload (Section 9.2)
- `<PRFItemRow>` — editable/read-only PRF line item with auto-fill indicator (Section 7.2)
- `<ProcurementActionPanel>` — PO status update form (Section 19.2)

---

## 28. Role-to-Screen Access Matrix

| Screen | Faculty | RC | Dean | Director | VP | President | Finance | Procurement | HR | Admin |
|---|---|---|---|---|---|---|---|---|---|---|
| 01 Login | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 02 Faculty Home | ✅ | — | — | — | — | — | — | — | — | — |
| 03 New Application Form | ✅ | — | — | — | — | — | — | — | — | — |
| 04 Application Status/Detail | ✅ (own) | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | — | ✅ |
| 05 PRF Review & Confirm | ✅ (own) | — | — | — | — | — | — | — | — | — |
| 06 PRF Status Tracker | ✅ (own) | — | — | — | — | — | — | — | — | — |
| 07 Post-Conference Checklist | ✅ (own) | — | — | — | — | — | — | — | — | — |
| 08 RC Home & Queue | — | ✅ | — | — | — | — | — | — | — | — |
| 09 Approver Home | — | — | ✅ | ✅ | ✅ | ✅ | — | — | — | — |
| 10 Pending Approvals Queue | — | — | ✅ | ✅ | ✅ | ✅ | — | — | — | — |
| 11 Single Application Review | — | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | — | — |
| 12 All Applications View | — | ✅ | ✅ (college) | ✅ | ✅ | ✅ | — | — | — | ✅ |
| 13 PRF Approvals Queue | — | — | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | — |
| 14 Executive Dashboard | — | — | ✅ (college) | ✅ | ✅ | ✅ | — | — | — | ✅ |
| 15 Finance Home & PRF Approvals | — | — | — | — | — | — | ✅ | — | — | — |
| 16 Finance Budget Overview | — | — | — | — | — | — | ✅ | — | — | ✅ |
| 17 Procurement Home & PRFs | — | — | — | — | — | — | — | ✅ | — | — |
| 18 HR Home & Leave Notifications | — | — | — | — | — | — | — | — | ✅ | — |
| 19 Admin: User Management | — | — | — | — | — | — | — | — | — | ✅ |
| 20 Admin: Workflow Config | — | — | — | — | — | — | — | — | — | ✅ |
| 21 Admin: Audit Log | — | — | — | — | — | — | — | — | — | ✅ |
| 22 Admin: Academic Year | — | — | — | — | — | — | — | — | — | ✅ |
| 23 Notifications Centre | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 24 Profile & Settings | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

---

<div align="center">

**University of Dubai · Conference Registration System**
**Screen Layout & Design Specification · v1.0**

*Confidential — Internal Use Only*

*Next step: High-fidelity mockups screen by screen, starting with Screen 01 — Login.*

</div>
