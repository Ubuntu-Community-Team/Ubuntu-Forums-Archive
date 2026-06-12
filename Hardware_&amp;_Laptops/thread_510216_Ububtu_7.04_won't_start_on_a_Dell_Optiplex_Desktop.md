---
title: "Ububtu 7.04 won't start on a Dell Optiplex Desktop"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by dipankarsahu@gmail.com on 2007-07-26
I am absolutely new to Linux.
However, I got a copy of Ubuntu 7.04 (Live CD) and tried to install it on my Desktop (Dell Optiplex 320, 3.0 GHz, 1 GB, 160 GB, Win XP pro, SP 2). I used the partition manager to dedicate 30 GB to Ubuntu and completed the installation successfully (I got the message saying installation completed successfully). 

Here the problem started. When the system was restarted, nothing happened. Ubuntu would not boot, when I choose the option from the boot menu.

Then I tried to re-install Ubuntu on the entire harddisk and I had the biggest problem. Nothing happened and my desktop is now doing nothing but a blank screen with a small white cursor blinking on the top left corner.

Kindly help.

---

### Post by ianare on 2007-07-27
That's a known issue with GRUB (the boot loader)

[https://bugs.launchpad.net/ubuntu/feisty/+source/mdadm/+bug/75681](https://bugs.launchpad.net/ubuntu/feisty/+source/mdadm/+bug/75681)


check for solution here:
[http://ubuntuforums.org/archive/index.php/t-330397.html](http://ubuntuforums.org/archive/index.php/t-330397.html)

[http://ubuntuforums.org/showthread.php?t=409345%20](http://ubuntuforums.org/showthread.php?t=409345%20)


it looks complicated ... if you are new to Linux you may want to try a distro that allows you to install using LILO (the other bootloader) right from the installer.

Debian is very good (ubuntu is based on it), Fedora is also nice.

Or this will be a very good learning experience!!

Best of luck.

---

