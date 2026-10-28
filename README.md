# NAMADE KADDA (ನಮ್ಮದೇ ಕಡ್ಡ)
> **Source Globally. Build Intelligently.**  
> *One intelligent workspace for global industrial sourcing, supplier discovery, and manufacturing procurement.*

---

## 1. Executive Summary & Product Vision

**Namade Kadda** is an AI-powered B2B sourcing, procurement, and manufacturing marketplace engineered to streamline high-value technical procurement for enterprise buyers, industrial suppliers, and contract manufacturers worldwide.

Taking architectural and design inspiration from:
- **Scoutbee**: AI-powered industrial supplier discovery and capability matching across international borders.
- **Alibaba.com**: Multi-supplier global catalog browsing, multi-currency pricing, bulk RFQ dispatch, competitive quote comparisons, and rich seller product/inventory management.
- **Coupa**: Enterprise-grade procurement workflows, Purchase Order (PO) state machines, supplier portals, agreement leakage tracking, counteroffer negotiations, and role-based administration.

Rather than serving as another generic static product catalog or e-commerce storefront, Namade Kadda introduces a unified, two-sided platform:
1. **Explainable AI Buyer Workspace**: featuring a **Council of 6 Specialist AI Agents**, a **Live Global Product Marketplace**, RFQ dispatch, interactive quote comparison matrix, landed cost calculators with PDF export, and engineering BOM builders.
2. **Dedicated Seller & Manufacturer Workspace**: featuring an audited **10-step operational workflow**, real-time RFQ responses, decimal-safe quotation authoring with revision tracking, counteroffer negotiations, shop-floor order milestone advancement synced with buyer timelines, a **6-role AI Seller Assistant**, commercial telemetry with CSV export, and in-app notifications.

---

## 2. Seeded Demonstration Accounts

The platform includes pre-configured accounts with pre-hashed bcrypt credentials and rich synthetic industrial datasets:

| Role | Email Address | Password | Dedicated Workspace & Capabilities |
| :--- | :--- | :--- | :--- |
| **Enterprise Buyer** | `buyer@namadekadda.demo` | `NmkBuyer@2026` | **`/dashboard/buyer`**: Browse `/products`, issue RFQs, evaluate quotes side-by-side, adjust scoring weights, approve POs, generate Trade PDFs, and build engineering BOMs. |
| **Industrial Supplier** | `supplier@namadekadda.demo` | `NmkSupplier@2026` | **`/dashboard/supplier`**: Manage catalog & inventory, review incoming RFQs, submit binding quotes, negotiate commercial terms, advance PO milestones, consult 6 AI seller advisors, export analytics CSV. |
| **Platform Administrator** | `admin@namadekadda.demo` | `NmkAdmin@2026` | **`/dashboard/admin`**: Inspect platform GMV metrics, review and approve new supplier registrations, manage user activation, inspect audit logs. |

> **Quick Access**: The `/login` page includes a **Role Selector** (Buyer, Supplier, Administrator) and a **"TRY DEMO ACCOUNT"** panel with one-click credential auto-fill buttons.

---

## 3. Seeded Synthetic Products & Global Suppliers

The platform comes pre-seeded with verified global suppliers and industrial products across India, Germany, China, Japan, and the United States:

| Product Name | Category | Origin Country | Supplier Name & Hub | Unit Price | MOQ | Lead Time | Manufacturing Capability |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Stainless-steel mounting brackets** | Hardware & Fasteners | 🇮🇳 India | MetalCraft Industries (Pune, IN) | ₹450 (~$5.40) | 100 pcs | 14 days | Stamping, Laser Cutting, ISO 9001 |
| **Industrial ball bearings** | Machinery Components | 🇩🇪 Germany | Precision Dynamics GmbH (Stuttgart, DE) | €42.00 (~$45.80) | 50 pcs | 10 days | Precision CNC Grinding, DIN EN 9100 |
| **CNC-machined aluminium components** | Custom Fabrication | 🇨🇳 China | Apex Global Manufacturing (Shenzhen, CN) | $18.50 | 200 pcs | 18 days | 5-Axis CNC Milling, Anodizing |
| **Industrial sensors** | Electronics & Sensors | 🇯🇵 Japan | Nippon Advanced Robotics (Osaka, JP) | ¥12,500 (~$82.00)| 25 pcs | 7 days | Optoelectronic Cleanroom, IATF 16949 |
| **Hydraulic valves** | Hydraulics & Fluid Power | 🇺🇸 United States | Titan Heavy Dynamics LLC (Detroit, US) | $145.00 | 20 pcs | 12 days | High-Pressure Hydro-Testing, ASME |
| **Copper sheets** | Raw Materials | 🇮🇳 India | Bharat Precision Alloys Ltd (Mumbai, IN) | ₹2,800 (~$33.60) | 50 pcs | 15 days | Continuous Casting, Electrolytic Grade |
| **CNC Machined Flange Adapter M20** | CNC Machining | 🇮🇳 India | Apex Precision Engineering (Bengaluru, IN) | $45.00 | 50 pcs | 14 days | 5-Axis Milling, Turning, ISO 9001:2015 |

