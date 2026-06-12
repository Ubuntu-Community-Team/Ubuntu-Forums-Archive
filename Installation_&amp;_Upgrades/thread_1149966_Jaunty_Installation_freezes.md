---
title: "Jaunty Installation freezes"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by sanyaldibya on 2009-05-05
I tried to install Jaunty on my laptop. I have windows vista on 1st partition (120 GB). 2nd partition is /boot for intrepid. Rest of the partitions till /dev/sda12 is used by intrepid. I picked up general installation CD for 9.04 for AMD 64 (my laptop is AMD 64) and started installation.
I have Easy BCD configured to boot windows and intrepid. grub for intrepid is written in the boot sector of /boot (which is /dev/sda2).
My plan:
Keep intrepid intact (taking no chance with my nicely installed intrepid)
Install jaunty in a separate single partition (/dev/sda13)
Write the grub for jaunty in the boot sector of /dev/sda13
Use EasyBCD to load windows/intrepid/jaunty
 
I used manual partitioning and created /dev/sda13 using EXT4 (wanted to check how ext4 fairs).
 
Installation went fine till configuring target system, connecting to online rep over internet to get security updates, setting the hardware time from time server et al. I think it's around 90% completion that the issue happens. It shows nothing but the splash screen for installation; no other prompt/notification - just the screen - and keeps frozen there. My system is all quiet; nothing accessing the CD anymore, no activity in the hard drive as well. I tried the volume controls on my system and the volume control shows up on the screen and works fine). Alt+Ctl+F6 takes me to terminal with a valid prompt.
I waited for 30 mins. At this point I hard booted the system. I added an entry in EasyBCD hoping the jaunty installation went fine. But the system does not boot into jaunty.
 
Can anyone help?

---

