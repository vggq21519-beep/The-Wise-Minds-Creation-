# GET MONEY MACHINE

## MASTER REPOSITORY README

GET MONEY MACHINE is a full-stack financial application consisting of a mobile-first frontend, secure backend API, persistent database, internal earnings ledger, station system, opportunity/scanner framework, transfer system, payment-provider integration, authentication, audit logging, notifications, and Android application.

This repository is the source of truth for the application implementation.

---

# 1. CORE REQUIREMENT

GET MONEY MACHINE must be implemented as a complete, connected, functional application.

This is NOT:

- A mockup
- A prototype
- A static dashboard
- A disconnected frontend
- A demonstration application
- A fake financial simulator
- A placeholder application
- A collection of nonfunctional screens

The frontend, backend, database, ledger, stations, authentication, transfer system, provider integration, audit system, and Android application must operate together.

---

# 2. NO FAKE FINANCIAL ACTIVITY

Never fabricate:

- Money
- Earnings
- Opportunities
- Scanner results
- Eligibility
- Verification
- Settlements
- Transactions
- Transfers
- Provider confirmations
- Provider balances
- Historical transactions

An opportunity is not money.

An estimated opportunity value is not earnings.

A pending amount is not available money.

A transfer request is not a completed transfer.

A provider request is not provider confirmation.

Only legitimate verified/settled earnings become available according to the ledger rules.

If an external service or API is unavailable, show the actual unavailable, error, or not-configured state.

Never create fake success merely to make the application appear complete.

---

# 3. EXACT 15 STATIONS

The application contains exactly these 15 stations:

1. Unclaimed Property Station
2. Refund Recovery Station
3. Rebate Station
4. Cashback Station
5. Rewards Station
6. Promotional Bonus Station
7. Fee Recovery Station
8. Overpayment Recovery Station
9. Subscription Credit Station
10. Settlement & Claims Station
11. Business Incentive Station
12. Public Opportunity Station
13. Revenue Opportunity Station
14. Reinvestment Station
15. Earnings & Transfer Station

Do not add additional earning stations.

---

# 4. MASTER STATION CONTROLS

The application must provide:

- START ALL
- STOP ALL
- PAUSE ALL
- EMERGENCY STOP

These controls must operate against actual backend/database state.

They must not merely change the appearance of the frontend.

---

# 5. INDIVIDUAL STATION CONTROLS

Each station must support:

- ENABLE
- DISABLE
- START
- PAUSE
- STOP
- EMERGENCY STOP
- MANUAL SCAN
- MANUAL OPPORTUNITY ENTRY
- VIEW RESULTS
- VIEW HISTORY
- VIEW ERRORS
- VIEW PENDING
- VIEW VERIFIED

Every control must be functional.

No dead buttons.

No placeholder buttons.

No UI-only state changes.

---

# 6. AUTOMATION

The scheduler/worker must respect:

- ENABLE
- DISABLE
- START
- PAUSE
- STOP
- EMERGENCY STOP
- START ALL
- STOP ALL
- PAUSE ALL
- EMERGENCY STOP

A stopped, disabled, paused, or emergency-stopped station must not continue running.

Backend state is authoritative.

---

# 7. OPPORTUNITY LIFECYCLE

The application must follow this lifecycle:

STATION ACTIVITY
→ OPPORTUNITY
→ ELIGIBILITY
→ SUBMISSION
→ PENDING
→ VERIFICATION
→ SETTLEMENT
→ AVAILABLE EARNED MONEY
→ TRANSFER REQUEST
→ DESTINATION
→ PROVIDER CONFIRMATION
→ LEDGER RECONCILIATION

Discovery does not automatically create earnings.

Manual opportunity entry does not automatically create earnings.

Estimated value does not automatically become available balance.

---

# 8. INTERNAL LEDGER

The internal database ledger is the financial source of truth.

Supported transaction statuses:

- PENDING
- PROCESSING
- COMPLETED
- FAILED
- REVERSED
- CANCELLED

Ledger operations must be persistent and auditable.

Do not subtract money simply because a transfer button was pressed.

Provider confirmation is required before a provider-backed transfer is marked COMPLETED.

Duplicate provider events must not create duplicate financial transactions.

Use idempotency where appropriate.

---

