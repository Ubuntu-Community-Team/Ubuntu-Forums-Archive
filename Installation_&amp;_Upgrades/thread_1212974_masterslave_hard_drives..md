---
title: "master/slave hard drives."
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by accessys on 2009-07-14
just did a major upgrade to my computer, have been using linux about 10 years so I have checked all the usual places.

was running SUSE 10.0 on old box and bought
new dual core CPU
new ASUS mother board
new Seagate 1tb hard drive 

loaded ubuntu 9.04 with no major hassles BUT what I have done in the past when I up graded is use the new hard drive as master and the old one as a "Slave" so I have access to all my older data (yes the critical stuff is backed up on a removeable hard drive that can be accessed) but there is a lot of "Stuff"  that would be usefull to just copy over or just get to it if I need it.

in any case the new harddrive is a SATA drive and loads and mounts in the correct location.
the old hard drive is an IDE and it is cabled with a CD drive that is found and works fine (in fact loaded ubuntu from that drive)

normally in the past I would just go into terminal in root and use 
mount /dev/hdb2 /mnt/hdb2  and it would mount fine and access worked 
used sudo to do the same but keep getting "not found" etc.

various Dir and searches etc can't find that hard drive (yes the setting on the back is set for "slave")

and on boot the BIOS does not seem to find it either.

not critical but sure would be convienent if I could access the slave hard drive.


thanks
Bob

---

### Post by unlimitedz on 2009-07-14
Try setting the drive to Cable Select, You may also want to try moving it to the master position and see if that has any effect.  Perhaps your IDE controller is damaged.

---

### Post by accessys on 2009-07-14
> **unlimitedz said:**
> Try setting the drive to Cable Select, You may also want to try moving it to the master position and see if that has any effect.  Perhaps your IDE controller is damaged.


did the reset to master and tried it with the new hard drive unplugged so that is should have booted from the old SUSE OS but it instead booted from the cache somehow into Ubuntu and only showed the memory I had in RAM not showing any hard drives.

???

not sure about the IDE controller, seems to work with the other devices hooked to it.  any way to tell for sure.

not sure how you set the drive to "Cable select" is that another position on the jumper on the back, label is worn away, is 4 positions but only know the master and slave positions.

wonder if there is a way to take it out of the computer, hook it to a USB cable and use it like an external hard drive????  probably not enough power thru the USB cable even if I could get the right adapter.

am considering just putting the old motherboard, harddrive and CPU in an old box powering it up and doing a full copy to an external blank harddrive might be easier.

thanks
Bob

---

### Post by unlimitedz on 2009-07-14
Cable select is a jumper setting, not all drives are the same so it's hard to guess at what the CS position is.    There is no such thing as "caching" when booting, if you took the drive out that has ubuntu, and saw the ubuntu screen when you booted then you probably have the CD in your drive still, or you installed ubuntu to both drives somehow???

As a side note, if your bios isn't seeing the drive, then ubuntu won't see it.  I would suggest setting the drive to master, and putting it on the master position of your IDE cable, and remove the CDROM, then boot up and see if the BIOS sees it.  you could also try putting in on Master moving it to the Secondary controller (if there are 2).

---

