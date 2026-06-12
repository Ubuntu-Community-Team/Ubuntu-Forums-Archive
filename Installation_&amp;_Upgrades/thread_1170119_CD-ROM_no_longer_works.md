---
title: "CD-ROM no longer works"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by why on 2009-05-25
I upgraded my system to 9.04 from 8.10, now I can no longer use my CD-ROM

I don't have the device "sr0" or any symlinks (cdrom, dvd, scd0, etc) in /dev. either
udev rule "70-persistent-cd.rule" will not auto re-generate on boot
"lshw" & "hwinfo" do not think I have a CD-ROM at all

What do I have to re-install to fix this?

Thanks

---

### Post by why on 2009-05-30
CD-ROM does come up sometimes on re-boot:D. Not sure but could be related to the number of times the message "ata3: COMRESET failed (errno=-32)" comes up during re-boot (had to fix this problem in the last version using "irqpoll rootdelay=120" at the end of the 2.6.27-11 kernel line in Grub, which I did not have to do with the upgraded Kernel 2.6.28-11 - see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637)).

---

