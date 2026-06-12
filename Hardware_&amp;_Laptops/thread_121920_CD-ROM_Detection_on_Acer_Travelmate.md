---
title: "CD-ROM Detection on Acer Travelmate"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by rappatappa on 2006-01-26
My problem is that when i attempt to install Ubuntu 5.10 on my Acer Travelmate it cannot autodetect my CD-ROM drive and none of the manually selectable drives seem to work and the installation fails.  I do not have a floppy drive, so that makes it a bit impossible to load floppy drivers for the CD-ROM.  I admit that I am a Linux noob, so any help would be most appreciated and please excuse my ignorance. :confused:

---

### Post by 5-HT on 2006-01-27
Hi,

I had a very similar problem when trying a clean install of Breezy (Hoary worked great though).

I found that disabling ACPI allowed me to install with no problems (well...apart from disabling ACPI).

Not sure if the same route would be of help to you, but it's worth a shot.

If you want to give it a try, to disable ACPI for the install (and to have it automagically disabled in GRUB's menu.lst), enter this when you are presented with the install cd prompt:

```
 linux acpi=off noacpi 
```

Hopefully, that should let you install and enjoy Ubuntu.

If not, please post again in the chance that someone else may be of help.

HTH

---

### Post by kingsidy on 2006-01-27
if you mean it is not booting to the install cd, then you need to go into the BIOS and make the cdrom boot first. i do not know whether that is the issue or not. then you can try 5-ht 's advice otherwise.

---

### Post by helgman on 2006-02-01
I'm having the same problem (and I too am trying to install on an Acer Travelmate). It just won't find that CD-ROM (in my case a DVD). I did manage to find it with Mandriva, but then there was some other problems ...

I can't even find anything that could be my CD-ROM drive in the /dev directory. I've started the installation using both the "linux acpi=off noacpi" parameter and one other that I can't remember.

Has anyone solved this problem?

---

