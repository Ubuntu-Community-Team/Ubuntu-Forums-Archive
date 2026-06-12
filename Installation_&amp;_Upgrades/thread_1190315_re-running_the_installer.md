---
title: "re-running the installer"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2009-06-17
This is a pretty silly question, but hoping someone knows the answer.

The system installer (when popping in mini.iso liveCD & do the portioning & stuff) is a pretty useful & versatile tool, and I'm hoping to run it again, after the system has already been installed, to reconfigure some stuff.

From what I can gather, it consists of:
* basic kernel to get the installer OS going
* mirror & locale settings
* partitioning tool, with support for LVM, and the ability to resize a pre-existing windows partition. some variation of fdisk or cfdisk
* kernel picker: generic, server, desktop, virtual, etc. This is the juicy bit I'm after, as I may wan to change the kernel, say, from a server to generic without having to completely trash my existing installation & configs
* system task & role selector: tasksel

If tools such as `tasksel` is still available on the system, it stands to reason that the other tools are too, or are just an apt-get away

---

### Post by lemming465 on 2009-06-18
The documentation for *ubiquity* suggests it isn't useful on a running system.  However, *dpkg-reconfigure* might be a great help to you.

---

### Post by freakalad on 2009-06-18
Ubiquity? Thanks for that info; I'll look into it a bit more.

I've used the dpkg-reconfigure tool on numerous occasions (frequently with the -a option), especially if I've broken something good & proper, but in this case. it's not exactly the tool I'm looking for.
Besides, sometimes dpkg-reconfigure is pretty hit & miss when trying to guess which packages to config

But I thinks Ubiquity is ringing bells in the right direction

---