---

## 4. Real vs. Simulated Capabilities Matrix

To maintain production integrity and compliance for an academic/student prototype, every platform capability is clearly categorized:

| Feature Domain | Real Implementation (Database & Backend) | Simulated / Demonstration Boundary |
| :--- | :--- | :--- |
| **Authentication & RBAC** | Real bcrypt password hashing, real JWT session tokens, role-based route guards (`BUYER`, `SUPPLIER`, `ADMIN`), database user records. | External OAuth single-sign-on (SSO) providers and enterprise SAML are bypassed in favor of local JWT. |
| **Shared Catalog & Marketplace** | Real database catalog querying, multi-attribute filtering (category, origin country, price range, MOQ, lead time), full-text search. Seller-published products immediately appear in the public `/products` marketplace. | Catalog items are seeded synthetic benchmarks rather than live scraped web listings. |
| **Company Profile & Completeness** | Real database persistence of 13 extended profile fields (legal name, factory address, export countries, production capacity, materials, certifications) and dynamic 0–100% completeness formula. | Verification badge submission transitions status from UNVERIFIED to PENDING/ACTIVE without third-party physical site auditors. |
| **Incoming RFQs & Decision Actions** | Real RFQ matching against supplier capabilities, Accept / Reasoned Decline / Clarification inquiry actions, in-app notification dispatches. | Quotations are submitted by verified platform accounts rather than external email parsers. |
| **Decimal-Safe Quotations** | Multi-line itemized cost breakdown, subtotal/shipping/tax/discount arithmetic using Python `Decimal`, revision history tracking (`rev-1`, `rev-2`), validity date enforcement. | Payment gateway integration is demarcated as "Payment data not configured". |
| **Negotiation Workspace** | Real database counteroffer message thread (`negotiation_messages` table), structured commercial proposal fields (price, lead time, terms), AI strategy advisor. | Counterparties are simulated via platform users or demo accounts rather than live external chat protocols. |
| **Order Milestones & Buyer Sync** | Real Purchase Order state-machine transitions (`CONFIRMED` $\to$ `IN_PRODUCTION` $\to$ `READY_TO_SHIP` $\to$ `SHIPPED` $\to$ `DELIVERED`). Advancing status in seller portal immediately updates the buyer's order tracking view. | Carrier tracking numbers (`SIM-TRK-XXXX-YYYY`) are synthetic and do not ping live FedEx/DHL APIs. |
| **Commercial Telemetry & CSV** | Real calculation of 11 seller metrics: Quoted vs Accepted vs Delivered value, Acceptance %, Avg Response Time, On-Time Delivery %, Product Performance funnel, Country revenue breakdown, and streaming RFC 4180 CSV export. | Payments Received metric displays "$0.00" with explicit "Payment data not configured" status banner. |
| **AI Multi-Agent Systems** | 6 Specialist Buyer Agents + 6 Specialist Seller Operational Roles (RFQ Analyzer, Cost Estimator, Negotiation Coach, Compliance Validator, Production Planner, Catalog Optimizer). | Deterministic offline adapter ensures 100% test reliability and zero API bill shock without external API credentials. |
| **Trade Cost PDF Report** | Real binary PDF generation using ReportLab streaming downloadable documents with itemized CIF breakdown, duties, documentation checklist, and statutory legal disclaimers. | Disclaimers state calculations are estimations and require licensed customs broker verification for formal entry. |
| **In-App Notification Center** | Real database persistence of system notifications (`notifications` table), unread count badge, mark-as-read, and mark-all-as-read actions. | Browser Web Push webhooks are simulated via in-app popovers and badges. |

---

## 5. Architecture & Technology Stack

