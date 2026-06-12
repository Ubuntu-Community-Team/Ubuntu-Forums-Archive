---
title: "Help! Cannot install Ubuntu"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by pentag on 2009-09-10
I've been having a huge number of problems trying to get ubuntu installed on my PC.

I have windows 7 RC installed in one partition a (NTFS) data partition, and want to install ubuntu 64-bit on a third partition of my 1.5 TB HDD.

I first tried using the latest version of Ubuntu. Booting via the CD allowed me to go through the first few install screens, until it 'could not detect common CD-ROM drive' (or something similar). A bit of searching found a few people had similar problems, but the various proposed solutions I saw didn't seem to work.

I then tried booting from USB, which again started fine untill in mid installation I got an error about how the BIOS delivered something, and the install failed.

I read someone had had similar difficulties with 9.04 and 8.10 but was OK with 8.04, so I tried the 8.04 cd. This time the install generally went OK except at 94% grub-install failed. Searching showed several people had had this problem, but simply choosing a different partition didn't seem to solve the problem for me. Installing without a boot loader went through fine. I tried separately installing grub after booting again from the live CD (chroot into the installed but unbootable ubuntu and the use apt-get install) but for some reason apt-get install grub failed.

I have only basic linux familiarity, and am now unsure of what the problem is, or where to go. I don't want to continue to downloafd different versions because I have a download limit and I've already downloaded 1.5GB in two different distributions (I still have both).

One reason I think there could be problems potentially is that bth my harddrive and cdrom are sata ii devices, and as such appear as the master on ide channels 1 and 2 of my motherboard - channel 0 is empty.

Does anyone have any ideas as to how I can get either of these versions to install correctly? I currently have a valid (I think) install of 8.04 but without grub.

My specs are:
AMD phenom ii x3 cpu
4gb ddr2
1.5tb sata ii hdd
sata ii dvd multi odd
gigabyte ma785gm-us2h mobo

---

### Post by running_rabbit07 on 2009-09-11
> **pentag said:**
> I've been having a huge number of problems trying to get ubuntu installed on my PC.

I have windows 7 RC installed in one partition a (NTFS) data partition, and want to install ubuntu 64-bit on a third partition of my 1.5 TB HDD.

I first tried using the latest version of Ubuntu. Booting via the CD allowed me to go through the first few install screens, until it 'could not detect common CD-ROM drive' (or something similar). A bit of searching found a few people had similar problems, but the various proposed solutions I saw didn't seem to work.

I then tried booting from USB, which again started fine untill in mid installation I got an error about how the BIOS delivered something, and the install failed.

I read someone had had similar difficulties with 9.04 and 8.10 but was OK with 8.04, so I tried the 8.04 cd. This time the install generally went OK except at 94% grub-install failed. Searching showed several people had had this problem, but simply choosing a different partition didn't seem to solve the problem for me. Installing without a boot loader went through fine. I tried separately installing grub after booting again from the live CD (chroot into the installed but unbootable ubuntu and the use apt-get install) but for some reason apt-get install grub failed.

I have only basic linux familiarity, and am now unsure of what the problem is, or where to go. I don't want to continue to downloafd different versions because I have a download limit and I've already downloaded 1.5GB in two different distributions (I still have both).

One reason I think there could be problems potentially is that bth my harddrive and cdrom are sata ii devices, and as such appear as the master on ide channels 1 and 2 of my motherboard - channel 0 is empty.

Does anyone have any ideas as to how I can get either of these versions to install correctly? I currently have a valid (I think) install of 8.04 but without grub.

My specs are:
AMD phenom ii x3 cpu
4gb ddr2
1.5tb sata ii hdd
sata ii dvd multi odd
gigabyte ma785gm-us2h mobo

Installing Grub should be pretty easy. You will need the liveCD to boot up and use a terminal to give some commands. Go to this [thread]("http://ubuntuforums.org/showthread.php?t=224351") and follow the directions for a happy system.

---

