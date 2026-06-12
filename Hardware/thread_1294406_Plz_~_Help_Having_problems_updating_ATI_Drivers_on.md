---
title: "Plz ~ Help :Having problems updating ATI Drivers on Toshiba..."
date: 2009-10-18
forum: Hardware
---

### Post by MMarques007 on 2009-10-18
*I'm having problems updating my drivers for my Toshiba Satellite L305D-S5900. The hardware on the laptop is a ATI on-board x1250 Radeon and a AMD 64 X2 TK-57 CPU and 3GB of memory. I am using Ubuntu 9.04. If anyone can help please... I am new to Linux but if you can show me some easy steps that would be nice... Thanks ahead of time...*

[SIZE=4]"This is what I am getting in my Terminal:"[/SIZE]

root@mmarques007-laptop:/home/mmarques007# sh ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.AmVEII
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593....................................................................................................................
............................................................................................................................
...........................................................................................................................
............................................................................................................................
............................................................................................................................
............................................................................................................................
ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-15-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.AmVEII

---

### Post by MMarques007 on 2009-10-18
Please Someone Help, Going Crazy Trying To Figure Out The Problem......... Crying for help, please... :(

---

### Post by night-wing on 2009-10-20
Hello.

You won't have luck in this case. The ati x1250 isn't supported with the proprietary ati driver anymore in combination with jaunty (the new xorg). You'll have to use the open source driver!

Regards
nightwing

---

