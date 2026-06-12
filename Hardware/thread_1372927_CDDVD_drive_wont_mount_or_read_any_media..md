---
title: "CD/DVD drive wont mount or read any media."
date: 2010-01-05
forum: Hardware
---

### Post by Decommissioner on 2010-01-05
Hello all, I looked through some other threads on the matter and I didn't see any answers, so hopefully there will be one for my problem.

Basically, my cd/dvd drive wont mount. My computer doesn't seem to read it at all. No matter what media, be it a game, audio disk, data disk. Thing is it used to mount just fine, I even installed some windows games in wine no problem. I am running 9.04, I am not sure exactly what cd/dvd drive I have, but if it helps my computer is a gateway gt4010 and I still use the default drive that came with it. 

I have tried mount /media/cdrom0 to no avail.

---

### Post by 1branchonthevine on 2010-01-05
try

[http://ubuntuforums.org/showthread.php?t=469019](http://ubuntuforums.org/showthread.php?t=469019)

 or 

[http://ubuntuforums.org/showthread.php?t=820933](http://ubuntuforums.org/showthread.php?t=820933)

---

### Post by Decommissioner on 2010-01-06
How do I fstab?

---

### Post by Decommissioner on 2010-01-07
Ok here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=618a7f2c-7961-4a51-81a4-3e90a10c91ea /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0
```I made sure to change udf,iso9660 to auto, and it still didn't work for me.

---

### Post by Decommissioner on 2010-01-08
I have checked out some other threads suggestions, still to no avail. I really hope there is a solution to this.

---

### Post by kwstas on 2010-01-17
i had the same problem on my acer 4810t or at least i thought it was a problem!
i could load a dvd from boot but couldn't load/mount if i had ejected that first one.
the reason of this was because i was trying to eject by pressing the laptop's button!!!
i just had to eject by right clicking on the drive icon and then choose "eject"!

i am really grateful to ubuntu-greek support team who took me out of my misery at last!

---

### Post by Decommissioner on 2010-01-18
I've tried ejecting from the terminal, and manually with the button. Neither does a bit of good.

I don't think it even attempts to read the media. I know it isn't a hardware problem because dvds and cds still work under my windows partition.

---

