---
title: "programme installation is failing to create relevent folders in usr/share"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by nagaraj on 2009-04-18
starting this in this forum for want of better place. please redirect me if necesary.
trying to install an accounting ware called 'lazy8 ledger' which requires sun's java and jedit. i have managed to install both but when i try to install the relevant plugin it returns error - [COLOR="black"]_an i/o eror occured (/usr/share/jedit/jars.....(permission denied))_[/COLOR]. which means the installation programme is not able to create thte relevant folders though i am logged in as root user. what is the problem and can anybody help in this ? i am also gettting some help from the programme designer.

---

### Post by lemming465 on 2009-04-19
Typical reasons for an I/O error on /usr would be a) out of space b) out of inodes c) mounted read-only.  What do **df -m /usr; df -i /usr; mount | grep /usr** tell you?

There could also be bugs in the installer for the application, which is perhaps more likely.

---

### Post by nagaraj on 2009-04-22
ran it and this was the result 
~$ df -m /usr; df -i /usr; mount | grep /usr
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1               148536      7117    133933   6% /
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            9584640  238482 9346158    3% /.
not able to make out anything. any suggestions?

---

### Post by lemming465 on 2009-04-22
It doesn't look like a problem with the filesystem, so it's something about the application installer.  

Is there a specific JRE or JDK version 'lazy8 ledger' prefers?  If so, try that. 

If you run the installer twice, does the second run get any farther, or does it always die in exactly the same spot?

---

