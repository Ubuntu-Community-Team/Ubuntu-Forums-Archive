---
title: "[SOLVED] reinstalling"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by theozzlives on 2009-01-08
is there a way to re-install Ubuntu without losing all the 3rd party apps? I want to do some partition resizing and I always have to install when I resize my /home partition.

---

### Post by aesis05401 on 2009-01-08
I'm not sure we are talking about doing the same thing, but won't using a utility disc like Gparted prevent you from needing to reinstall.

I have done something like the following:

Reboot with GParted (or other bootable utility disc)
Create/Format new/larger partition
Copy image of old partition into the new partition
Set the new image as bootable
Attempt to boot into the new image
*Had to do some sort of integrity check here .. don't recall :) *
Use all that new space

Sorry if there is an obvious problem with my suggestion, I am new to Ubuntu.

---

### Post by theozzlives on 2009-01-08
Nevermind, I just resized my windows.

---

