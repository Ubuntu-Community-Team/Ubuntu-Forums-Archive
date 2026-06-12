---
title: "CD-ROM Not Found"
date: 2008-08-04
forum: General Help
---

### Post by bks on 2008-08-04
I am trying to install Xubuntu 8.04 on a Compaq Armada 1530DM (P133/80MB RAM) and I can't get the CD-ROM to work. Here's what's happening:

I can't get into the BIOS setup to change boot order, so I used RawWrite to write sbm.bin to a floppy. SBM was able to detect the CD-ROM and it booted the Xubuntu alternate installer, but from here it gets frusterating. I start the install and get through the language and keyboard layout, but when the installer trys to detect the hardware, it can't find the CD-ROM :confused:

I've tried using the terminal (ALT+F2) to locate the module in /dev, but there's nothing there. This is my first try with the alternate installer, so if anyone has any ideas, I'm all eyes :lolflag:

If you need anymore information, I'll do my best to provide it.

---

### Post by oldos2er on 2008-08-04
You should hit F10 on bootup to access the bios. Xubuntu is going to run very slowly on such a low spec machine; I think you should try Puppy Linux or Damn Small Linux instead.

---

### Post by snowpine on 2008-08-04
DSL is your friend with those system specs, good luck!

---

### Post by bks on 2008-08-04
> **oldos2er said:**
> You should hit F10 on bootup to access the bios.

I have tried pressing F keys and none of them seem to do the trick. I seem to remember something about Compaq using a hidden partition to access the BIOS. Somewhere along the line, said partition on this machine got whacked!

> **oldos2er said:**
>  Xubuntu is going to run very slowly on such a low spec machine; I think you should try Puppy Linux or Damn Small Linux instead.

I had thought about trying a different version, 6.06 perhaps, but maybe you're right.

---

