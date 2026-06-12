---
title: "******* u3, how do i remove it from usb drive?"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by jamesford on 2007-06-29
how do i remove the uberannoying totally useless, probably dangerous, u3 from a usb drive without having access to any windows machine, or virtual win machine ?

---

### Post by klrrider on 2007-06-29
> **jamesford said:**
> how do i remove the uberannoying totally useless, probably dangerous, u3 from a usb drive without having access to any windows machine, or virtual win machine ?
I'm guessing here but I think you can simply delete the following;

System Folder
LaunchU3.exe

That should do it. Or you could format the pendrive and wipe it out for sure.

---

### Post by jamesford on 2007-06-29
ive deleted those files, they reapper
the hidden u3 partition doesent appear in gparted
ive formatted but the u3 stuff seems to be hidden, it doesent go away

---

### Post by Noobie555 on 2007-06-29
hey i had the same problem go tho the u3 site and they got a program to remove it quick and easy hope this helps

---

### Post by Licurgo on 2007-06-29
I have a USB pendrive and partitioned and then formatted and this solved the problem to uninstall the U3.

---

### Post by jamesford on 2007-06-30
Noobie555 , thats a windows uninstaller isnt it?

Licurgo, could u walk me through that? ive formatted it using gparted but the u3 stuff doesent go away!

---

### Post by hronir on 2007-10-16
I have the same problem, fdisk can't even see the u3 partition...
I googled this
[http://forums.macosxhints.com/showthread.php?p=361449](http://forums.macosxhints.com/showthread.php?p=361449)
which seems to say no-hope.

There's really no way to do it by shell?!?

---

### Post by notwen on 2007-10-16
You have to remove it using [Sandisk's software]("http://www.u3.com/uninstall/"), which is only available in Windows.  I simply downloaded it and copied it to my drive and the next time I had access to a Windows machine I used their utility and wiped my drive.  Was really annoying at best, solid USB drive tho. =]

---EDIT---
You could try running it through WINE or possibly a Virtual machine.  Just a thought, not sure of it working w/ either.

---

