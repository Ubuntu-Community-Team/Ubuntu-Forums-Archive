---
title: "Installation from HDD fails"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by Rumtscho on 2009-04-09
I have to set up an old PC (PII, 256 RAM). It has to have a Geman user interface and a wireless Internet connection. 
I wanted to install Xubuntu 8.10 the usual way, but discovered that the PC has a faulty IDE controller, and no CD can be read beyond the first 150 MB. The only OS I was able to install from CD was Puppy, Xubuntu spits Buffer I/O errors. But Puppy is available in English only. 

The PC can`t boot from USB, and it isn`t part of a LAN. I don`t have any other PC with a floppy device, so a bootable floppy is out of question. So I decided to use Puppy to make an installation from the HDD, like in [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux). Idecided to use Procedure 1. 
I formatted the HDD with 1.5 GB swap, 500 Mb ext2 for Puppy, 800 Mb ext2 for the installer, and all that remained went into the future Xubuntu partition, ext3. Then I installed Puppy to its partition, including GRUB. Got a Hardy alternate iso (newer versions have a bug, cannot be installed from HDD), and copied it together with the vmlinuz and the initrd on the installer partition. Then booted from the installer. 

Everything seemed well until the partitioner started. I selected manual config, assigned / to my big ext3 partition and selected next. The installer complained that it cannot remove system files from the selected partition - which struck me as very odd, as I thought that it should be trying to write system files to that partition instead of removing them. So I thought I`d give the guided partition a try, but only got the choice of entire hard disk or entire harddisk with LVM. I selected the first, and the thing was of course dumb enough to wipe the partition on which the iso itself was. So I have an empty HDD again. 

Does anybody know how to get the thing working? No matter if it is the HDD way, some other way to install, or another distro (as long as it is in German and can be configured to work with WPA).

I think I should try the "Alternate CD alternate method" described on the page linked above, but the explanation is so short, I can`t understand if I should boot the installer from its temporary location or from its future partition?

---

### Post by Rumtscho on 2009-04-09
Ok it seems I have encountered the bug described here: 
[https://bugs.launchpad.net/ubuntu/hardy/+source/partman-target/+bug/186711](https://bugs.launchpad.net/ubuntu/hardy/+source/partman-target/+bug/186711) 
As far i understand the workarounds, I have to unmount all partitions beside Swap and / (correct me if this is wrong). 
Now, how do I unmount the Puppy partition while installing? The installer detects the harddrives automatically.

---

### Post by Rumtscho on 2009-04-09
Well, it is moot now. 

After trying out the most ridiculous setups, I realized the value of my time spent on it is higher than the price my friend paid for the thing in the first place. So I just hooked the HDD to my PC, installed Xubuntu the normal way, and returned the HDD. It worked. Basta!

---

