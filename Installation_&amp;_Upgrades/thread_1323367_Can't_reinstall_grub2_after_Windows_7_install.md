---
title: "Can't reinstall grub2 after Windows 7 install"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by magneze on 2009-11-11
I've been searching for the solution for this for ages, but can't get it to work.

I had Karmic and XP installed. I installed Windows 7 over XP and as expected the it splatted grub2.

However, I'm now booted off the LiveCD and I can't get grub2 to reinstall.

I always get this after executing "sudo grub-install /dev/sda":
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 
```
What am I missing?!?!?

---

### Post by jjcv on 2009-11-11
This article my be of help?

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Also, make sure that /dev/sda is still actually to correct device.

---

### Post by magneze on 2009-11-11
I've done this and /dev/sda is the right device (I only have one hard disk).
 
I successfully did this with Jaunty a few weeks ago but grub2 is different it seems. :(

---

### Post by viriimind on 2010-08-05
> **magneze said:**
> I've done this and /dev/sda is the right device (I only have one hard disk).
 
I successfully did this with Jaunty a few weeks ago but grub2 is different it seems. :(

maybe this would help you;
```
http://h0w-t0.blogspot.com/2010/08/how-to-reinstall-grub2-after-installing.html
```

---

### Post by oldfred on 2010-08-05
Are you telling it which partition the install is on, by mounting it before running the install.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

