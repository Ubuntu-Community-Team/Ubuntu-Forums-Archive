---
title: "Using remote printers from applications with IPP"
date: 2008-09-20
forum: General Help
---

### Post by joehte on 2008-09-20
Hi,

I have following setup:
 - Ubuntu Server 7.10 which has printer shared printer connected
 - Two client machines with Ubuntu 8.04 that try using this printer remotely with IPP

Printing test pages works from the clients, but printing from applications does not. This is apparently a well-known bug in Hardy Heron's gtk:

[https://bugs.launchpad.net/ubuntu/hardy/+source/gtk+2.0/+bug/258104](https://bugs.launchpad.net/ubuntu/hardy/+source/gtk+2.0/+bug/258104)

Is there a workaround to get this working? Due to my previous experiences about the hassle with Samba I wouldn't want to start configuring that to the server. The next Ubuntu version which has this fixed is still over month away and installing it at its current beta state sounds like asking trouble (especially for my wife who uses the other computer). Is there some smart and easy way to get the printing working?

Thanks.

---

### Post by momist on 2008-09-20
Joe,

Do you have Ubuntu backports enabled?  If there's a fix in the new Intrepid Ibex, itmay have been sent into hardy updates.

---

### Post by joehte on 2008-09-20
> **momist said:**
> Joe,

Do you have Ubuntu backports enabled?  If there's a fix in the new Intrepid Ibex, itmay have been sent into hardy updates.

Yes I do. Apparently the patch for hardy heron has been there a couple months but it has not been backported. It's unclear when the team will have time to port it as it's not marked as high priority problem. So that's why I'm looking for some way around this problem.

---

