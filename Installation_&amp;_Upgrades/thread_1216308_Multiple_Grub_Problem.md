---
title: "Multiple Grub Problem"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Kazade on 2009-07-18
This is going to take some explaining.. so bear with me :)

I used to have a single hard disk which had both a Windows and Ubuntu install. Using Grub as the bootloader. 

Then I bought 2 brand new shiny disks and set them up as software RAID 1, I installed Ubuntu on them and Ubuntu boots super fast. I left the original disk along side them, now I have this situation:

/dev/sda - First RAID1 disk with Ubuntu installed and bootloader
/dev/sdb - Second RAID1 disk, a mirror of the first
/dev/sdc - Original disk with Windows and old Ubuntu install, with GRUB

Now the problem is, I want to boot the Windows install on the 3rd disk.. but I don't know how to.. GRUB hasn't picked it up, I guess because it's not got a Windows MBR but another GRUB one. Any easy way out of this?

---

