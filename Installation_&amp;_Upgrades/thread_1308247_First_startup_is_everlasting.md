---
title: "First startup is everlasting"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by G1imt on 2009-10-31
I just reformatted my HDD into a 200GB ext3 partition and a 50GB ntfs partition. I installed ubuntu 9.10 on the ext3 partition flawlessly using the boot CD. (during the install i set the ext3 partition to mount point /, the ntfs partition to mount point /Windows and my second harddrive to mount point /Storage)

But when i start up my PC, the "loading cursor" sits in the center of the screen, unmoved by my mouse. (I've attached a cellphone picture to illustrate)

This screen lasted for a good 20 minutes (an approximate guess) before the screen goes black (though still turned on). After a further 10-20 minutes the screen turns completely off. All of this in spite of my mouse movements. After this point nothing happens. Although, if i press the computers power button the new white ubuntu icon appears for a few seconds before the computer turns off.

I've rebooted the PC 3 times with identical results. Have i dont something wrong in the installation process or will a simple reinstall help?

(I downloaded the CD, burned at max speed, booted with "try ubuntu first" so that i could format my disks, then selected the install icon on the desktop.)

---

### Post by lemming465 on 2009-11-01
Is that NTFS partition actually formatted?  If not, or if it was reformatted after the ubuntu install, you may be hanging early in the boot process trying to mount filesystems by UUID that aren't there.  We could be more specific if we had the output of```

cat /etc/fstab
sudo fdisk -lu
sudo blkid
```
But you'd probably have to use a live CD and hand-mount your Linux partition somewhere, e.g.```

mount /dev/sda2 /mnt
cat /mnt/etc/fstab

```

If the problem is fstab, you could do```

sudo nano /mnt/etc/fstab
```
from the rescue CD and either add "noauto" to the options, or comment out the problematic partitions temporarily.  For partitions I'm planning on reformatting, I usually revert them to /dev/sdXN format rather than UUID, because the disk position doesn't change when they are reformatted.

---

