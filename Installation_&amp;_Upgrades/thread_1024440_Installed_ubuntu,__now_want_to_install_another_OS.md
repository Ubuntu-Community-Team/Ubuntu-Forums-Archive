---
title: "Installed ubuntu,  now want to install another OS"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Relief on 2008-12-29
So I have just installed ubuntu and was wanting to install windows xp on a dual boot, and I am unsure what to do. Is there a tool to partician off my HD, etc? I am new to using this system and am unsure on how to proceed. Any help is appreciated. 

- Relief

---

### Post by gettinoriginal on 2008-12-29
Great tutorial here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by plarq on 2008-12-29
> **Relief said:**
> So I have just installed ubuntu and was wanting to install windows xp on a dual boot, and I am unsure what to do. Is there a tool to partician off my HD, etc? I am new to using this system and am unsure on how to proceed. Any help is appreciated. 

- Relief

Use gparted to repartition your disk without losing data.
---
Back up your MBR using dd.
Install Windows
Use Live CD or Rescue CD or USB to boot into Linux
use dd to recover MBR
setup GRUB
---
Alternatively, copy a working Windows on a new NTFS partition (Assume you have license )
setup GRUB.

---

### Post by Relief on 2008-12-29
I do have a working xp license so that is not an issue (no sense in stealing windows best os so far). 

Though, I was wondering, before I go through all this, I did install the 32 bit version of ubuntu, but I have a 64 bit capable laptop, am I missing much by using the 32 bit architecture? If so I supose I could just format and install windows then ubuntu over again. 

Thanks, 

- Relief

---

