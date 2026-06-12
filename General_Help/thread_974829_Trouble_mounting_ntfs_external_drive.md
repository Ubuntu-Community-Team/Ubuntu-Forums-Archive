---
title: "Trouble mounting ntfs external drive"
date: 2008-11-07
forum: General Help
---

### Post by NathanDC on 2008-11-07
I am trying to mount a 1TB NTFS USB Seagate Freeagent external drive. I have tried multiple ntfs-3g commands but none of them have found what it needs to mount. My laptop  one has only one internal drive.

How do you linux gurus go about mounting these things? I have my drive set to read only in ubuntu config.

Thanks. :popcorn:

---

### Post by zero777zero on 2008-11-07
hi nathan, i've got two 750gb ntfs seagates that look like this

[IMG]http://ai.pricegrabber.com/pi/3/26/73/32673088_125.jpg[/IMG]

since they don't have a proper on off switch (they have a touch sensor) i literally need to unplug the power chord from the drive and plug it back in for ubuntu to recognize the drive. the touch sensor lets me turn it off though lol. annoying, but i hear mac users have the same issue with these...

---

### Post by WWSmith36 on 2008-11-07
With the drive plugged in please give the output of 

sudo fdisk -lu

Thanks

---

### Post by NathanDC on 2008-11-08
LOL...They are a pain but nice drives:)

That fdisk command is very cool! 

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS

---

### Post by NathanDC on 2008-11-08
ok I'm kicking myself. Found my answer here. Thanks guys. :)

[http://ubuntuforums.org/showthread.php?p=6129412#post6129412](http://ubuntuforums.org/showthread.php?p=6129412#post6129412)

---

