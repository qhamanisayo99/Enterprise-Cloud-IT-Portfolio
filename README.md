# Modern Enterprise Cloud IT Support Portfolio
**Target Market Alignment:** South African Enterprise Ecosystems (JHB Corporate, CPT Cloud/BPO, KZN Industrial/Logistics)  
**Author:** Qhamani  

---

## 🛠️ Project 1: Automated Cloud Identity Directory Infrastructure (Entra ID)
* **Objective:** Design, architect, and execute a zero-touch mass deployment of secure enterprise identity objects mapping to regional physical business hubs.
* **Technology Stack:** Microsoft Entra ID (Azure AD), Azure Cloud Shell Sandbox, Microsoft Graph PowerShell SDK, Automation Scripting.
* **Local Market Relevance:** Bypasses manual entry workflows common in L1 environments, replacing them with automated, repeatable script deployments favored by mid-market Managed Service Providers (MSPs) and large financial hubs across Johannesburg.

### 📐 Structural Mapping Architecture
Personnel directory files are injected with regional attributes to support dynamic group segregation and security compliance policies:
* **Johannesburg Hub:** `Department: JHB-Finance` (Focus: Enterprise Financial Controls)
* **Cape Town Hub:** `Department: CPT-Operations` (Focus: Cloud BPO Operations Operations)
* **KwaZulu-Natal Hub:** `Department: KZN-Logistics` (Focus: Industrial Supply Chain Coordinates)

### 💻 Production Deployment Automation Script
```powershell
# 1. Accessing cloud framework via managed service token identity
Connect-MgGraph -Identity

# 2. Localized Multi-Region Corporate Staff Database Array
\$UsersToCreate = @(
    [PSCustomObject]@{FirstName="Sipho"; LastName="Mthembu"; Dept="JHB-Finance"; Title="Finance Analyst"; MailNick="smthembu"}
    [PSCustomObject]@{FirstName="Chantel"; LastName="Smit"; Dept="CPT-Operations"; Title="Operations Lead"; MailNick="csmit"}
    [PSCustomObject]@{FirstName="Farai"; LastName="Gumbo"; Dept="KZN-Logistics"; Title="Logistics Coordinator"; MailNick="fgumbo"}
)

# 3. Dynamic Default Domain Extraction Routing Routing
CurrentDomain = (Get-MgOrganization).VerifiedDomains | Where-Object _.IsDefault} | Select-Object -ExpandProperty Name

# 4. Clean Execution Loop Deploying Accounts with Splatting Architecture
foreach (\$User in \(UsersToCreate) {\)PasswordProfile = @{ Password = "TemporarySecurePassword2026!"; ForceChangePasswordNextSignIn = \(true }\)UserParams = @{
        DisplayName       = "(User.FirstName) (User.LastName)"
        GivenName         = \$User.FirstName
        Surname           = \$User.LastName
        Department        = \$User.Dept
        JobTitle          = \$User.Title
        UsageLocation     = "ZA"
        MailNickname      = \$User.MailNick
        UserPrincipalName = "\$(\(User.MailNick)@\)CurrentDomain"
        AccountEnabled    = \$true
        PasswordProfile   = \$PasswordProfile
    }
    
    New-MgUser @UserParams
    Write-Host "Successfully automated creation for user account: \$(\(User.MailNick)@\)CurrentDomain" -ForegroundColor Green
}
```

### 🧠 Real-World Engineering Troubleshooting Log
* **Issue Encountered:** Web terminal execution strings stripped out PowerShell backtick escape operators (` ` `) during direct clipboard injections into browser frames, spitting out syntax errors (`A positional parameter cannot be found that accepts argument 'True'`).
* **Root Cause Diagnostics:** Browser text encodings broke line-continuation arrays, isolating key validation arguments onto separate execution lines.
* **Engineering Resolution:** Refactored the core script block away from primitive line breaks into structured **PowerShell Splatting** hashtables (`@UserParams`). This bundles all required strings cleanly into a single memory object, maximizing deployment reliability in remote browser-based engineering consoles.
