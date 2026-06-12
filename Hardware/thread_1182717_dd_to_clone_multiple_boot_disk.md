---
title: "dd to clone multiple boot disk"
date: 2009-06-09
forum: Hardware
---

### Post by amk221 on 2009-06-09
I've cloned a hard disk using dd if=/dev/sda of=/dev/sdb on a live cd

On it, was XP and Xubuntu on their own partitions. Grub was used to select which OS during boot.

It seems to have worked great, Xubuntu boots when I select it - but XP seems to boot, but then reboots the machine a few seconds in.

In Gparted, there is an exclamation mark next to the XP partition saying it cannot be read or something along those lines.

Any ideas what I can do to get XP to boot?

thanks

---

### Post by dandnsmith on 2009-06-09
Was the new HDD an exact duplicate of the old - same size, same number of heads, same number of tracks?

When you do the dd like that, you do a physical copy of the MBR, which contains info about the disk. Windows relies on this, but linux refers to the BIOS.

How do you fix it? - with a bit of difficulty.

You might be able to avoid it by the following (on a blank HDD)
1. create a partition table, and partitions of the correct size.
2. use dd for each partition, so dd if=/dev/sda1 of=/dev/sdb1
3. install grub on the MBR
4. ensure the XP system partition has the boot flag set

I'm not sure whether that will work, but it stands a better chance.

---

### Post by amk221 on 2009-06-09
No, it was from an 80gb, to 300gb disk

that explains it then.

damn.

---

### Post by dandnsmith on 2009-06-09
If that's the case, you'll have to clear all partitions first, definitely - as it will now be showing itself as 80GB.

Having had a bit more time to think, you may have to do repair work on XP to convince it that its partition is the one to use. I don't remember how you do that, and cannot be sure that I ever cloned the XP partition (certainly not in that fashion).

---

