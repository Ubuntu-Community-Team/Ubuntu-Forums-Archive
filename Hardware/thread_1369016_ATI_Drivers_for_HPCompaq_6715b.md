---
title: "ATI Drivers for HP/Compaq 6715b"
date: 2009-12-31
forum: Hardware
---

### Post by TechieJustin on 2009-12-31
Hi folks, I have a Compaq 6715b and I just installed Ubuntu 9.10 AMD64. 
I can't seem to get the driver installation right. 

I downloaded downloaded ati-driver-installer-9-3-x86.x86_64.run 

justin@Ubuntu-lappy:~/Downloads$ sh ati-driver-installer-9-3-x86.x86_64.run 
Created directory fglrx-install.yPqZeU 
Verifying archive integrity... All good. 
Uncompressing ATI Proprietary Linux Driver-8.593............ 
================================================== 
 ATI Technologies Linux Driver Installer/Packager 
================================================== 

***Error: ./default_policy.sh does not support version*** 
default:v2:x86_64:lib::none:2.6.31-16-generic; make sure that the  version is being 
correctly set by --iscurrentdistro 

Removing temporary directory: fglrx-install.yPqZeU 

The 802.11 also doesn't work, but I figure I better work on the display  first. 
Thanks!

---

### Post by TechieJustin on 2010-01-01
Ok...
I tried installing slrx via apt-get and it still doesn't work.  Anyone have any advice?

---

### Post by coldraven on 2010-01-10
Hi, I just installed Ubuntu 9.10 on my Compaq 6715b. Everything seems to work out of the box and the screen flicker problem that I had with 9.04 has gone. I installed the CompizConfig settings manager and have the spinning cube working smoothly. AFAIK you cannot use the ATI proprietary driver as it will not work with the version of Xorg in this release. That's why ATI have it in the Legacy section.  Good luck, tell me if you find out how to do it!

---

### Post by coldraven on 2010-01-10
P.S. I gave up trying after looking everywhere including here  [http://groups.google.co.uk/group/x1250?lnk=srg&hl=en](http://groups.google.co.uk/group/x1250?lnk=srg&hl=en)

---

