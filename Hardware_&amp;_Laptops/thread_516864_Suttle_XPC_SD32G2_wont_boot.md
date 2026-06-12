---
title: "Suttle XPC SD32G2 wont boot"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by bjb.butler on 2007-08-03
I did some searching and i found someone that had almost the EXACT same hardware and problems as me , but im trying to install feisty:

"A short description / interpretation of the bug :
My linux kernel 2.6.10 (default kernel of Ubuntu 6.10) stop itself during boot on the following message :
Waiting for root file system...
3 min later, i've got a BusyBox with a minimalist shell (the rescue shell of me init ram-drive), the root partition isn't mounted...
I use GRUB v 0.97-11-ubuntu14 (Ubuntu deb package)

Hardware used when this bug occurs :
Shuttle SD32G2
Intel Core Duo, SATA 2 250 GiB hdd...

Software installed when this bug occurs :
A freshly installed Ubuntu 6.10 Offical release.

Procedure that makes the bug appears :
My Shuttle initially have an empty hdd (no Windows, no existing partition...).
I put the live/install CD of the official release of Ubuntu 6.10. The CD boots well. I follow normal installation procedure (in graphics mode, with ubiquity), I create an msdos type of partition table, and an approx 16GiB ext3 primary partition (denoted /dev/sda1, this is my root partition), next an extended partition filling all the rest of my 250 GB hdd. In this extended partition, I make a swap partition (2 GiB) at the beginning of the free space (sda5). I make an another partition (16 GiB, reiserfs, sda6) for some data.
Ubiquity install my Ubuntu in sda1, setting up sda5 for swap, and mount sda6 in /media/sda6...
No errors during install.
At the end, I reboot, GRUB say (approxiamatively) "Press ESC to see the menu", and next it load automatically the Ubuntu's default kernel.
The system hangs just after the following message :
"Waiting for root file system..."
The computer isn't frozzen, but the kernel waits...3 minutes ! And next this lap of time, the initrd launch a BusyBox minimalist shell.
ls -al /root
shows that this is an emply folder.
mount
show that only /proc, /sys and /dev are mounted."

[http://savannah.gnu.org/bugs/?19070](http://savannah.gnu.org/bugs/?19070)

I have no idea what to do to get this problem fixed, and if it is possible to get ubuntu installed seccessfully

---

### Post by Syke on 2007-08-03
I think you need to flash the bios.

[http://hq1.shuttle.com/services_download03.jsp?PCI=19&PI=247](http://hq1.shuttle.com/services_download03.jsp?PCI=19&PI=247)

"2.Fixed can't install Linux with Dual Core CPU."

---

### Post by bjb.butler on 2007-08-03
ok thanks. which update should i use?

---

### Post by Syke on 2007-08-04
The latest is probably best, SD32S30E.

---

### Post by bjb.butler on 2007-08-04
ok i got feisty installed, all thats left is the nvidia drivers. 

i have an nvidia EN8500GT video card.  i tried installing the nvidia drivers that are in automatix, but they didnt work, it crashed my X server. does anyone know which drivers i should be using?

thanks, bj

---

### Post by Syke on 2007-08-04
Install and run Envy to install the best drivers.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Obituaryfreak on 2007-08-06
Hi All
I have a SS30V10shuttle XPC 
and tried to install Ubuntu Version 5.10 on it while installing itself it prompted me to partition the system but there wasnt anything detected 
and it couldnt go any furthur altough I could run the Live version on the system.
I`m quite confused!!!!!:confused:

---

### Post by Syke on 2007-08-06
I'm not familiar with that model, but I would suggest getting Ubuntu 7.04 and trying that out. There's much better hardware support in the newer versions of Ubuntu.

---

