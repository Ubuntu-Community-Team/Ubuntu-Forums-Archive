---
title: "Via vt6410 IDE chipset"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by Eagleorn on 2006-06-19
Hi!

I have just installed Ubuntu 6.06 and it works fine, but i cannot use all my IDe disks.

I have one of my disks connected to Via vt6410 IDE chipset. The disk was recognized during installation, but now I cannot make it work.

When trying to boot into ubuntu the system hangs on "mounting root file system" and drops me to busybox, complaining about that hda3 does not exist. If I disable VIA IDE RAID support in BIOS, everything works fine, but I want to use those connectors as IDE (not RAID), but now they are useless in Linux.

What can I do about this.

I found this patch: [http://robertk.com/source/](http://robertk.com/source/)
but it says:
> The functionality of this patch is already included in the main linux kernel versions 2.6.15-rc2 and later.

I am running a custom compiled Linux kernel 2.6.16 (with ck12) I have an Intel Pentium D. Is it some kernel option i misconfigured?

Please could anyone help me and explain what I must do?

---

### Post by Eagleorn on 2006-06-19
I have encountered something interesting while experimenting.

When I look in /dev there are normally (when VIA vt64 chip disabled) the following disks:

[LIST]
[*]hda1
[*]hda2
[*]hda3
[*]hda4
[*]hda5
[*]hda6
[*]hda7
[*]hdb
[/LIST]

But when i enable the chipset (IDE functionality only) I find the following disks via busybox:

[LIST]
[*]hde
[*]hde1
[*]hde2
[*]hde3
[*]hde4
[*]hde5
[*]hde6
[*]hde7
[*]hdf
[/LIST]

It seems like something changes, and as I said, the boot up process complains about not finding hda3, where the root partition resides.

Looks like I have to change something in my configurations (remount?) how do I do this?

I don't know if this is the actual problem, I might be wrong out, so every hint that may help me to solve this problem is more than welcome!

---

