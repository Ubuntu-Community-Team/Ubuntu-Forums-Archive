---
title: "Re-allocating hard drive space to Windows partition"
date: 2008-11-11
forum: General Help
---

### Post by sporkubus on 2008-11-11
Hi guys, so I shrank down my Ubuntu partition so that I could make my Vista partition bigger. Now I have a large amount of free space showing up in GParted, but I can't seem to allocate it to the Windows partition - when I edit that partition, it doesn't show any space as being available. It's also still listed under the Linux partition, which seems to be the problem. Anyone know how I can get that space back to my Windows partition?

---

### Post by Shazaam on 2008-11-11
Did you defrag Windows first? If you can, post a screenshot of gparted.

---

### Post by sporkubus on 2008-11-27
hey, sorry this took so long. Here's the screenshot. I'm not sure what defragging Windows would do to help the problem?

---

### Post by psusi on 2008-11-27
You need to move the linux partition to the right so that the free space immediately follows the windows partition.

---

### Post by CatKiller on 2008-11-28
Not just the Linux partition (sda5), but also the extended partition (sda3) that surrounds it.

---

### Post by sporkubus on 2008-12-19
> **CatKiller said:**
> Not just the Linux partition (sda5), but also the extended partition (sda3) that surrounds it.

I don't understand how to do this.

---

### Post by plucky on 2008-12-19
You have to boot the Live CD or the [Gparted Live Cd](http://gparted.sourceforge.net/)


Assuming the Live Cd go to **System > Administration > Partition Editor**

1) Select /dev/sda5 and move it,do not resize,to the right into the unallocated space.(This could take a long time)

2) Select the swap partition and un-mount.This partition is mounted on the Live Cd.You will not be able to resize the extended partition if the swap partition is mounted.

3) Select the /dev/sda3 partition and resize.The unallocated space will be moved next to the ntfs partition.

4) If you are using vista,use the vista partition manager to extend the ntfs partition.If not then use gparted to resize the ntfs partition to take up the un-allocated space.

[color=red]Make sure you have backed up your important files before attempting this,just in case it doesn't work[/color]


Good Luck

---

### Post by sporkubus on 2008-12-19
> **plucky said:**
> You have to boot the Live CD or the [Gparted Live Cd](http://gparted.sourceforge.net/)


Assuming the Live Cd go to **System > Administration > Partition Editor**

1) Select /dev/sda5 and move it,do not resize,to the right into the unallocated space.(This could take a long time)

What i don't understand is how do I move /dev/sda5 to the right?

---

### Post by CatKiller on 2008-12-19
> **sporkubus said:**
> What i don't understand is how do I move /dev/sda5 to the right?

Provided you are running a live cd (so the partition isn't mounted) you select the partition, hit the Resize/Move button, and then just click and drag.

> **sporkubus said:**
> I don't understand how to do this.

You'll do the same procedure for /dev/sda3, which in the screenshot you posted earlier is represented as the light blue box around sda5, sda6 and the unpartitioned space.

---

