---
title: "Error installing Ubuntu 4.10 as guest on vmware"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by flameco on 2005-01-13
Hi,

I have been trying to install Ubuntu 4.10 "The Warty Warthog" as guest on vmware but without results.

Every time I try to install Ubuntu I get this error during Base System Installation:

The debootstrap program exited with an error (return value 1).
Check /var/log/messages or see virtual console 3 for deatils.


Then I go to Virtual Console 3 pressing Atl-F3 and I find this text on screen:

ismod /lib/modules/2.6.8.1-3-386/kernel/drivers/net/pcnet32.ko
  No matching physical volumes found
  No volume groups found
Reading all physical volumes. This may take a while...
Selecting previosly deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_3.0.16ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-files_3.0.16ubuntu6_i386.deb 
  (--install):
  subprocess pre-installation script kielled by signal (Segmentation fault)
Selecting previously deselected package base-passwd.
Unpacking base-files (from .../base-passwd_3.5.7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-passwd_3.5.7_i386.deb 
  (--install):
  subprocess pre-installation script kielled by signal (Segmentation fault)
Errors where encountered while processing:
  /var/cache/apt/archives/base-files_3.0.16ubuntu6_i386.deb
  /var/cache/apt/archives/base-passwd_3.5.7_i386.deb


I downloaded the ISO image twice and the md5 is ok. I have tried the installation from the iso image directly and burning it on cd but got the same result.

I have been googling but found no answer or clue. If somebody could tell me where can I find a solution or explain why this is happening I would be grateful :D and happy as well.

I'm running vmware 4.0.5 with Fedora Core 1 as host. Thanks in advance.

---

### Post by neuneu on 2005-03-03
[QUOTE=flameco]Hi,

I have been trying to install Ubuntu 4.10 "The Warty Warthog" as guest on vmware but without results.

Every time I try to install Ubuntu I get this error during Base System Installation:

The debootstrap program exited with an error (return value 1).
Check /var/log/messages or see virtual console 3 for deatils.


Then I go to Virtual Console 3 pressing Atl-F3 and I find this text on screen:

ismod /lib/modules/2.6.8.1-3-386/kernel/drivers/net/pcnet32.ko
  No matching physical volumes found
  No volume groups found
Reading all physical volumes. This may take a while...
Selecting previosly deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_3.0.16ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-files_3.0.16ubuntu6_i386.deb 
  (--install):
  subprocess pre-installation script kielled by signal (Segmentation fault)
Selecting previously deselected package base-passwd.
Unpacking base-files (from .../base-passwd_3.5.7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-passwd_3.5.7_i386.deb 
  (--install):
  subprocess pre-installation script kielled by signal (Segmentation fault)
Errors where encountered while processing:
  /var/cache/apt/archives/base-files_3.0.16ubuntu6_i386.deb
  /var/cache/apt/archives/base-passwd_3.5.7_i386.deb


I downloaded the ISO image twice and the md5 is ok. I have tried the installation from the iso image directly and burning it on cd but got the same result.

I have been googling but found no answer or clue. If somebody could tell me where can I find a solution or explain why this is happening I would be grateful :D and happy as well.

I'm running vmware 4.0.5 with Fedora Core 1 as host. Thanks in advance.[/QUOTE]
 Hello,

I am having the same problem. Have you found same solutions?

---

### Post by wojtalik on 2005-03-03
Hey! Please, find the solution at: [http://www.ubuntuforums.org/showthread.php?t=17860](http://www.ubuntuforums.org/showthread.php?t=17860)

Greetings, Marcin

---

