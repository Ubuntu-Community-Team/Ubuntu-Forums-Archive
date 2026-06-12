---
title: "ubuntu starts up un readable graphics"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by Digitallysick on 2005-08-07
I recently installed an Nivida 128mb graphics card, when ubuntu starts up (black screen white words) they are unreadable, all jumbled up, but when startx everything is fine, the graphics are great, any way to fix??

---

### Post by grj on 2005-08-07
if you added a vga=<some number> parameter to your /boot/grub/menu.lst file remove it and see if that solves it. You will have to edit the file using the sudo command.

---

### Post by Digitallysick on 2005-08-07
## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


the grub menu shows up fine but when i select ubuntu, then the graphics go bad, i cant read whats loading, so far its not that big of an issue, i am in kde most of the time, but would be nice if it would work right again

---

