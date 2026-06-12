---
title: "remove Ubuntu from Samsung NC10"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by roy20 on 2009-10-21
Hello All,

Going back to the original Samsung NC10 MBR doesn't seem to be easily possible. My NC10 is currently dual boot with Ubuntu and XP. I need to put things back as I have to return the computer for service and I want as little aggro from the engineers as possible. 

The NC10's Recovery Partition *go back to the first stored configuration* will overwrite drive C: but will *not* replace the MBR. I've tried this and it doesn't in my case at least.

Why would I want to? Well I'd like to get rid of the Linux Grub boot-loader - I can easily remove the linux partitions with tools like Partition Manager. OK the XP re-install CD will put back XP as the sole op system but things like the F4 boot recovery would then get wiped out I think as it resides on a Vista op system hidden partition all of its own.

One idea I did have was to use something like Partition Manager (it's often free as a cover mount on PC mags in the UK) - that has a restore MBR option, but it would again be the default XP one I think. To do this a bootable USB memory device could be created with nLite.

Any suggestions?
Roy

---

### Post by stlsaint on 2009-10-21
so you said vista and xp...which OS is the one that came with the system? 
for total wipe i suggest just doing a recovery on the entire system...this will without a d doubt remove grub...but if not than choose which os you want to be the bootloader and install it to mbr manually.

maybe im missing something...if so please explain again.

---

