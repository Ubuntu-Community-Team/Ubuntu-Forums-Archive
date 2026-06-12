---
title: "ubuntu persistent, problem after reboot"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by borisen on 2009-10-14
Hi, first of all sorry my bad english.

I have installed Ubuntu 9.04 on flash drive by this tutorial: [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

Everything is work fine, but when i reboot the machine, the led on my flash drive turns off and system does not boot. Bios dont see flash drive too. But if i turn off my computer and then turn on, everythink work fine until reboot ubuntu again.

Any ideas?

---

### Post by dstew on 2009-10-14
Have you tried the flash drive in other machines? I have a flash drive made by that tutorial that boots in some machines but not in others. I think different BIOSes act in different ways.

I have tried to get around this problem by installing grub to the flash drive instead of syslinux for booting, but I have incomplete success. The grub menu shows up in one machine, but syslinux in another! Same drive! I really don't understand these USB drives. I think BIOSes handle then in different, non-standard ways. If I make any progress I will let you know.

---

### Post by borisen on 2009-10-14
thanks for reply.
as for me, i have two flash drives one works normal but the second one have the problem that i described in first post, at the same machine...

---

### Post by borisen on 2009-10-14
i found this bug report: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702)

but don't undestend , this bug is the reason of my problem or not?
and one more question in 9.10(beta) this bug was fixed or not?

---

### Post by dstew on 2009-10-15
I think that bug is the source of our problems. I read that there are a lot of I/O errors seen at shutdown, and I am getting that. It seems they figured out a fix, but since the next version is not going to be using the same program for persisten USB, the old program will not be updated. There is a patch though that can be downloaded. See Steve's messages on that thread, toward the end. I think I will try it later when I get home.

---

