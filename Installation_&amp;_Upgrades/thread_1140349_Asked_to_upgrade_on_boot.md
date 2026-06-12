---
title: "Asked to upgrade on boot"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by JoelMay on 2009-04-27
Hello,

I was using Wubi before and make a compressed file of all the files on my hard drive (excluding a few directories like media).  Then I formatted my drive an installed Ubuntu server (for the smaller disk, I have a 650 CD-RW).  Then I copied my files back.  Now every boot I get:
```
A distribution volume with software packages has been detected.

Would you like to try to upgrade from it automatically?
```

Whenever I click the "Run upgrade" button it looks like it's upgrading the OS, then asks me if it can get the updates from the internet; I tell it yes and after a bit of doing stuff it says:
```
Your system is up-to-date

There are no upgrades available for your system. The upgrade will now be canceled.
```

It does this 2 times every boot.  What do I do to fix it?:confused:

---

### Post by JoelMay on 2009-04-27
Nobody has a fix? :(

---

### Post by JoelMay on 2009-05-08
> **JoelMay said:**
> Hello,

I was using Wubi before and make a compressed file of all the files on my hard drive (excluding a few directories like media).  Then I formatted my drive an installed Ubuntu server (for the smaller disk, I have a 650 CD-RW).  Then I copied my files back.  Now every boot I get:
```
A distribution volume with software packages has been detected.

Would you like to try to upgrade from it automatically?
```

Whenever I click the "Run upgrade" button it looks like it's upgrading the OS, then asks me if it can get the updates from the internet; I tell it yes and after a bit of doing stuff it says:
```
Your system is up-to-date

There are no upgrades available for your system. The upgrade will now be canceled.
```

It does this 2 times every boot.  What do I do to fix it?:confused:


I found my problem.  I left the install CD in my drive.  My BIOS is set to ignore the CD drive at boot unless I tell it to use it.

---

