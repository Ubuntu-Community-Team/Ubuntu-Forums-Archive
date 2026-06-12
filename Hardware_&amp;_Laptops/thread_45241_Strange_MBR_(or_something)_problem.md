---
title: "Strange MBR (or something) problem"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by pioni on 2005-06-29
I have an old ~10GB hard disk I recently got that I'd like to use with Ubuntu. However, the disk has some sort of old Windows virus on it and it has marked part of the disk as bad sectors. Because of this I'm unable to format the disk correctly, Grub doesn't install etc. Does the Ubuntu live-cd have any tool that could _really_ format the disk, including these "bad" sectors? The disk doesn't have anything worth sparing, so I don't have to worry about lost data.

---

### Post by Burkey on 2005-06-29
Low level format, the virus sounds a lot like the old "Pakistani Brain" from a looong time ago when hard disks were like 20Megs 5.25" glass plattered beasts.. *sighs* the goold old days.

The way I always fixed them was a low level format.  Later PC's could do it in their rom BIOS setup program (I used to use Debug) and depending how old your PC is probably has the option.  Otherwise get some disk-management software to do it (like Maxtor's MaxBlast etc.)

BTW, Low level format is not like a normal format, it has nothing to do with partitions, other than it ruins them.  It also is not something you do often as it is hard going on the drive (it touches every sector of every track on every platter)

---

### Post by pioni on 2005-06-29
The disk is from a ~1999 or so PC, which had Windows on it, which in turn might explain the virus.  :) I don't think the disk is in need of low level format (which I guess is impossible nowadays), just a quick recheck for the bad sectors might be enough. If I could do this somehow, I'll promise the disk won't ever see Windows again.  \\:D/

---

