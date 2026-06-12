---
title: "RAID Partition Error during install"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by gemini420 on 2009-01-27
I am running Ubuntu 8.10 Server Install.

I have two 120 GB disks and an Intel RAID controller.

I am configuring RAID 0.

When the Intel RAID controller is active, I can install Ubuntu just fine.  BUT I do see I/O errors on start up.

> attempt to access beyond end of device
sda: rw=0, want=462832448, limit=234441648
Buffer I/O error on device sda1, logical block 462832384
attempt to access beyond end of device
sda: rw=0, want=462832449, limit=234441648
Buffer I/O error on device sda1, logical block 462832385
attempt to access beyond end of device

The system seems to run OK, but who knows what issues are waiting down the road with 'access beyond end of device' disk IO errors.

Figuring that my Intel RAID controller is not well supported, I decided to try software raid.

Configuring software raid causes issues during install -> partitioning stage.

After I partition each drive and create the RAID device on /dev/md0, the installer says 'kernel could not re-read partition tables ... you must reboot before accessing /dev/md0'

I have tried rebooting (mid install) right after partitioning. This did not work.

I have tried ignoring this warning and the system continues to install, but will not boot. I just get a blinking cursor at bootup that seems to be when BIOS tries to load the bootloader.

Interestingly, if I run the 8.10 installer in 'repair mode' and access a shell on /dev/md0 I can see a file system.

So something seems to be wrong with GRUB in my scenario. Or the software RAID 0 device isn't bootable?

The repair option 'Reinstall GRUB' fails.

Any ideas? Pretty please!

Shane

---

### Post by gemini420 on 2009-01-27
I have been searching all over for a resolution to this issue.

I have found one reference to a discussion stating Software RAID0 can not be a bootable drive??

Can anyone with working knowledge of RAID0 confirm that this is true?

---

