---
title: "Installing on a RAID0 partition.  Is it possible?"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by fogNL on 2009-09-14
I'm not sure if this is even possible with linux or not, but I thought I would throw this question out there.

I have two Western Digital Caviar Black 640GB hard drives plugged into an EVGA X58 motherboard.

I have two RAID0 volumes created that take the first 320GB of each drive for Volume0 and the second 320GB of each drive for Volume1. So, each volume is showing 640GB but they span both disks.

On Volume0 i have Windows 7 64-bit installed with no troubles at all, everything working as it should.

I downloaded the Ubuntu Alternate install cd for 64bit and ran that.  Before the partitioning section, it gave me the "One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices? ", to which I said yes to.  I went ahead and completed the partitioning structure assigning my / and swap partitions on the Volume1.  It detected my Windows install without issue as well.  The rest of the install seemed to go smoothly without any issue, up until the very end where it installs grub.  It gets as far as "detecting Windows install" then it pops up the installer menu where i can choose different installation steps, so I once again tell it to install Grub, and it keeps going in this loop.  

Spawning a shell, i got and look at /target/boot/grub/ and the directory is empty, so it looks like Grub won't install.

Is what i'm doing impossible?  I was thinking that maybe the raid driver wasn't available for linux or something, but it seemed to detect everything during install.  Perhaps Grub can't write to the boot sector?  Maybe I just don't understand how raid drivers work.  Would I have to assign a small partition outside the Raid volumes for booting?

Any suggestions?

---

### Post by fogNL on 2009-09-14
I read somewhere today that creating a small, 150MB RAID1 partition at the begining of the drive may help.  Would this apply to my situation?

---

### Post by scrooge_74 on 2009-09-14
Trying to help here since I have 0 experience with RAID but this is the way to learn ;)

I just found [this]("http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html") and at some point it says grub needs to go in all the drives does this make sense to you?

---

### Post by fogNL on 2009-09-15
Wow, I can't believe its this complicated to install linux on here.  Maybe I can find some third party bootloader that will be able to boot linux instead of grub.

---

### Post by scrooge_74 on 2009-09-15
There is Lilo for boot loading but I havent used that either

---

