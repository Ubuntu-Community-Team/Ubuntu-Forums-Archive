---
title: "xubuntu vmlinuz/intrid.gz"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by theRightNee on 2009-01-10
i am hoping to install xubuntu using the cd image method outlined here

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

but i do believe i need the xubuntu version of vmlinuz/intrid.gz, which i cannot seem to find, in order to install xubuntu

any ideas?

---

### Post by logos34 on 2009-01-10
xubuntu uses the same kernel as the ubuntu release, so use the files here:

[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)**intrepid**/main/installer-i386/current/images/hd-media/

'cd image' approach requires alternate install cd, so make sure you get this one:

xubuntu-8.10-alternate-i386.iso  

good luck

---

### Post by theRightNee on 2009-01-11
so i downloaded the proper files, but i can't seem to start the partitioner?
all i get are ??? ???...

---

### Post by logos34 on 2009-01-12
so, you **extracted** grldr to c:, and xubuntu-8.10-alternate-i386.iso as well as the menu.lst is there too? 

You created the c:\hd-media folder and put vmlinuz and initrd.img inside?

If you've done all that correctly, and still nothing, then you might try using the regular ubuntu alternate install iso, but as soon as you complete the installation add the xubuntu-desktop metapackage and select that at gdm session login screen.

There's also the minimal-cd route, which will also allow you to choose the xubuntu desktop environment

---

### Post by theRightNee on 2009-01-12
no floppy drive/cd drive available..

---

### Post by logos34 on 2009-01-12
I meant you could use the minimal iso in place of the alternate.  I would swear it started up and worked when I tested it out a while back...

---