```
┌─────────────────────────────────────────────────────────────┐
│                 NAMADE KADDA ARCHITECTURE                   │
├──────────────────────────────┬──────────────────────────────┤
│  Frontend (Port 3000)        │  Backend (Port 8000)         │
│  - Next.js 16 (App Router)   │  - FastAPI (Python 3.14+)    │
│  - React 19 & TypeScript     │  - Pydantic v2 validation    │
│  - Tailwind CSS v4           │  - PyJWT & Bcrypt hashing    │
│  - Lucide React icons        │  - SQLAlchemy 2.0 ORM        │
│  - Recharts analytics        │  - ReportLab PDF Engine      │
│  - Decimal-safe math         │  - CSV streaming export      │
├──────────────────────────────┼──────────────────────────────┤
│  Persistence Layer           │  AI Orchestration Layer      │
│  - SQLite (Local zero-setup) │  - 6 Buyer Specialist Agents │
│  - PostgreSQL compatible     │  - 6 Seller Operational Roles│
│  - Full Relational Schema    │  - Deterministic Demo Adapter│
│  - Dynamic column migration  │  - Pluggable LLM Gateway     │
└──────────────────────────────┴──────────────────────────────┘
```

---

## 6. Left-Side Navigation Hierarchy

### Supplier / Manufacturer Workspace (Exact 10 Items)
When logged in as a Supplier (`supplier@namadekadda.demo`), the persistent left sidebar ([`Sidebar.tsx`](frontend/src/components/Sidebar.tsx)) displays the exact 10-step hierarchy:

1. **Dashboard** (`/dashboard/supplier`) — Central hub with 8 KPI cards, Financial distinction, Sections A–F (RFQ inbox, quotes, active orders, low inventory, recent inquiries, performance trend).
2. **Company Profile** (`/supplier/profile`) — Legal identity, factory location, manufacturing capabilities envelope, materials supported, certifications, profile completion progress, accreditation submission.
3. **Products & Inventory** (`/supplier/products`) — Multi-state catalog management (Draft, Published, Archived), instant sync with public `/products` marketplace.
4. **Incoming RFQs** (`/supplier/rfqs`) — Matching buyer inquiries with Accept, Decline (with required reason), Clarification inquiry, and Prepare Quotation triggers.
5. **My Quotations** (`/supplier/quotations`) — Itemized decimal-safe pricing, Incoterms, payment terms, revision numbering, and status filters.
6. **Negotiations** (`/supplier/negotiations`) — Counteroffer timeline, commercial terms proposals, and AI Negotiation Strategy Guidance.
7. **Orders & Fulfilment** (`/supplier/orders`) — 5-stage shop-floor milestone tracking synced real-time with the buyer PO timeline.
8. **AI Seller Assistant** (`/supplier/ai-assistant`) — 6 specialist operational roles (RFQ Analyzer, Cost Estimator, Negotiation Coach, Compliance Validator, Production Planner, Catalog Optimizer) with inspectable inputs/outputs.
9. **Analytics & Telemetry** (`/supplier/analytics`) — 11 core metrics, Quoted vs Accepted vs Delivered distinction, Recharts monthly trend, country breakdown, and working **"Export Analytics CSV"** button.
10. **Settings** (`/supplier/settings`) — Account operator identity, enterprise commercial defaults (currency, timezone, Incoterms, payment terms), notification webhooks, password rotation, and workspace sign out.

*Sidebar Header*: Company Identity area displaying company name, factory location, verification badge, profile completion progress bar, and in-app notification center popover.

---

### Buyer Workspace Hierarchy
When logged in as a Buyer (`buyer@namadekadda.demo`):
1. **Products** (`/products`) — Global industrial marketplace catalog.
2. **Dashboard** (`/dashboard/buyer`) — Procurement spend overview and active requests.
3. **Order & Fulfilment** (`/orders`) — Real-time PO tracking with milestone progress.
4. **AI Procurement Council** (`/agents`) — Multi-agent procurement council execution timeline.
5. **Engineering & BOM** (`/bom`) — Interactive Bill of Materials builder and CSV export.
6. **Trade & Compliance** (`/trade`) — Landed cost calculator and downloadable PDF report.
7. **Discover Suppliers** (`/suppliers`) — Verified supplier catalog with capability filters.
8. **Analytics & Telemetry** (`/analytics`) — Spend distribution, agreement leakage audit log.
9. **Sourcing Requests** (`/sourcing`) — Natural-language requirement structuring.
10. **Quotations & RFQs** (`/quotations`) — Multi-attribute weighted scoring matrix.

---

## 7. Quickstart Guide (Windows PowerShell)

