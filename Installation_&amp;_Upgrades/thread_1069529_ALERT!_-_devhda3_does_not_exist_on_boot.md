---
title: "ALERT! - /dev/hda3 does not exist on boot"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Cyanaether22 on 2009-02-14
Hey, just installed Xubuntu 7.10 with the alternate cd on my iMac G3. The installation went smoothly, no problems.

When booting, it goes to the xubuntu loading screen for a second but doesn't load at all, it freezes there for a while and then shows a shell saying "ALERT! /dev/hda3 does not exist, exitting to a shell.." or something similar.

What's going on there? I can't get past this.

thanks! :)

---

### Post by x33a on 2009-02-14
load your live cd and then open a terminal. 

then type, sudo fdisk -l, and post its output here.

---

### Post by Cyanaether22 on 2009-02-20
Alright, I had to run a shell on /dev/hda3 in rescue mode in order to make the sudo command work. Here are the results:

```

/dev/hda
#           type                name     length     base     size     system
/dev/hda1   Apple_partition_map Apple    63   @     1        (31.5k)  Partition map
/dev/hda2   Apple_Bootstrap     untitled 1954 @     64       (977.0k) NewWorld bootblock
/dev/hda3   Apple_UNIX_SVR2     untitled 12695313 @ 2018     (6.1G)   Linux native
/dev/hda4   Apple_UNIX_SVR2     swap     681979 @   12697331 (333.0M) Linux swap

Block size = 512, Number of Blocks = 13379310,
DeviceType = 0x0, DeviceID = 0x0

```

somehow that doesn't look good to me. But this is what I get everytime I do a fresh install, replacing all existing partitions on the HD.

---

### Post by Cyanaether22 on 2009-02-23
bump - i really need to get this working. please help! :)

---

### Post by Cyanaether22 on 2009-03-15
After a while of success with debian which ended with X deciding not to start, I'm going to try xubunt 8.10 again.

Just in case this error might happen again, does anyone have any advice about this?

---

