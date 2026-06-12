---
title: "Hibernation and Swap file problems [solved]"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Talon2 on 2007-06-18
If you have been having hibernation or Swap file problems the issue may be that the UUID assigned to Swap is changing on each reboot.  This is bad news and has killed hibernation and Swap file on every system I support.  The problem started with Fiesty and continues in Gutsy.  Here is more info and a checklist showing what I did to fix it:

Bug #105490, first reported on 2007-04-11
[Feisty] Swap partition receives new UUID

Problem:  The Swap partition is assigned a different UUID on each reboot.  This kills Swap capability and hibernate capability.


Fiesty and Gutsy Swap/hibernate fix:

- Check swap:                       $ free | grep Swap

  If you see the follow then your Swap file is broken:

  Swap:            0          0          0


- Find the device name of Swap:     $ sudo fdisk -l

  UUID support appears to be broken as far as the Swap is concerned.


- Edit fstab with correct non-UUID information:     $ sudo gedit /etc/fstab


- Edit resume with correct non-UUID information:    $ sudo gedit /etc/initramfs-tools/conf.d/resume

  Example: RESUME=/dev/sda6


- Run:  $ sudo update-initramfs -u


- Reboot


- Check swap if you want:                       $ free | grep Swap


- Open some apps


- Test hibernate

---

This problem has caused me no end of grief.  How could something like this end up in a released product?

---

### Post by kidders on 2007-06-19
Hi there,

I agree with you. I can't quite understand the logic ... the use of UUIDs with swap filesystems seems so completely obviously inappropriate! :confused: Although referencing filesystems by UUID is immensely convenient in general, I've always stuck religiously to using /dev names for swap partitions ... precisely because (as you've mentioned) it avoids problems caused by reformatting swap space.

Thankfully it's a minor tweak. :-)

---

### Post by dashnak on 2007-06-19
This was happening to me as well, however, the fix didn't work, and am still unable to hibernate, it doesn't work, or it works but doesn't resume. Suspend is working just fine. Anyone has any insights on this?

---

### Post by wportre on 2008-06-01
My G*d this is a huge bug. I v nearly gave up on Ubuntu before I figured it out by sheer chance amending fstab to mount my other linux partitions. Here is the definitive thread on it: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637)

---

