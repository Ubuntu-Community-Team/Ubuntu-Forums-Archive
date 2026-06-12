---
title: "CPU Temperature Shutdown Problem"
date: 2009-07-04
forum: Hardware
---

### Post by vcfger on 2009-07-04
CPU Temperature Shutdow Problem

Hi all,

have a problem to get newest ubuntu version run after installation 
of Jacky Jackalope via wubi under xp on a dell inspiron 5150, 1GB RAM.

Gutsy Gibon live CD runs fine, XP also okay but power shutdown 
while trying to boot Jacky Jackalope.

Any hints appreciated.

Thanx2all

---

### Post by 00b00nt00 on 2009-07-05
From Wiki:

Inspiron 5150
This was the high end version of 5100. It weighs over 7.5 pounds. It was designed for the Mobile Intel Pentium 4 processor upto 3.2Ghz, The hyper-threading features of the CPU were available only if the BIOS firmware supported it, a choice made at time of purchase. It had a Intel 852 PM chipset, and supported a 333Mhz system bus, Max 2Gb PC333 SDRAM, 4x AGP ATI Mobility Radeon 9000/Nvidia Geforce Fx5200 go 32/64mb, 15.4 inch 1400x1050 SXGA widescreen, >40GB Ultra-ATA/100 44 pin IDE ATA/EIDE/ATAPI, 1 IEEE 1394 Firewire, 2 hi-speed USB, 18bit AC97 sigmatel 9750, 1 external VGA, 1 S-video, 1 compact flash slot, mini-PCI slot containing dell true-mobile 802.11b/g 1350, 1 fast ethernet, 1 RJ11,1 optical drive, 6 cell 4400mah battery. The wireless networking was based on a closed broadcom chipset. **This laptop had a huge number of design failures, overheating, battery failures, connector loosening, motherboard failures.**

See if you need any BIOS/Firmware updates from here:

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=&SystemID=INS_PNT_P4_5150&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&ServiceTag=&SystemID=INS_PNT_P4_5150&os=WW1&osl=en&catid=&impid=)

Otherwise, try vacuuming the ventilation slots.

---

### Post by Done_Fishin on 2009-07-05
try running with acpi=off although it seems strange that you should get this problem at this stage 

when booting .. at Grub window 
press escape to stop countdown
press "e" to edit grub
use arrow keys to scroll down lines on screen, add acpi=off as shown below 

> GNU GRUB Version 1.96
[quote]set root=(hd1/1)
searcg --fs-uuid --set 894ec0c8-a9d4-4d76-8bf0-d2f9ef97db3f
linux /boot/vmlinuz-2.6.30-8-generic root=UUID=894ec0c8-a9d4-4d76-8bf0-d2f9ef97db3f ro  quiet splash **[COLOR="Red"]acpi=off[/COLOR]**
initrd /boot/initrd.img-2.6.30-8-generic


Minimum Emacs-like screen editing is supported. TAB lists completions. Press Ctrl-x to boot, Ctrl-c for a command line or esc to return menu

[/quote]

[B][COLOR="Blue"]I am booting from USB so don't make any other changes. The above menu is ONLY for my system, just find that line and add the command.

follow the instructions on screen for any other differences .. this is from Ubunu Karmic 9.10[/COLOR][/B]

---

### Post by brookie on 2009-07-12
If anyone is still checking this I'd like to know if the acpi line helped. I'm running Intrepid on an inspiron 5150 and have had the same fatal shutdown due to heat. WinXp does not do this, so it is Ubuntu, regardless of how much of a lemon this pc is. 

I have installed and configured i8kutils, and gkrellm. Hope it helps. When playing gnubackgammon and listening to Banshee Radio Paradise the thing just crapped out. Dang! 

Oh well, woe for us old pc owners. BTW, Jaunty did not work with the ati drivers on this machine, so I went with Intrepid. 
Cheers, 
brook

---

