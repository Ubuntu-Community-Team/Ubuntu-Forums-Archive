---
title: "installer hangs on (initramfs)"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by ninzeb on 2009-08-07
I downloaded the latest ubuntu CD image, and booted from it. 

I boot it up, choose install ( or even live CD ) and this is what the screen says:```
[    3.13608] Write protecting kernel text: 4128k
[    3.13906] Write protecting kernel read-only data: 1532k
Loading, please wait...
[    3.175337] Input: AT Translated set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Begin: Loading essential drivers... ...
Done.
Begin: Running scripts/init-premount ...
Done.
Begin: Mounting  root filesystem... ...
[    3.556252] FDC 0 is a post-1991 82077

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubutu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

(initramfs) dmesg | grep -e "error"
(initramfs)

```Where is the problem? I've installed different linux distro's (including ubuntu) in the past, so i'm a bit confused on this.

---

### Post by ninzeb on 2009-08-07
I figured out I had to use "noacpi" option.

What does it mean? Do I have to do something later, to use it?

Do I need to modify grub with this option?

---

