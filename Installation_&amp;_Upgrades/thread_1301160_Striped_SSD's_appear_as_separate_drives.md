---
title: "Striped SSD's appear as separate drives"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by wwynn on 2009-10-25
MB: ASUS M4A79T deluxe
CPU: AMD Phenom X4 3.4 GHz
RAM: 8 GB (4x2GB) Corsair Dominator DDR3-1600
Storage: 2 Corsair Indilinx 64 GB SSD's striped (RAID 0) with the onboard controller
Video: ASUS EN8500GT (NVidia, and not new). Not using Crossfire; bought this board for the extra PCI-E slots.

Both the 64-bit DVD and 32-bit CD versions of Ubuntu will run in trial mode. In both, GParted shows shows the Corsair drives separately, 59.62 GB each, not in their logical 128-GB single-drive mode. This is the main problem right now.

I have also tried other options with the 64-bit DVD:
- "Test memory" gives a blank screen with flashing underscore top left. Hard reset required.
- "Install Ubuntu" shows "failure to load ....", about five lines worth, flashing by too quickly to gather the rest. Then a screen of BIOS error messages used to appear starting with "Fimware Bug powernow-k8".... There was a reference to ACPI_PSS, that Ubuntu could not talk with it. Also to complain to the BIOS vendor. Now, those messages do not appear and the install process continues as expected. The jproblem remains, however, that the RAID 0 array is not recognized.

My guess is that I should have bought a Gigabyte or MSI MB. :-) I am open to changing it if I know another board will really work. Looking to build a workstation with much use of virtualization.

Any suggestions to make this board work?

---

### Post by urugTON on 2009-10-25
Take a look at [http://ubuntuforums.org/showthread.php?t=1146773](http://ubuntuforums.org/showthread.php?t=1146773).  See what BIACS has to say.  

BTW, I found that with a google of "raid 0 ubuntu 9.04".

Hopefully BIACS' write up applies to you.  From my limited experience with Raid 0, I believe that it nearly applies to your situation.  BIACS assumes that you don't have any data in the RAID0 that you want to keep (see "Go to format the partition and hit Enter.").  If you have data that you want to save, his write up is not the way to accomplish your goal.

---

### Post by wwynn on 2009-10-25
Thanks, urugTON, but that info appears to be software RAID. I want hardware RAID. No need to waste CPU clicks on RAID when the hardware's firmware will do it.

I will keep looking, but thanks anyway.

---

### Post by wwynn on 2009-10-26
There is an alternate install process that uses an alternate install CD. 
Downloaded, now installing. RAID is a question that comes up.

The install process is continuing even though the first screen flashed a bunch of errors very briefly.

---

