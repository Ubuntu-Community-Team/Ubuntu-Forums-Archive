---
title: "Making CD"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-02-15
How do I make this CD from the ISO I downloaded? Do I just drop the file onto the CD? I've never really made a CD from ISO before.

---

### Post by bluevoodoo1 on 2006-02-15
What operating system are you using? What burning software are you using?

You can't burn it as you would any piece of data. You'll have to look for an option that says "burn as cd image" or "burn as iso" so that it will be a bootable CD.

EDIT: you're using Kubuntu, didn't see that...

---

### Post by taurus on 2006-02-15
You first need to run md5sum to make sure the file is good during the transit.  Then, you have to burn it to your CD as an image file, not a data file or you won't be able to boot!  Not sure which burner software you use but as far as I know, they all have an option where you can burn it as an image file!  And when it's done, you want to go into your BIOS and change the order of boot.  Put the CD-ROM first, floppy second if you have it, then the harddrive.  That's all...

---

### Post by bluevoodoo1 on 2006-02-15
[QUOTE=taurus]And when it's done, you want to go into your BIOS and change the order of boot.  Put the CD-ROM first, floppy second if you have it, then the harddrive.  That's all...[/QUOTE]

There also might be an option to boot from your CD drive instead of your HD, it's probably one of the F* buttons. I think mine is F8. My old Dell did it, my ASUS machine can do it now, then you don't have to alter the boot order in BIOS.

---

