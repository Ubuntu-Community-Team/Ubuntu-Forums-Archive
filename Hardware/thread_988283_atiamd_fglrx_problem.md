---
title: "ati/amd fglrx problem"
date: 2008-11-20
forum: Hardware
---

### Post by maneesh77 on 2008-11-20
UBUNTU 8.10 laptop with ATI radeon HD3200

When I try to activate the driver I get this error

SystemError: Failed to lock /var/cache/apt/archives/lock

Please help

---

### Post by philip l on 2009-01-02
I found a work around with fglrx problem to get dual monitors working.  I have ati readon hd 2600pro with dual monitors.  in applications open ATI Catalyst Control Center.  First set which monitor is #1, then open from the drop down menu under dual monitors and set Expand desktop either to the right or left from monitor #1.  Save changes.  But "DO NOT RESTART COMPUTER" When it tells you "for changes to take effect restart.  Just close that window, without restating.  You can then operate with the dual monitors.  This NO RESTART works with other changes you wish to make.  The drawback is you must do this each time you start the computer, as it will revert back to either clone monitors or default.  But it is a work around until there is a true fix from ATI

---

### Post by nick09 on 2009-01-02
Do you get the same error when you try to install a program from commandline or Applications--> Add/Remove?

---

