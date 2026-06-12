---
title: "A linux-image upgrade broke my bootloader"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by lightpriest on 2009-04-09
Hello,

I've installed Ubuntu on /dev/sda6 (a part of an extended partition ofcourse).
After a while I wanted to move my installation to /dev/sda1 (primary) and remove windows completely.
I did so with 'cp -a'. After changing the boot/root configuration in grub/menu.lst and in fstab everything worked as before and as expected.

When I installed the recent linux-image (2.6.27-11-generic) package I was asked during the installation what do I want to do with grub's menu.lst.
I selected the "maintainers'" option. After the reboot grub displayed an error message.

Grub itself loaded fine. The kernel root parameter was the correct UUID for /dev/sda1.
The problem was that "root (hdX,X)" wasn't correct. It held the value (hd0,5) (if my 0,1 counting is correct it's /dev/sda6 :) )
Needless to say that before the installation this value was correct (I also checked grub/menu.lst.backup).

How did the package knew where I installed Ubuntu in the first time? Is there value written anywhere? Isn't it supposed to look at the current system state and take the values from there?
I've also tried looking at the post install scripts in the linux-image source's package, but with no luck...

It's not such a big deal to alter the menu.lst after a linux-image upgrade, but it doesn't feel right :)

Maybe there's some kind of dpkg-reconfigure for grub that addresses this?

---

### Post by cariboo on 2009-04-09
Use this [thread=224351]howto[/thread] to repair your grub problems, I've used it so often I can do it by heart :). I belive the drive info is stored in /boot/grub/device.map

Jim

---

### Post by lightpriest on 2009-04-09
Thanks for the reply.
I used this exact guide when I moved the installation to the primary partition :)
Plus, grub/device.map only maps the entire device and not the partitions.

I've cleared blkid.tab with blkid -g thinking blkid.tab is its reference.
I'll just have to wait and see then... :)

---

