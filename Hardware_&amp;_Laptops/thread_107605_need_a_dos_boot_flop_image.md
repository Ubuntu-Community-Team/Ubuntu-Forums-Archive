---
title: "need a dos boot flop image"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by stoeptegel on 2005-12-23
Hi all

I need a dos boot flop to get another computer's BIOS flashed. I have windows on my parents computer, but without a floppy drive. So i wanna ask for help ;) 
If one of you have windows installed you can help me:
-  make a boot floppy from [here](http://1gighost.net/jerseyboy/boot98se.exe) on a formatted FAT floppy disk
- boot linux and make an image of the floppy with $ dd if=/dev/fd0 of=bootdisk.img bs=512 count=2880 

I hope someone can help me out.
TIA

---

### Post by aamukahvi on 2005-12-23
Or you could download this:
[http://1gighost.net/jerseyboy/win98sc.zip](http://1gighost.net/jerseyboy/win98sc.zip)

Inside you'll find a floppy image. Mount it with mount -o loop, delete unnecessary files then add the flash rom and flash utility. Finally, burn a bootable CD using the image.

Hope it works for you. :)

---

### Post by stoeptegel on 2005-12-26
Yup that worked for me :)

Thank you kindly.

---

