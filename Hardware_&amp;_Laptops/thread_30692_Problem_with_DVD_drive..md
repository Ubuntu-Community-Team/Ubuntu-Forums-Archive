---
title: "Problem with DVD drive."
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by word_virus on 2005-04-29
Hey, people!  Could some kind soul out there please help me with a couple problems I've been having with my Plextor 716S internal IDE drive under Hoary? I've tried searching the forums, but can't seem to find anyone who's experienced quite the same difficulty I am.

Specifically, when I put a DVD into my drive, an icon pops up for it on the desktop, and a new Nautilus window opens with the contents displayed.  Great so far, right?  Unfortunately, instead of giving me directories/folders I can open, Nautilus displays the contents of the disc as files (with little gnome feet icons).  So if, for instance, I have a directory on disc called /foo and one under it called bar/, I can see /foo but can't click it to get to bar/.  This is frusterating.

I assume the problem may involve my fstab, but really don't know where to start.  It is included here for your perusal:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                    /proc                    proc    defaults        0       0
/dev/hda1            /                           ext3    defaults,errors=remount-ro 0       1
/dev/hda5            none                     swap    sw              0       0
/dev/hdc             /media/cdrom0       udf,iso9660 ro,user,noauto  0       0
/dev/fd0              /media/floppy0        auto    rw,user,noauto  0       0

Hmm, and upon closer inspection, it looks like I don't have a /dev/dvd....  anyone know where I should go from here?

Thanks!!!

---

### Post by deathburger on 2005-04-29
[QUOTE=word_virus]/dev/hdc             /media/cdrom0       **udf,iso9660** ro,user,noauto  [/QUOTE]

Try changing that to "auto"? Just a guess, worst that'll happen is it won't mount until it's changed back.

Mine (Warty) reads just like yours does, but it works fine. I *do* have a /dev/dvd but it's symlinked to /dev/hdc .. not sure if anything aside from VLC wants it like that.

---

