---
title: "Samsung Instinct s30 won't mount"
date: 2009-09-01
forum: Hardware
---

### Post by emoguitarist06 on 2009-09-01
I'm trying to access my pictures and music from my Instinct but when I plug my phone into my Compaq Labtop running Ubuntu Jaunty it doesn't autodetect and it doesn't seem to mount anywhere.

Any suggestions?

---

### Post by newton21989 on 2009-09-03
Does dmesg give you any relevant output when you plug your phone in?

---

### Post by ktamm on 2009-09-09
There has been a bug lauched for this problem awhile back, however it doesn't seem to be resolved as of yet. If anyone knows of a solution please let me know. ([https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/299628](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/299628)). 

From another thread ([http://ubuntuforums.org/showthread.php?t=838278&highlight=samsung+instinct&page=3):](http://ubuntuforums.org/showthread.php?t=838278&highlight=samsung+instinct&page=3):)

> **hotani said:**
> UPDATE: If you have an Instinct, do NOT connect it to Ubuntu 8.10. This will result in data corruption of the media card which can only be repaired by reformatting via windows.

Steps to reproduce:
1- attach phone to machine running ubuntu 8.10
2- attach phone to machine running windows (I'm using and up-to-date build of XP)
3- attempt to write a file to the media card (I tried to copy a music file)
4- BSOD

This fails consistently. Reformatting the card to fat32 via windows fixes the problem (at the expense of whatever data you had on the card). Reading the card from windows does not cause a BSOD, only writing. 

Options if you have an Instinct: 
1- Downgrade to Ubuntu 8.04 if you are running 8.10 (I will not be connecting to any more 8.10 machines until there is some positive progress on the [bug in launchpad](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/299628)). Fortunately I have a machine running 8.04 both at home and work to use for accessing data from the media card and charging the phone.

2- *gasp* access the phone/card via windows. Yeah, I know.

---

