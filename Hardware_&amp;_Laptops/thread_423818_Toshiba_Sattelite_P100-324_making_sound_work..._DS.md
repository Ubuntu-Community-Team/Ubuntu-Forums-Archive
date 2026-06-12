---
title: "Toshiba Sattelite P100-324 making sound work... DSDT customization"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by samopal on 2007-04-26
hi, 
I followed few good guides how to recompile DSDT.asm file and load it to kernel to get some of Toshiba P100's sound working. I followed the guide (in French) [http://sle.homelinux.net/olive/?p=67#more-67](http://sle.homelinux.net/olive/?p=67#more-67) steb by step, but for me, it seems to be not working... sound cracks on startup (this wasn't before), so sound should be OK, but nvidias drivers won't load... 
I uploaded custom DSDT.aml file on acpi.sourceforge.net -> [http://acpi.sourceforge.net/dsdt/view.php?id=779](http://acpi.sourceforge.net/dsdt/view.php?id=779) 

dsdt.dsl file attached. 

does anybody know how to move with this? i'm stuck here...
compiled on 2.6.20.14 kernel, because i didn't want to mess with most recent kernel i'm using - 2.6.20.15. 
maybe that's the reason it don't work, but i don't know how to backup it, or recover if recompile it with wrong dsdt and it won't start... i can't afford loosing my system :<

---

