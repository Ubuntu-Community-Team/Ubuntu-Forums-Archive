---
title: "Dual boot with d865glc MB grun not working"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by makoshark55 on 2009-06-20
OK I have been asking every were but still do not have an answer. I have an D865GLC motherboard the has BIOS settings for enhanced and legacy HDD. at this point I have to mess with the BIOS settings when I want to boot ubunto or windows XP. when the BIOS is set to enhaceced the SATA drive(3) becomes the boot drive. when set to Legacy in the BIOS the IDE drive becomes HDA0,6 and it is the bootable drive On my first out of 9 installes I had GRUB in the windows boot but all I got was a promt the said GRUB> and I could not do anything with it? I would like a way to leave the BIOS set to boot the SATA drive and dual boot without GRUB getting lost and confused, or is that me lost and confused. I need you to speek newbish as this in only my 4 day with ubuntu? [COLOR=Blue]Addition info I fond a way to leave the SATA on and boot ubuntu IDE drive first. Now if I knew how to map it I might get what I want. Any help here[/COLOR]? Pleaseeeees
Thanks Jim AKA makoshark

---

### Post by makoshark55 on 2009-06-20
Well I figured I out. I found another way to list my drives and hacked at the menu.lst until I got it to work
 on /dev/sdc1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
title           Windows XP Professional
root            (hd2,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd2)
map (hd2) (hd0)

---

