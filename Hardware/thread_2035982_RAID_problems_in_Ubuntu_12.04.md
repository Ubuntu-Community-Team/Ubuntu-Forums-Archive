---
title: "RAID problems in Ubuntu 12.04"
date: 2012-07-31
forum: Hardware
---

### Post by squadexodus on 2012-07-31
A few days ago, I made the switch from OpenSUSE to Ubuntu, and I haven't regretted the switch aside from one thing. On the OpenSUSE, I had a RAID 5 (Consisting of 3 2TB Hitachi Deskars), which worked fine. Upon migration to Ubuntu and after the first restart, either the computer would freeze upon selection of Ubuntu on the screen, or it goes to a text stating
      "md127 : inactive sdb1[0](s)
           1953512536 blocks super 1.2
         unused devices: <none>"

My friends and I have tried everything we can think of, as the hardware scans had indicated no problems with the hardware. I wiped the raid, and remade it to no avail. 

I assume the freezing on the purple screen has something to do with the ATI onboard graphics I'm using, but it might have something to do with the faulty raid. I haven't even had the opportunity to wrestle and try and get the blasted thing to work properly on the 42" HDTV I want it on.

Can anyone help me at least make sure the sdb1 drive is dead before I order a new one? I'm not completely fluent in linux, so forgive me for perhaps being slow

HTPC Specifications:
Motherboard: ASUS M4A88TD-M/USB3 AM3 AMD 880G SATA 6Gb/s USB 3.0 HDMI Micro ATX AMD Motherboard
CPU: AMD Athlon II X4 640 Propus
RAM: G.SKILL Sniper 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333
Boot Drive: Western Digital Caviar Blue WD5000AAKX 500GB
RAID Drives: HGST Deskstar 5K3000 2TB

---

### Post by squadexodus on 2012-08-03
Just as an update, I've since unplugged the RAID drives, and everything boots fine (aside from the RAID drives)

A full wipe and rebuild has been performed, yet Ubuntu refuses to play nice with the array.

---

