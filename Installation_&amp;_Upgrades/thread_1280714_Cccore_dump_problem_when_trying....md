---
title: "Cccore dump problem when trying..."
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by maverik35 on 2009-10-02
Good morning..I'd like some help for my problem.
Scenario: Dell Laptop (Centrino 1.6ghz,160 HD, 1.5 Gb ram), WinXP on hda0,0 (hda1), Ubuntu 9.04 on hda0,4 (hda5), BT4 (Ubuntu 8.10 based) on hd0,6 (hda7), Swap hda0,5 (hda6)...I use the same swap partition for both Ubuntu Jaunty and BT4 (Ubuntu 8.10)...
In my menu.lst after installing BT4, never shows up anything regarding BT4..
I had to add it manually, but when booting up, only shows Ubuntu 9.04    and WinXP (other op. systems)...
I tried booting up with Ubuntu 9.04 live cd...opened up grub console (sudo grub) and tried to boot the BT4 from grub console, all I get is "segmentation fault (core dump)"...
This is what I do after booting up from Ubuntu 9.04 Live CD:
  $sudo grub
  $root (hd0,6)  (BT4 partition)
  $kernel /boot/vmlinuz-2.6.28.11-4gb root=/dev/hda7
  "segmentation fault (core dump)"....
Tried this too:
  $$sudo grub
  $root (hd0,6)  (BT4 partition)
  $kernel /boot/vmlinuz-2.6.28.11-4gb root=UUID=xxxxxxxxxxxxxx ro 
  "segmentation fault (core dump)"....
I've read about the grub, and nothing seems to fix this problem...
Any idea?
I tried this because after installing BT4, if I enable the option "Write to bootloader", it installs it, but It does not boot, it throws error 17 at the grub...I had to use Super Grub Disk to   fix it and boot from Jaunty again..The thing here is that the menu.lst from Jaunty does not show anything about the BT4 in "Other Operating Systems" option but Windows XP.....So I tried without writting to bootloader, and It boots from Jaunty but in bootmenu does not appear the BT4, only Jaunty and XP..
But partition (BT4) is there, I even mounted it and checked the menu.lst..And it is there..
Tha is why I tried to run it from grub console...
There, is when I get the fragmentation Fault message as described above..
Please, anyone's help will be very appreciated...

---

