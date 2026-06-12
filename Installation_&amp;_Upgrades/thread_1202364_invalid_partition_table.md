---
title: "invalid partition table"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-07-02
Had dual boot working with Jaunty, windows XP.  Upgraded Jaunty and eventually re-installed Jaunty (32 bit version) from the live CD.  Windows XP was on 2 separate physical hard drives, Jaunty was on a separate drive (3 drives, total).

Well, now I can boot to Jaunty just fine, but the one hard drive needed to boot XP will not even mount.

I disconnected all the drives except the XP boot drive.  I've used rescuecd, the Jaunty live cd, and supergrub cd.

Everything I try gives a message like "invalid partition table".

If I open a terminal window and type "mount -t ntfs /dev/sda1 /mnt/mydir"

I get a few lines saying the file system cannot be recognized.

I tried ntfs-3g and got the same thing.

Is the "invalid partition table" the official seal of doom?  Should I give up and just re-install XP, or is there something that can be done?

If nothing else, I would like to copy everything on the drive to an external USB drive.

Any and all suggestions would be greatly appreciated.

---

### Post by lemming465 on 2009-07-04
If you have exact records of the original partition table, you could delete all of the partitions and recreate them in the same places using something like *fdisk*.  This only redoes the partition table, not the filesystem data, which is what makes it work.

Otherwise, it's probably easiest to give up and re-install.

> I would like to copy everything on the drive to an external USB drive.
You can clone the raw data with a command like```
sudo dd if=/dev/sda of=/mount/usb/damaged_disk_image bs=64k
```

Getting the data back might require using forensic tools such as *autopsy*.

---

### Post by Herman on 2009-07-04
[LEFT]TestDisk is a great program for fixing partition tables.
TestDisk can scan the hard disk for file system blocks and then it will let the user know what it found so the user can decide what to write to the partition table.

TestDisk has excellent documentation at its own website, and here's a link to a web page that shows illustrated examples of how to use TestDisk, [TestDisk Page]("http://members.iinet.net.au/%7Eherman546/p21.html").
[/LEFT]

---

### Post by raymondvillain on 2009-07-11
Thank you Herman!

Testdisk is great!

I installed it on the hardrive with my Jaunty installation, then:

sudo testdisk

and everything is fine!  What a great program.  I wish I had known about it a long time ago.

Hard to believe how easy it was to use.  It searched my damaged NTFS drive and found the backup copy of the partition table, then asked me if I wanted to copy it to the location of the existing table, and all I had to do was click on the response.  Windows XP booted up normally and nothing was damaged.  Thank you thank you thank you.

The computer repair people wanted gobs of money just to "scan" my hard drive.  If I'd had them fix it the cost would have been even higher.

They probably use testdisk themselves.

I'm going to mark this SOLVED!

---

### Post by Herman on 2009-07-11
:cool: Cool! It's always nice to hear back from someone who's had a successful outcome, well done and thanks for taking the time to report your problem as solved. 

The testdisk developers are great!

Regards, Herman :)

---

