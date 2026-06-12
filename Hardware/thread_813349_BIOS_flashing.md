---
title: "BIOS flashing"
date: 2008-05-30
forum: Hardware
---

### Post by CSquared on 2008-05-30
I'm running Heron on my half-dead laptop to get it working again.  The HDD is corrupt, so every other boot, I have to run a manual fsck (why doesn't that map out the corrupted sectors, by the way?), but I'm replacing the HDD soon anyway.

It's an Acer Aspire 3102WLMi, and the BIOS flashing utilities provided by Acer are, unsurprisingly, Windows based.  Well, MS based.  There's a DOS option, involving running a .bat, and a Windows option, with a .exe.  What's the easiest way to get one of these to work?  Am I better off trying to run the .exe under WINE, or is there some nice easy way to run a .bat in the terminal, or something like that?

I'm fairly sure this will fix a fair few of the problems the laptop's having, so any help will be greatly appreciated.

---

### Post by oVIXx on 2008-05-30
Wine is good for a lot of programs but I wouldn't flash a BIOS using it. One little quirk and you nuke your mobo. 

Best bet is to use the DOS environment. If you have access to a Windows machine format a floppy using the "format A: /s" command. This will copy system files to boot from onto the floppy. After it's finished formatting if theres enough room on the floppy copy your flash program and the binary BIOS file to it. If not, put the flash program and the binary BIOS file onto another floppy and insert it after the startup disk has loaded the DOS environment. A:>

---

### Post by acron1 on 2008-05-30
> **oVIXx said:**
> Wine is good for a lot of programs but I wouldn't flash a BIOS using it. One little quirk and you nuke your mobo. 

Best bet is to use the DOS environment. If you have access to a Windows machine format a floppy using the "format A: /s" command. This will copy system files to boot from onto the floppy. After it's finished formatting if theres enough room on the floppy copy your flash program and the binary BIOS file to it. If not, put the flash program and the binary BIOS file onto another floppy and insert it after the startup disk has loaded the DOS environment. A:>

You will need to have a floppy drive to do it this way of course.

---

### Post by tamoneya on 2008-05-30
most newer motherboards can do the floppy method with a USB drive instead.  Since this is a laptop this is probably the prefered method.

---

### Post by oVIXx on 2008-05-30
Well maybe you didn't read it fully, thats an older laptop, <2 ghz and probably came with a floppy drive. 

 :) If you have a computer w/out a floppy drive, you've been duped.

---

### Post by CSquared on 2008-05-31
Yeah... it's not **that** old a laptop.  It's only just out of warranty.  And 1.8GHz isn't that much below 2. XD

Thanks for your help guys - I figured it might be something along those lines that I'd have to do.  I'll see what I can manage, I do have several Windows machines.

---

### Post by arvevans on 2008-05-31
If you have no access to a DOS boot disk, but do have a DOS version of BIOS Flash, it might be worthwhile to look here:

[INDENT][http://www.freedos.org/](http://www.freedos.org/)[/INDENT]

That will let you make a DOS bootable CD.

FreeDOS is sometimes helpful to do rescue operations on friends crashed DOS/Windows computers.

Arv
_._

---

