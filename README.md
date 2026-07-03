# CaseReviews

## Purpose

CaseReviews is a proof-of-concept solution that integrates Power Apps, Power Automate, GitHub Issues, and GitHub Actions into a single automated workflow for AI case review requests.

Users submit a review request through Power Apps, which automatically creates a GitHub Issue and triggers a GitHub Action for processing.

---

## Solution Flow

```text
Power App
    ↓
Power Automate Flow
    ↓
GitHub Issue Created
    ↓
GitHub Action Triggered
    ↓
Process Request
    ↓
Close Issue
```

---

## Power App

The Power App collects the following information:

- Manager
- Engineer
- Days Reviewed
- Maximum Cases to Return
- Optional Case Numbers
- Email Address

When the user clicks the AI Assistant, the app submits the request to Power Automate.

---

## Power Automate

The flow performs the following actions:

1. Receives parameters from Power Apps
2. Creates a GitHub Issue in the CaseReviews repository
3. Sends a confirmation email
4. Includes a direct link to the created GitHub Issue

### Sample Issue Title

```text
AI Review - David Cordero (dcordero) - Date: 2026-07-03
```

### Sample Issue Body

```text
Manager: Rob Wright

Engineer: David Cordero (dcordero)

Days Reviewed: 30

Maximum Cases: 10

Optional Cases: 453,234

Submitted From: Power Apps
```

---

## GitHub Actions

A GitHub Action is configured to automatically execute whenever a new issue is opened.

### Workflow Trigger

```yaml
on:
  issues:
    types: [opened]
```

### Current Functionality

The workflow:

- Detects newly created issues
- Reads the issue title
- Reads the issue body
- Outputs request details to the workflow log
- Processes the request
- Closes the issue when complete

### Example Workflow Output

```text
Issue Title:
AI Review - David Cordero (dcordero) - Date: 2026-07-03

Issue Body:

Manager: Rob Wright
Engineer: David Cordero (dcordero)
Days Reviewed: 30
Maximum Cases: 10
Optional Cases: 453,234

Submitted From: Power Apps
```

---

## Future Enhancements

Potential enhancements include:

- Salesforce case retrieval
- AI-powered case analysis
- Automatic issue comments with results
- Emailing completed review summaries
- Status tracking through GitHub labels
- Enhanced validation and error handling

---

## Current Status

✅ Power App integration complete

✅ Power Automate integration complete

✅ GitHub Issue creation working

✅ Email notifications working

✅ GitHub Action trigger working

✅ Issue data available to workflows

✅ Automatic issue processing and closure working

CaseReviews now serves as the automation entry point for future Salesforce and AI-driven case review processing.