# 9. OPENING APPLICATION BALANCE

The application specification contains one opening ledger entry:

**$15,000 USD**

Classification:

**EXISTING / OPENING APPLICATION EARNINGS**

Do not fabricate historical transactions to explain this entry.

Do not create fake deposits.

Do not represent it as externally funded cash unless an actual verified funding source exists.

---

# 10. AUTHENTICATION

Use real owner authentication.

Required:

- Owner email
- Owner password
- Secure password hashing
- JWT/session authentication
- Protected financial endpoints
- Authorization
- Secure sessions
- Logout
- Authentication error handling

Never expose authentication secrets to the frontend.

---

# 11. NAVIGATION

The application must contain:

- DASHBOARD
- STATIONS
- SCANNER
- OPPORTUNITIES
- EARNINGS
- LEDGER
- MOVE MY EARNED MONEY
- TRANSACTIONS
- AUDIT
- NOTIFICATIONS
- SETTINGS
- SECURITY

Every navigation item must lead to a functional screen.

---

# 12. MOVE MY EARNED MONEY

The application must provide a functional:

**MOVE MY EARNED MONEY**

section.

It must support:

- Available balance
- Destination selection
- Add destination
- Transfer amount
- Transfer validation
- Transfer submission
- Transfer status
- Provider reference
- Errors
- Status refresh
- Transfer history

---

# 13. PAYOUT DESTINATIONS

Supported destination categories are:

1. DEBIT CARD
2. BANK ACCOUNT / ACH
3. PAYPAL
4. ONEPAY
5. OTHER SUPPORTED PAYOUT RAIL

**NO CASH APP.**

Do not add Cash App.

---

# 14. DEBIT CARD

Debit-card payouts must use a legitimate provider-supported payout mechanism.

Never store:

- Raw card numbers
- CVV/security codes

Use secure provider-hosted or tokenized collection where supported.

Display masked card information after saving.

If debit-card payouts are not supported by the configured provider:

**DEBIT CARD PAYOUT NOT CONFIGURED / NOT SUPPORTED**

Do not fake the integration.

---

# 15. BANK ACCOUNT / ACH

Where supported, provide legitimate ACH destination handling.

Potential information includes:

- Account holder
- Routing number
- Account number
- Account type

Use secure provider tokenization/vaulting where available.

Never unnecessarily expose or display full account numbers.

If ACH is not configured:

**ACH PAYOUT NOT CONFIGURED**

Do not fake ACH transfers.

---

# 16. PAYPAL

PAYPAL IS THE PAYMENT PROVIDER.

Do not replace PayPal with Cash App.

PayPal must be implemented as a real backend provider integration.

The integration must support the applicable live PayPal functionality, including:

- Server-side credentials
- OAuth
- Payout creation
- Payout status lookup
- Webhook processing
- Webhook signature verification
- Provider references
- Idempotency
- Duplicate-event protection
- Reconciliation
- Provider-confirmed completion

Never expose PayPal secrets in the frontend or Android application.

Never fabricate PayPal confirmations.

Do not mark a transfer COMPLETED without appropriate provider confirmation.

The destination architecture must not be limited to a generic fake PayPal screen.

Use the actual recipient identifier/mechanism required by the configured PayPal payout API.

---

# 17. PAYPAL ENVIRONMENT

The production application must not remain in PayPal sandbox/mock mode.

Production configuration must use the legitimate live PayPal environment when live credentials and configuration are available.

If required credentials are missing:

**PAYPAL SETUP REQUIRED**

Do not simulate successful payouts.

Never invent credentials.

Never expose credentials in source code, frontend code, APK contents, logs, or README files.

---

# 18. ONEPAY

Only implement OnePay if an actual supported live integration exists.

Do not invent an API.

Do not fabricate OnePay transfers.

If unavailable:

**ONEPAY NOT CONFIGURED / NOT SUPPORTED**

---

# 19. OTHER PAYOUT RAILS

Only implement payout rails that have a legitimate supported integration.

Unsupported rails must clearly display:

**NOT CONFIGURED / NOT SUPPORTED**

Never create fake integrations.

---

# 20. TRANSFER STATES

Transfers must support:

- PENDING
- PROCESSING
- COMPLETED
- FAILED
- REVERSED
- CANCELLED

