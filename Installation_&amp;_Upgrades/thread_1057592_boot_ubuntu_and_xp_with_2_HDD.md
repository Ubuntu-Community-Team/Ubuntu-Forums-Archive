---
title: "boot ubuntu and xp with 2 HDD?"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Turd Ferguson on 2009-02-02
I already have Ubuntu installed and customized now I have a second HDD and I want to boot XP with Ubuntu. Can I do this? and what do I need to do if I can?

---

### Post by TaskmasterC on 2009-02-02
Do you want to boot xp and run Ubuntu from inside xp, or do you want the option for xp or Ubuntu?

---

### Post by Turd Ferguson on 2009-02-02
I want ubuntu as my main install and xp as a second option and preferable grub as the booter but dont mind whatever windows uses. I got a laptop with windows already so I don't need windows as much on this machine.

---

### Post by Turd Ferguson on 2009-02-02
I want ubuntu as my main install and xp as a second option and preferable grub as the booter but dont mind whatever windows uses. I got a laptop with windows already so I don't need windows as much on this machine. 

Edit: So both to answer your question and I don't have any intentions of using wubi if thats what your thinking. I don't have xp installed yet on the seconed HDD by the way!

---

### Post by lidex on 2009-02-02
Windows gets grumpy if it's not on the primary drive so you're in good shape if you just leave as is. You can simply install Ubuntu on the second disk and let grub handle the boot options with Ubuntu as default.
That is my setup - works great.

---

### Post by TaskmasterC on 2009-02-02
Well, you have a few options. You can install xp on the other drive, then set Ubuntu to be the primary OS in GRUB. I have 3 OS's and Ubuntu is first in the GRUB, followed by my 2 Windows OS's, all works fine that way. XP is on the first HH, and Vista and Ubunu are on the second.

---

### Post by lidex on 2009-02-02
Later I shrunk the windows partition and installed Ubuntu in the unallocated space on the primary drive as well. I don't work in it or
really update it either. It's mainly for backups and accessing main Ubuntu
if I screw it up since windows won't read ext3.

---

### Post by TaskmasterC on 2009-02-02
Well, if you decide to install windows on either HDD remember that you will have to use the Live CD and install the grub loader from it. Otherwise you will get a GRUB error when you try to boot. Or you can just turn off the drive you don't want in BIOS, but thats a pain to do if you are going to be using both OS's.

---

