---
title: "dma issues with optical drives"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by narcosleepy on 2004-12-04
Trying to get dma enabled on my 2 optical drives (one dvd writer, other dvd player)

Harddrive: SATA
mobo: nforce2

i've been reading through alot of forums looking for a solution, found one that suggested using scsi emulation for the optical drives, [here](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=113685&highlight=dma+nforce) .  I'm using grub as the boot loader.  anyway when I added the option "hdc=ide-scsi hdd=ide-scsi" i get the error:

**FATAL: Module ide_mod not found** .. 

couldn't find much info on ide_mod, any clues on how to find it ;)  

Cheers everyone

---

