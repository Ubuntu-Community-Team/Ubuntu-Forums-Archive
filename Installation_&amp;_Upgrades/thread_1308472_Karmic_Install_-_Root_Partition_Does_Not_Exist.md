---
title: "Karmic Install - Root Partition Does Not Exist"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by maxol on 2009-10-31
I have run a clean install of Karmic 64 onto my multi boot system with RAID1 mirroring two identical SATA hard disks.

The partitioner recognises the RAID array during the Karmic install dialog and I have four partitions set up like this.

> /dev/mapper/pdc_iaedgi1 fat32 ( windows partition )
/dev/mapper/pdc_iaedgi2 ext4 ( root partition )
/dev/mapper/pdc_iaedgi3 linux-swap ( swap partition )
/dev/mapper/pdc_iaedgi4 ext4 ( home partition )

After running my Karmic install without any errors when the computer restarts I am dropped back to the BusyBox terminal with the error> ALERT! /dev/mapper/pdc_iaedgi2 does not exist. Dropping to a shell!

When I boot up the Karmic Live CD /dev/mapper/pdc_iaedgi2 is present with the root file system intact.

I really don't understand why this refuses to work. Does anybody have any ideas?

---

### Post by maxol on 2009-11-01
bump

---

### Post by maxol on 2009-11-01
OK dmraid is broken in Karmic.

It will let you set up your raid array with the installer on the CD but then fails to properly install dmraid so that when you try to boot from your raid array you can't.

The solution that worked for me is when Karmic has finished installing, before you restart to boot from your hard disks is to chroot into your new karmic install and run.> apt-get purge dmraid
followed by> apt-get install dmraid
Then reboot and RAID should work.

---

### Post by jonah1980 on 2009-11-17
i have the same problem, i can install ok then on reboot i get stuck at initramfs with this error:
> 
ALERT! /dev/mapper/nvidia_dcfadeef2 does not exist. Dropping to a shell! 

I tried to follow guides to chroot in from a livecd but failed miserably, can anyone please help me out. thanks.

---

### Post by huuan on 2009-11-18
see here about grub which may have some bearing on your problem, comment around #14,#15,#16 :
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340)

I had all kinds of grief trying to install RAID 1 using 9.10 server 64 bit, GRUB installed one time for me but never again, could not reproduce the good install and I have now ended up using LILO which installs and reboots to the RAID1 just fine.
FWIW I tried on 3 different 64 bit mobos same result, always stuck at grub install but on all 3 LILO installed and rebooted just fine.
YMMV.

---

