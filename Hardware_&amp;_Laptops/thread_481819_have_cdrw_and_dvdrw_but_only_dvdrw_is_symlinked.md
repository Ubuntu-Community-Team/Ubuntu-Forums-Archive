---
title: "have cdrw and dvdrw but only dvdrw is symlinked"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by keb on 2007-06-22
I have a Plextor cdrw and a LG dvdrw attached to the second ide cable.
After the system boots, when i look in /dev i see 4 symlinks:
    lrwxrwxrwx 1 root root 3 2007-06-04 12:55 /dev/cdrom -> hdd
    lrwxrwxrwx 1 root root 3 2007-06-04 12:55 /dev/cdrw -> hdd
    lrwxrwxrwx 1 root root 3 2007-06-04 12:55 /dev/dvd -> hdd
    lrwxrwxrwx 1 root root 3 2007-06-04 12:55 /dev/dvdrw -> hdd

How do i get the symlinks automatically setup so that my default cdrom and cdrw are the Plextor drive?
I suspect it involves adding or modifying some files in /etc/udev/rules.d/ 

Other info:
- I have Xubuntu 7.0.4, upgraded successively from 6.10 and 6.06 and 5.10

---

### Post by kidders on 2007-06-24
> **keb said:**
> I suspect it involves adding or modifying some files in /etc/udev/rules.d/You're absolutely right. Normally, what I prefer to do is add a new file in /etc/udev/rules.d & create custom devices & symlinks that live well away from Linux's own ones, so as not to interfere with things like automatic updates, that might alter udev's rulesets in the future.

Some general guidelines:
[LIST]
[*]If you alter one of udev's existing rule files, Ubuntu may refuse to change it during the course of future system updates, which can have unpredictable consequences.
[*]The numbers at the start of udev rule files dictate the order in which they are processed. For your own use, try to pick a number that's not too early & not too late.
[*]I would suggest creating symlinks with names like /dev/stuff/dvd or /dev/stuff/cdrw (ie things that exist completely independently of Ubuntu's default device names), so you don't have to babysit every system update that involves udev in the future.
[*]You can use **udevinfo** to grab useful information (eg device UUID, manufacturer name, and so on) for use in udev rules.
[*]A **sudo udevcontrol reload_rules** often saves you having to reboot to force rule changes into effect.[/LIST]While you're at it, you can always set up some other convenience rules, depending on your hardware. Examples include...
[LIST]
[*]If you use more than one pointing device or keyboard, xorg.conf can be far easier to write if you can predetermine the names of those devices in /dev.
[*]Some people get annoyed by the fact that the /dev names of USB block devices are effectively random (ie they depend on the order you connect your devices in). If you wanted to, you could force the creation of /dev/ipod, /dev/phone, or /dev/camera, to simplify your life.[/LIST]I hope that helps.

---

### Post by keb on 2007-10-19
thanks that was very informative!

---