Frontend state must match backend state.

Backend state must match legitimate provider state.

Ledger state must reconcile with provider results.

---

# 21. PAYPAL WEBHOOKS

Webhook processing must:

- Verify PayPal webhook signatures
- Reject invalid webhook requests
- Prevent duplicate processing
- Use provider event identifiers/idempotency
- Update transfer status according to legitimate events
- Store provider references
- Record failures
- Record reversals
- Reconcile completed transfers

---

# 22. SCANNER

The scanner framework must use legitimate sources/connectors.

Do not fabricate scanner results.

If no external connector is configured:

**NO EXTERNAL SOURCE CONNECTOR IS CONFIGURED**

Return an empty legitimate result instead of inventing opportunities.

---

# 23. MANUAL OPPORTUNITY ENTRY

Manual opportunity entry must create a persistent opportunity record.

It must NOT automatically create available money.

It must proceed through the appropriate verification and settlement lifecycle.

---

# 24. DATABASE

The database must persist:

- Owner accounts
- Authentication state
- Stations
- Station states
- Opportunities
- Eligibility
- Submissions
- Verification
- Settlements
- Earnings
- Ledger entries
- Balances
- Destinations
- Transfers
- Provider references
- Provider statuses
- Audit events
- Notifications
- Errors
- Automation state
- Emergency-stop state
- Configuration

The database must be the source of truth.

Do not use temporary frontend state as the financial source of truth.

---

# 25. AUDIT LOGGING

Important actions must be audited, including:

- Login
- Logout
- Station changes
- START
- STOP
- PAUSE
- ENABLE
- DISABLE
- EMERGENCY STOP
- Manual opportunity entry
- Verification
- Settlement
- Destination changes
- Transfer requests
- Provider configuration changes
- Failed transfers
- Reversed transfers
- Security events

Audit records must be persistent.

---

# 26. NOTIFICATIONS

Provide real notification state for important events, including:

- Transfer submitted
- Transfer processing
- Transfer completed
- Transfer failed
- Transfer reversed
- Provider unavailable
- Station error
- Emergency stop
- Verification
- Settlement

Never generate fake notifications.

---

# 27. SECURITY

Never expose:

- PayPal client secret
- JWT secret
- Database credentials
- Private API credentials
- Raw card numbers
- CVV/security codes

Sensitive operations must remain server-side.

---

# 28. BACKEND API

The backend must provide functional API routes for:

- Authentication
- Stations
- Station controls
- Master controls
- Scanner
- Opportunities
- Earnings
- Balance
- Ledger
- Transactions
- Destinations
- Transfers/withdrawals
- Provider status
- PayPal webhook
- Audit
- Notifications
- Health/status

Every route must connect to actual persistent application state.

---

# 29. ERROR HANDLING

Never turn an error into a success.

Handle:

- Provider unavailable
- Missing configuration
- Authentication failure
- Authorization failure
- Network failure
- Database failure
- Invalid transfer
- Insufficient available funds
- Provider rejection
- Provider timeout
- Webhook verification failure
- Unsupported payout rail
- Station failure

Show the actual error/state.

---

# 30. PRODUCTION STATE

The production application must use:

- Production backend
- Production database
- Production authentication
- Production ledger
- Production provider configuration
- Production webhook configuration
- Production API URL

Do not silently use localhost.

Do not silently use mock APIs.

Do not silently use sandbox providers.

Do not leave MOCK mode enabled.

---

# 31. ANDROID APPLICATION

The Android application must be a real compiled application.

It must:

- Launch correctly
- Authenticate
- Connect to the production backend
- Display real backend state
- Operate stations
- Display ledger information
- Display earnings
- Manage destinations
- Submit legitimate transfer requests
- Display provider status
- Display errors

Do not deliver a blank APK.

Do not deliver a static APK.

Do not deliver a placeholder APK.

Do not deliver a development-only package as the final application.

---

# 32. EXPO / REACT NATIVE

Where the current application uses Expo / React Native, preserve that architecture and produce the actual Android application from the final implementation.

The Android application must contain the actual GET MONEY MACHINE application.

---

# 33. NO PRODUCTION TEST DATA

The production application must contain no test financial activity.

Do not create:

- Test money
- Test earnings
- Test
