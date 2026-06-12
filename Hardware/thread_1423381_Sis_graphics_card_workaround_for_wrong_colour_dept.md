---
title: "Sis graphics card workaround for wrong colour depth"
date: 2010-03-06
forum: Hardware
---

### Post by richs-lxh on 2010-03-06
If you use a laptop with a Sis graphics card, you will notice that new  Debian based distros are leaving you with the wrong colour depth, which  means you get blurred circles and strange colour blotches on your  desktop.

The fix is to use the "sisfb" framebuffer.

**With Grub2 you need to edit /etc/default/grub and add "sisfb" before "quiet splash" on the kernel line.**
*There are guides which tell you to edit */boot/grub/grub.cfg* even  though that document clearly states that it _shouldn't be edited_  and will be overwritten if Grub is updated.*
```
sudo nano /etc/default/grub
```**Change this section:**
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```**to:**
```
GRUB_CMDLINE_LINUX_DEFAULT="video=sisfb quiet splash"
```**Any changes to your Grub profile require an update:** (will add changes from "default" to "grub.cfg)
```
sudo update-grub
```Usually, that is enough and "sisfb" will be autoloaded at boot. If it doesn't (this has happened to me with Lucid Alpha), add sisfb to /etc/modules:
```
sudo nano /etc/modules
```**So that it looks like this:**
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
sisfb
lp

```There's always more than one way to skin a cat, but that is the fix I use for my Sis driven Acer Aspire 3004 laptop.

---

### Post by aimwin on 2010-05-02
I did not work for me for the high resolution, may be I am in the wrong thread, but I post my problem in the lunchpad in the following thread.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/8](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/8)

---

### Post by axelsvag on 2010-06-30
It worked perfectly for me. Thank you after two years of problem it suddenly was solved. Why could not that be in the kernel?

---

