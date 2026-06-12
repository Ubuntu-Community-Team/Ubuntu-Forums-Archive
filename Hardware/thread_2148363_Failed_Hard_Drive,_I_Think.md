---
title: "Failed Hard Drive, I Think?"
date: 2013-05-24
forum: Hardware
---

### Post by Incarnadine on 2013-05-24
My laptop won't boot anymore, and I'm thinking that the problem is the HDD.

I took the HDD out and put it in a external enclosure and connected it to my spare computer running Ubuntu. When I opened the Disk Manager it said that the HDD wasn't even partitioned!!!! The Windows partition wasn't showing up at all! Disk Manager is showing the HDD as unused. Is there anything I can do?

Thank you so much.

---

### Post by sudodus on 2013-05-24
In order to make it possible to give relevant and detailed advice, you must give us more details about your computer and hard disk drive.

- What computer is it: brand, model, cpu, ram, graphics?

- What is installed in it: version of Windows, version of Ubuntu, dual boot, wubi or ... ?

- What BIOS settings are there: regular BIOS or UEFI?

- What happened before it broke? Something unusual, that you can remember?

- And now, what happened (before you took the HDD out of the laptop) when you booted? Nothing or did it write something?

- And now, are there any sounds from the drive? Can your tools 'see' the drive at all?

-o-

Do you get any S.M.A.R.T. information about the drive? If you want more details about it, install ***smartmontools*** and run ***smartctl*** with superuser privileges. See the manual pages for details

```
man smartctl
```

The brief health assessment is invoked for the second drive with

```
sudo smartctl -H /dev/sdb
```

If you have damaged the partition table you can try ***testdisk*** or ***gpart***, but it is risky, so if you want to save data from the drive ***you need a backup*** (cloned copy or an image) before you go ahead.

If you have partitions and damaged file systems you can try ```
chkdsk /f x:
```for windows file systems and ```
e2fsck -f /dev/sdxy
``` for linux ext file systems (x is the drive letter and y is the partition number).

---

### Post by lethall1 on 2013-05-25
i would do
```
dd /dev/sdX /media/mount/image.iso
```
then download MHDD and burn it to CD or DVD, boot from it and check HDD.
Remap clusters, that are dead (if they are)
then boot again in Live CD and make 
```
fsck /dev/sdXX
``` if there would be any partition table. If not, may be chdisk would rebuild it (but i donk think so)
Good luck!

---

### Post by Incarnadine on 2013-05-25
The hard drive is coming out of a Toshiba Satellite A305-S6837. Windows Vista was on the HDD.

I can hear the HDD spinning in the external enclosure, so I'm assuming the mechanics are OK.

I checked the "Disks" application in Ubutnu just now and found something new. The HDD shows as having two partitions on it now. Both partition types are "unknown" though. Why are the partitions showing as "unknown"? Partition 1 is 1.6 GB and partition 2 is 318 GB.

I'm really lost on this one.

---

### Post by sudodus on 2013-05-25
We don't know yet, but if the drive is failing, it may work only for a short time until it breaks completely.

- If you have very valuable information (that is not backed up already)  on the drive, please make a backup of the drive as soon as possible!

- If the S.M.A.R.T. information is giving you any sign of warning, please make a backup of the drive as soon as possible!

And then start checking the drive with different tools.

---

### Post by Incarnadine on 2013-05-25
> **sudodus said:**
> We don't know yet, but if the drive is failing, it may work only for a short time until it breaks completely.

- If you have very valuable information (that is not backed up already)  on the drive, please make a backup of the drive as soon as possible!

- If the S.M.A.R.T. information is giving you any sign of warning, please make a backup of the drive as soon as possible!

And then start checking the drive with different tools.

The HDD isn't even accessible. I can't even view the S.M.A.R.T. information via the "Disk" utility because it's grayed out. I can check the status of my other HDDs easily, so I know something is very wrong :(

---

### Post by sudodus on 2013-05-25
I'm afraid that some hardware in your drive is failing.

There is a program called ***ddrescue***, that you can use in such situations, and save what can be saved. You can install it into your linux in another installed system or even into a live system. Read the info text, which is very good. There are explanations and examples for typical situations.

```
 info ddrescue
```

Now you have to decide if you should continue to keep the failing drive running, or to stop it until you can make a cloned copy of what can be saved (what can still be read). If it will take a long time until you have ddrescue and a target drive running, or if you need a restart anyway, it is probably better to let the drive rest.

---

### Post by ahallubuntu on 2013-05-25
~

---

### Post by Incarnadine on 2013-05-28
I just recently discovered PhotoRec and used it to recover all the files on the HDD that I needed. I didn't want to try messing around with the partition or reformat anything as it might have destroyed the data that I needed. PhotoRec recovered everything that I needed, so now I can try reformatting the HDD and see if I can get a fresh install of Ubuntu on it :D

---

### Post by sudodus on 2013-05-28
I'm you were able to recover the files you needed :-)

Next, try to find out why the drive is bad, if it is a hardware problem or a damaged file system (software problem).

---

