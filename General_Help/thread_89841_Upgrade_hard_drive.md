---
title: "Upgrade hard drive"
date: 2005-11-13
forum: General Help
---

### Post by apps4apps on 2005-11-13
Hi All, 

I'm trying to replace a 30GB drive with Ubuntu installed with a 120GB drive for more space but I seem to be having a few problems. I originally set the 30GB drive up by selecting to delete the disk and setup using LVM. 

I have tried using Ghost and a couple other utilities to clone the drive but I either mess up Grub's settings and/or end up with unrecognized partitions. 

The closest I have come so far (the setup that I am currently typing this message from...) was to setup Ubuntu on the new 120GB drive using the same method (delete and use LVM). After Ubuntu installed and rebooted once, I reset the PC and used Ghost to copy the second partition only. 

The current result is that the system boots up ok and I can access everything **but**... the system still shows the same amount of disk space free as when I was using the 30GB drive. 

In an attempt to try and fix this I loaded the "Disks Manager" in the System menu but I'm not sure what to do to fix the situation. 2 Hard disks are showing for some reason. The first one says 114.50GiB and shows 2 partitions. The first partition looks ok (Partition1 /dev/hda1  /boot  243.14MiB  204.39MiB free) but the second one shows Partition5 /dev/hda5  Access Path: none  114.50 GiB free space not available  Status: inaccessible

The other hard disk showing in the list shows the following partitions:
Partition ntu-root  /dev/mapper/Ubuntu-root  Access Path: /  Size: free space not available Status: inaccessible

Partition Swap Partition /dev/mapper/Ubuntu-swap_1  Filesystem: Memory Swap  Size: free space not available

I also tried loading GParted but I get a message saying that the kernel is unable to re-read the partition tables on the following devices: -/dev/mapper/Ubuntu-root  Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access. 

**Could someone please guide me in the right direction here?** I'd reall, reall, really, hate to have to reinstall and have to update and install all additional programs all over again... 

I do still have the original 30GB disk here also. If there is an easier way to transfer the system from one disk to the other to gain additional space I'd be interested in going that route if it's any easier than fixing my current mess.

---

### Post by dosed150 on 2005-11-13
couldnt you just slave the new hdd drive to the other then you wouldnt have to copy anything

---

### Post by apps4apps on 2005-11-13
Thanks for the reply :smile: . Unfortunately that's not practical in this case. The 30GB drive needs to be used elsewhere and I would prefer to only have one HD running in this setup.

---

### Post by dosed150 on 2005-11-13
oh rite then im not sure what you should do

---

### Post by apps4apps on 2005-11-13
Well, I'm still trying but I thought I'd try something a bit different. I decided to clone the drive again but this time I used g4l. Disks manager still shows 2 disks with similar info but this time the unpartitioned area is displayed. 

Partition5 - /dev/hda5  Filesystem: Unformatted  Access Path: none  Size: 28.40 GiB (free space not available)  System: Inaccessible

Free Space - Free Space, not formatted  Size: 85.86 GiB (free space not available)

The other drive listed shows Partition ntu-root and Swap partition as before. 

Does anyone have any suggestions on how I can access and modify the existing partition? I feel like I must be missing something really simple somewhere...

---

