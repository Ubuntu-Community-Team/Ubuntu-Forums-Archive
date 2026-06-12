---
title: "Unetbootin's Frugal HD Install for Linux Host"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by floborg on 2009-03-24
Found very little information on the hard disk option in Unetbootin.  It may be new, based on what I saw at it's SourceForge page.

Anyway, I've tested it in VirtualBox with Hardy and frugal installs of a couple Linux distros, FreeDos, and KolibriOS.  In the case of an ISO, it appears to dump the CD contents into the root of the main filesystem.  It also creates some special kernel files and intitrds and appends a new option to the Grub menu.  For the floppy IMGs, it just creates the kernel and updates the Grub menu.  The frugal installs appeared to boot correctly, and the uninstaller appeared to clean up everything that was altered by the install.

I've used it successfully on my actual machine for some one-floppy images, but the whole ISO install/uninstall just feels a little to "automagic" for me to take a chance.  I'd prefer a tidier frugal install to a subdirectory - perhaps, one that is portable.  Is this possible?

---

### Post by floborg on 2009-04-08
two-week bump

---

### Post by floborg on 2009-05-04
5-week bump

---

### Post by pwn on 2009-06-17
I could not even get any LiveCD to boot using the hard disk option.

---

### Post by Jesdisciple on 2010-09-20
Just thought I'd update this thread... [https://bugs.launchpad.net/unetbootin/+bug/351556](https://bugs.launchpad.net/unetbootin/+bug/351556)

---

