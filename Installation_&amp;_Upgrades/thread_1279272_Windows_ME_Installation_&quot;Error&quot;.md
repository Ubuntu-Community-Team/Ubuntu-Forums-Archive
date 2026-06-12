---
title: "Windows ME Installation &quot;Error&quot;"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by robertomano24 on 2009-09-30
i have successfully managed to get grub4dos running, however, during installation of Ubuntu 8.10 (intrepid ibex)[using WUBI] in verbose mode freezes at "squashfs version 3.3..". everything seems to be in order, i dont know where to go from here. 

thanks for your time :)

and in advance, thanks for any help

p.s. ME is Millenium Edition for those who didnt know..


...........

---

### Post by lemming465 on 2009-10-03
Does a live desktop CD boot successfully on this hardware?

---

### Post by Mark Phelps on 2009-10-04
If you had bothered to read the Wubi Guide, you would have seen in the sections regarding Operating Systems, that Windows ME is clearly NOT supported:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by gamefreak2009 on 2009-10-04
Since ME is a crap OS I would say create the Ultimate Boot CD and wipe the hard drive using Dariks Boot and Nuke. (Hell anything by Microsoft with the exception of XP.)

Then after formatimg hard drive with UBCD put the Ubuntu disk in your Druve and restart. Also check BIOS and put CD-ROM as 1st boot device.

---

### Post by lemming465 on 2009-10-08
An ubuntu install will take about the same amount of space, whether you install it using loopback files in some foreign OS (WUBI style) or native partitions.  4-10 GB is a comfortable range, more if you are doing software development.

In your situation I'd let the ubuntu installer resize the vfat partition windows is installed on and put ubuntu on the rest of the space.  I'd also take the default boot options and let ubuntu's GRUB bootloader take over the MBR of the disk; it should automatically create a boot stanza in /boot/grub/menu.lst for the existing windows ME install.

---