### Prerequisites
- **Python 3.10+** (Python 3.14 verified)
- **Node.js 18+** (Node.js 24 verified)

### Running the Services

#### 1. Backend (FastAPI on Port 8000)
```powershell
cd C:\Users\abhin\Downloads\namade-kadda\backend
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```
API Documentation will be live at: `http://127.0.0.1:8000/docs`

#### 2. Frontend (Next.js on Port 3000)
```powershell
cd C:\Users\abhin\Downloads\namade-kadda\frontend
npm run dev
```
Web Application will be live at: `http://localhost:3000`

---

## 8. Verification & Test Evidence

### Automated Backend Test Suite (`pytest`)
All **26 automated tests** pass with 100% success rate:
```
tests/test_api.py::test_health PASSED                                    [  3%]
tests/test_api.py::test_suppliers_list_and_filter PASSED                 [  7%]
tests/test_api.py::test_sourcing_parse_and_create PASSED                 [ 11%]
tests/test_api.py::test_rfq_and_quotation_workflow PASSED                [ 15%]
tests/test_api.py::test_order_status_transitions PASSED                  [ 19%]
tests/test_api.py::test_bom_management_and_csv PASSED                    [ 23%]
tests/test_api.py::test_ai_agent_orchestration_demo_mode PASSED          [ 26%]
tests/test_api.py::test_trade_compliance_estimate PASSED                 [ 30%]
tests/test_api.py::test_analytics_dashboard_backed_by_db PASSED          [ 34%]
tests/test_api.py::test_demo_accounts_authentication PASSED              [ 38%]
tests/test_api.py::test_buyer_registration_and_profile PASSED            [ 42%]
tests/test_api.py::test_supplier_registration_and_admin_verification PASSED [ 46%]
tests/test_api.py::test_role_based_access_control PASSED                 [ 50%]
tests/test_api.py::test_forgot_password_simulated PASSED                 [ 53%]
tests/test_api.py::test_quotations_list_endpoint PASSED                  [ 57%]
tests/test_api.py::test_products_marketplace_api PASSED                  [ 61%]
tests/test_api.py::test_trade_cost_pdf_generation PASSED                 [ 65%]
tests/test_supplier_workspace.py::test_supplier_login_and_auth PASSED    [ 69%]
tests/test_supplier_workspace.py::test_company_profile_update_and_verification PASSED [ 73%]
tests/test_supplier_workspace.py::test_product_lifecycle_and_marketplace_visibility PASSED [ 76%]
tests/test_supplier_workspace.py::test_supplier_rfqs_and_quotation_workflow PASSED [ 80%]
tests/test_supplier_workspace.py::test_negotiation_workspace PASSED      [ 84%]
tests/test_supplier_workspace.py::test_seller_ai_assistant_specialist_roles PASSED [ 88%]
tests/test_supplier_workspace.py::test_supplier_analytics_and_csv_export PASSED [ 92%]
tests/test_supplier_workspace.py::test_in_app_notifications PASSED       [ 96%]
tests/test_supplier_workspace.py::test_full_buyer_to_seller_journey PASSED [100%]

====================== 26 passed, 194 warnings in 8.72s =======================
```

### Next.js Production Build (`npm run build`)
All **33 routes** compile with zero TypeScript or Turbopack errors:
```
✓ Compiled successfully in 1818ms
✓ Generating static pages using 11 workers (33/33) in 1499ms
  Finalizing page optimization ...

Route (app)
┌ ○ /
├ ○ /_not-found
├ ○ /agents
├ ○ /analytics
├ ○ /bom
├ ○ /dashboard
├ ○ /dashboard/admin
├ ○ /dashboard/buyer
├ ○ /dashboard/overview
├ ○ /dashboard/supplier
├ ○ /forgot-password
├ ○ /help
├ ○ /login
├ ○ /orders
├ ○ /products
├ ○ /quotations
├ ○ /register
├ ○ /settings
├ ○ /sourcing
├ ○ /supplier/ai-assistant
├ ○ /supplier/analytics
├ ○ /supplier/negotiations
├ ○ /supplier/orders
├ ○ /supplier/products
├ ○ /supplier/profile
├ ○ /supplier/quotations
├ ○ /supplier/rfqs
├ ◐ /supplier/rfqs/[id]
├ ○ /supplier/settings
├ ○ /suppliers
└ ○ /trade

○  (Static)             prerendered as static content
◐  (Partial Prerender)  prerendered as static HTML with dynamic server-streamed content
```
