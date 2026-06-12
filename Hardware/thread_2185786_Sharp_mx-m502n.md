---
title: "Sharp mx-m502n"
date: 2013-11-04
forum: Hardware
---

### Post by rino.raimato on 2013-11-04
Hello Guys 
I have problem with my Sharp MX-M502N  I setup the Copier to authenticate users by Pin code, with windows I Don't have problem to print 
But using Ubuntu I have many problems because I'm not able to setup to allow users to print.
I had just try these solutions but them does not work 

FIRST ONE
*% ====================================================================
*% Base JCL key code option 
*JCLOpenUI JCLPasscode/Key Code: PickOne
*OrderDependency: 10 JCLSetup *JCLPasscode
*DefaultJCLPasscode: None
*JCLPasscode None/No Code: ""
*JCLPasscode 12345: " <at> PJL SET ACCOUNTNUMBER = 12345<0A>"
*JCLCloseUI: *JCLPasscode
*% ====================================================================

SECOND ONE

*OpenGroup: Authentication

*% Base JCL key code option 
*OpenUI JCLPasscode/Key Code: PickOne
*OrderDependency: 10 JCLSetup *JCLPasscode
*DefaultJCLPasscode: None
*JCLPasscode None/No Code: ""
*JCLPasscode 1111: "@PJL SET ACCOUNTNUMBER = \"1111\"<0A>"
*JCLPasscode 2222: "@PJL SET ACCOUNTNUMBER = \"2222\"<0A>"
*JCLPasscode 3333: "@PJL SET ACCOUNTNUMBER = \"3333\"<0A>"
*CloseUI: *JCLPasscode

*% Custom JCL key code option 
*CustomJCLPasscode True: "@PJL SET ACCOUNTNUMBER = \"\1\"<0A>"
*ParamCustomJCLPasscode Code/Key Code: 1 passcode 1 8

*CloseGroup: Authentication



Someone could help me?

Thank you for your time

---

