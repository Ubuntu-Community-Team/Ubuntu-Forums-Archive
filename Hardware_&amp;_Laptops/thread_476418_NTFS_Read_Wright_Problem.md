---
title: "NTFS Read Wright Problem"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by J.One on 2007-06-17
Hi to all Linux users! I 've got this problem : Despite i installed NTFS configuration tool on my ubuntu x64 Feisty Fawn i still can't "write" on disk (that includes create a floder, cut or paste a file.
I have also checked the box that says "Enable write support for external device"...The only detail here that i don't know if matters, for some reason the upper box wich says "Enable write support for internal device is unchecked and it doesen't let you to change it...! I have to hard disks installed on my Pc. The SATA drive is the one with the ubuntu and the other one is an IDE drive wich is my storage wich is NTFS. I can read but not write...
Can you please help me?

---

### Post by neptho on 2007-06-17
This is normal with the default NTFS driver.  It also allows writing, but is fairly unstable.

[Read This](http://ubuntuforums.org/showthread.php?t=217009) for information on NTFS 3g, and how to set it up to read and write from NTFS.

---

### Post by J.One on 2007-06-17
Nepto I saw that post earlier but it doesen't help because it has turtorials only for Dapper and Edgy. I have Feisty and AMD64. It has a how to for AMD 64 users but not Feisty ones...
Any ideas?

---

### Post by neptho on 2007-06-17
You can always:

Install [AutoMatix](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29), and let it install NTFS 3g support for you.

---

### Post by J.One on 2007-06-18
I installed Automatix i enable the Automatix read/write NTFS & FAT32 mounter but i still cant have write access to my other hard drive...Any ideas?

---

