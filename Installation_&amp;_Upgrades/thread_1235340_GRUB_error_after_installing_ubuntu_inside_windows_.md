---
title: "GRUB error after installing ubuntu inside windows XP"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by SriLankanBoy on 2009-08-09
I recently got the Ubuntu 9.04 CD from Ubuntu via shipit. I am already using Windows XP SP3. I installed ubuntu using the Install inside windows using the wubi installer within the CD.

After installing, the Ubuntu appears in the boot menu with Windows XP. But when I boot ubuntu, it loads black screen like something called GRUB. This is the problem I face :

> 
GRUB4DOS 0.44 2007-04-20, memory 637k/2045M, menu end : 0x43462 (Minimal BASH-like line editing is supported. For the first word TAB list possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.

grub > 

How can I fix the problem ? :confused:

I can't load the ubuntu GUI :(

Thanks in Advance :)

---

### Post by stlsaint on 2009-08-09
maybe a faulty install...try this and see if works!
[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

---

### Post by amites on 2009-08-09
that is the error I get after I remove all xserver-* files and xorg 

when I restore sources.list to hardy / intrepid I can run through the apt-get install for xorg no issues

wondering if I can go back 1 more step - trick is that takes me to xorg 7.3 from 7.4

I'd stick with Hardy Heron but that removes access to my SATA drive...

would like to stick with Ubuntu on my Desktop beginning to think it may require a hardware upgrade...

---

### Post by amites on 2009-08-26
solution I came up with:

I have 4 HD"s installed

3 through IDE with MB
1 through SATA via PCI adapter

the 3 in the IDE in the BIOS are detected in order
IDE0 Master
IDE0 Slave
IDE1 Master

in Ubuntu
IDE0 Master
IDE1 Master
IDE0 Slave

Thus my solution: Boot into Live CD, open up /boot/grub/device.map with sudo

change the drive order to match BIOS, in my case
from: 
HD0 /sda
HD1 /sdb
HD2 /sdc
HD3 /sdd

to:
HD0 /sda
HD1 /sdc
HD2 /sdb
HD3 /sdd

save, then run
grub --device-map=device.map
  (from inside the directory)
> root (hd2,0)
> setup (hd0)
> quit

reboot and good to go

---

