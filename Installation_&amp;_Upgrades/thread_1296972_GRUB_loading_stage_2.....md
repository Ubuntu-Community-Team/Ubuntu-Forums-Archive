---
title: "GRUB loading stage 2...."
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by chufflar on 2009-10-21
This is my first post and i am a a bit of a newbie to ubuntu!
so far i have only really had problems i have overcome most through forum searching but now im really stuck.
 
i attempted to dual boot windows xp and unbuntu 9.04 putting ubuntu on to an extrenal usb hard disk.
 
intially i had GRUB error 21 every time i booted and was forced to use my linux live disk to fix the problem.
 
i ended up installing supergrub which worked and i can now boot into ubuntu without a disk but i still cannot boot into windows.
 
i get to the grub menu and when i select windows it says GRUB loading stage 2....
and then the boot menu reappears.
 
any help will be much appreciated!

---

### Post by bumanie on 2009-10-21
It is likely that you have installed grub to the mbr of the windows (internal) drive. To boot successfully off an external hard drive, in essence, one needs to install grub to the external hard drive and leave the mbr of windows alone. To fix, use an xp installation cd to go into repair/console mode. In console mode type FIXMBR followed by FIXBOOT  windows should boot again. 
Install grub to the external hard drive by booting a live cd and going to terminal and put in the following commands > sudo grub > root (hdx,x) > setup (hdx) > quit replacing the x's with the numbers that equate to your external drive (Likely to be (hd1,0) and then (hd0) if there is only one hard drive in the computer). Alternatively, fix windows mbr as above and then reinstall ubuntu to the external hard drive by following [this]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372").

---

### Post by chufflar on 2009-11-09
I tried the the windows install disk with the fixmbr then fixboot and windows still won't boot. I then tried the grub settings and still the same problem.

---

### Post by oldfred on 2009-11-10
You may have issues with which drive boots first and which MBR controls booting. To see you config run this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

