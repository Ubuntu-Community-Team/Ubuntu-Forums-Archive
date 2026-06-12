---
title: "Bad sectors"
date: 2015-08-03
forum: Hardware
---

### Post by tommy2k10 on 2015-08-03
A mate of mine came round  this morning to take a hard drive out of a  laptop and put it in a  caddy.  In the laptop, Ubuntu said it has  multiple bad sectors (going  into seven digits) but in my test machine  (to which the caddy is  connected) Ubuntu reports it as having just one.   Do you know why this is?
Both the HP built-in diagnostics and the Hitach DOS disk test both report the disk has failed.

---

### Post by dino99 on 2015-08-03
grab on the net "gparted live" then boot with it, and check that device with gparted and reformat it (if it can, meaning hdd still alive)

---

### Post by tommy2k10 on 2015-08-03
Thankyou; I did that, it said 'disk read error'!!

---

### Post by weatherman2 on 2015-08-03
You need to check the disk's S.M.A.R.T. Attributes.  There are several different types of "bad sectors."  I'd guess you have a "pending sector count" of 1 or higher.  A "pending sector" is a sector that the drive has been requested to read but cannot - perhaps because it failed.

In Ubuntu, use GSmartControl to get the S.M.A.R.T. Attributes and run tests.  Gparted doesn't do this - it only creates and edits partitions.  You can install GSmartControl in Ubuntu.  (You may need to add options like "-d sat" and "-T permissive" to your smartctl options to get it to read a USB-attached hard drive.)

I have found that laptop hard drives can get into this state, perhaps because of the way they are moved or shut down unexpectedly or something, but that the hard drive may not be physically failing.  Instead, you can zero out the whole drive to clear any pending sectors.  This has worked for me on more than one laptop hard drive.

To zero out a hard drive in Ubuntu (WHICH ERASES EVERYTHING ON IT), assuming the drive is say /dev/sdb, try this:

```
sudo dd if=/dev/zero of=/dev/sdb bs=2048
```

Be VERY CAREFUL with the dd command - if you type it wrong or get the wrong device, you could destroy a lot of data quickly.  Make sure "/dev/sdb" is replaced above with the real device ID of the disk you are trying to zero out!

This dd command could take hours to run, without any output.  After it completes, disconnect the drive and re-connect it and check the S.M.A.R.T. Attributes again and run the extended the S.M.A.R.T. test again.

---

### Post by tommy2k10 on 2015-08-04
Thankyou, it is in the actual machine now.  I haven't done what you said yet, but I thought I would tell you that it is making clicking noises now!

---

### Post by sudodus on 2015-08-04
The disk might be failing (a hardware error). If gparted cannot manage it, you can try to overwrite only the first megabyte and try again with gparted.

```
sudo dd if=/dev/zero of=/dev/sdx bs=1024 count=1024
```

where x is the drive letter, for example **b**, but check very carefully, that you are not overwriting a drive with valuable data!!!

---

### Post by tommy2k10 on 2015-08-04
Thankyou; I will do that today and let you know when finished

---

### Post by tommy2k10 on 2015-08-07
It won't even mount now!

---

### Post by tgalati4 on 2015-08-07
If the manufacturer's diagnostic test (Hitachi in this case) says that the drive has failed, then you can be reasonably sure that the drive is dead.

To answer your original question, it's possible that the bad sectors were remapped to reserve sectors by the disk drive's firmware.  This is OK until your disk drive runs out of reserve sectors.

Without seeing the SMART parameters it's hard to guess what happened to the drive.  But if you can't mount it, then you can't use it any more.

---

### Post by tommy2k10 on 2015-08-07
Do you want me to take a screenshot of the SMART data?

---

### Post by dino99 on 2015-08-07
if the bios is still finding the device, and everything have failed, then try that last option: low format
[http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/)

if that also fail to fix that issue, then think to get an other hdd ;)

---

