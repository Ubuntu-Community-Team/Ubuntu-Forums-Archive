---
title: "Booting Windows 7 (On external HDD) from Grub"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Mosaab on 2009-08-13
is there any way to boot windows 7 from an External HDD using grub which is on the internal HDD ?

cause I heard its impossible to make windows bootable NORMALLY from an external HDD using a USB interface unlike SATA interface which I dont have.

Help is appreciated :)

---

### Post by stlsaint on 2009-08-13
please understand that Grub does not boot windows...once you select vista install from  Grub it sends the booting responsibility to MBR for whatever windwos os you have! and im not 100% sure how windows 7 operates so i cant assist there! you should consider dual boot...thats where im useful at.

---

### Post by Mark Phelps on 2009-08-14
stlsaint is right -- GRUB only hands off booting to a boot loader on the partition identified in the menu.lst stanza.  The MS Windows boot loader takes over from there.

If your BIOS supports booting from USB drive, you should be able to install Seven and boot from there.  However, since MS Windows OSs routinely overwrite the MBR on the "first" hard drive they find, it would most likely overwrite the MBR on your internal drive and, after that, you might not be able to boot anymore unless your USB drive is connected.  That's probably not what you want.

---

### Post by AmerNewbieInDE on 2009-08-14
I run vista and seven on my internal hard drive, and ubuntu on external, for reasons of seven cant be run on external. I have an external sata and got no help from microsoft to install there. Only answer i got was "external installations are not supported". 

on the other hand, i did read somewhere it can be done.. i just didnt want to go through the hassels to do it, and ubuntu doesnt mind where it is installed :)

---

### Post by Mosaab on 2009-08-14
please excuse my ignorance about this but .. when I clone a HDD to another one (external) why doesnt the MBR get cloned asl well ? isnt the MBR Normal Data on the desk? why doesnt this work ... simply cloning a HDD with its MBR that has windows installed !

---

