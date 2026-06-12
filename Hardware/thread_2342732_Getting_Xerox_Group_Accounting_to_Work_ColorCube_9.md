---
title: "Getting Xerox Group Accounting to Work ColorCube 9303"
date: 2016-11-09
forum: Hardware
---

### Post by worswick on 2016-11-09
Download and install CUPS

Download the CUPS driver for Linux from Xerox website

Download the PPD drivers from Xerox Website here [URL="http://www.support.xerox.com/support/colorqube-9300-series/file-download/enus.html?operatingSystem=win7&fileLanguage=en&contentId=128027&from=downloads&viewArchived=false"]Generic PPD

[/URL]
Use the Xerox information [here]("http://www.office.xerox.com/support/dctips/dc09cc0450.pdf") 

Copy the PPD driver and edit accordingly. This was for group accounting

*JCLBegin:"<1B>%-12345X@PJL JOB<0A>@PJL<0A>@PJL COMMENT XRXbegin<0A>" <---- Existing line

*% Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAGroup
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,001<22>;<0A>"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,001<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGeneralAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,001<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,3000<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,001<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,001<22>;<0A>"
*JCLCloseUI: *JCLAccounting

Since I was using Group Accounting, set 
*DefaultJCLAccounting: XSAGroup 

AND put the settings AFTER 
*JCLBegin:"<1B>%-12345X@PJL JOB<0A>@PJL<0A>@PJL COMMENT XRXbegin<0A>"

---

### Post by slickymaster on 2016-11-09
*Thread moved to **Hardware**.*

---

