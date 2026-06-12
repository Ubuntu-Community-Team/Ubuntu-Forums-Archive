---
title: "Cannot install on Gateway laptop"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Maerwyn on 2009-10-23
Hello.

We've been trying to install on a Gateway laptop for almost a year now.  Each time, the installer seems to go through well enough, but on restarting we get nothing but errors.  We have tried Ubuntu, Kubuntu and Suse.

The errors run for a while, but they all seem identical.  Then they stop.  Here is what's on screen when the errors finally stop moving (Kubuntu install attempt this time):

[140.009133] ata1.00 : status: {DRDY ERR}
[140.099279] ata1.00 : error :{unc}
[142.707309] ata1.00 : exception EMask 0x0 sact 0x1 SErr 0x0 action 0x0
[142.707365] ata1 00 : irq_stast 0x40000008
[142.707420] ata1.00 : cmd 60/08 : 00 : 28 : 60 ; 38/00:00:3a:00:06/40 tag 0 ncq 4096 in
[142.707422] res 41/46 : 08 : 2f : 60 :38/95 : 00 : 3a : 00 : 00/00 EMASK 0x409 (media error) <f>
[numbers missing] end_request : I/O error, dev sda sector 97677316T
[numbers missing]biffer I/O error on device sda, logical block 122096645

We know the laptop works, because we keep having to put Vista on it every time an installation fails, and Vista installs with no difficulty.  But we don't want Vista.  Can anybody help with this?

---

### Post by RJARRRPCGP on 2009-10-23
Looks like a bad HDD.

---

### Post by Mark Phelps on 2009-10-23
DRDY ERR on a SATA drive indicates some kind of data transfer error -- but that could be due to controller problems, bus delays, timeouts, and any number of other things.

One way to check this is to find out the manufacturer of the drive, go to their website, and see if they have some kind of drive diagnostics utility you can download and run against the drive.

---

### Post by RJARRRPCGP on 2009-10-23
"UNC" indicates a bad sector on your HDD.

---

