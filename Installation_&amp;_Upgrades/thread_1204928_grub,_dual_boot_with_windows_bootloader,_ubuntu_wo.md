---
title: "grub, dual boot with windows bootloader, ubuntu won't boot"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by jipajapa on 2009-07-05
I've been running a dual boot windows/linux system for several years now. I've gone through various iterations of lilo and grub. Windows runs on a first hard disk and linux runs on a second one. I started with Fedora 10, upgraded to Fedora 11, and then switched to ubuntu. 

Using Fedora 10, everything was working fine with grub as a boot loader. I could select windows or linux and grub smoothly managed to load the selected operating system. On upgrade to Fedora 11, quite happy with this state of affairs, I selected the option to update the existing configuration. When the upgrade was finished nothing would boot. Hm. After trying various suggestions to get grub going again (grub-install /dev/sda1, grub-install /dev/sdb, etc.), I gave up, used the Windows recovery disk, ran fixmbr and fixboot. Now at least windows is working again, but linux remains inaccessible. I'm using the Windows XP (SP3) boot loader now, and after carefully following the instructions at 

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

all I had was a blinking cursor whenever I tried to boot linux. So, just to try something new, I loaded ubuntu linux over the Fedora distro, left the box checked to install a new boot loader (on hd0) and tried again (after once again carrying out the steps in the link above to tell the windows bootloader where to find grub). The same blinking cursor whenever I try to boot into linux. Is there maybe some kind of diagnostic tool with grub to try and figure out what's going on with a system? Is there something obvious I missed that might need to be fixed? How do you troubleshoot a blinking cursor? 

Although I realize this is more of a grub issue than an ubuntu issue, any suggestions would be greatly appreciated.

---

