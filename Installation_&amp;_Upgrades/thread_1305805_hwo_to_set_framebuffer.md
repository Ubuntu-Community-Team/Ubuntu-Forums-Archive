---
title: "hwo to set framebuffer"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by bellnas on 2009-10-30
I install 910 , and when I set framebuffer following this:
[http://www.savvyadmin.com/console-framebuffer-in-ubuntu/](http://www.savvyadmin.com/console-framebuffer-in-ubuntu/)

but I can't find menu.lst in /boot/grub
I know 910 use grub2 default,

how can I set framebuffer ?

----------------------------
1- /etc/initramfs-tools/modules ,add:
fbcon
vesafb
2- /etc/modprobe.d/blacklist-framebuffer&#65292;find “blacklist vesafb”, comment it
3- /boot/grub/grub.cfg(old is menu.lst)&#65292;find kernel start line. add vga=0x317, the number due to your pc(used hwinfo --framebuffer see which your system support) 

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3c51a0d7-d373-473b-830e-225b6d7aafdf ro quiet splash vga=0x317

4- sudo update-initramfs -u

5- reboot

notice: My laptop can support 1400*1050 and I choose 0x349 (1400 1050 24bytes),and failed. Then I choose 0x318(1024 768 24bytes),succeded.

---

