---
title: "Grub error 25"
date: 2005-12-04
forum: General Help
---

### Post by mcrofutt on 2005-12-04
Hi,
 I'm trying to get my install of Kubuntu to boot on my 2nd hd and getting an error from grub. It says grub error 25,,,disk read error.
 I installed Breezy 5.10 to this drive and intend to make it Kubuntu, if only I can boot to it. 
 Here's my Ubuntu hda,1 menu list
 title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot


title		Kubuntu@hdb1 
root		(hd1,0)
chainloader +1
 Anything jump off the page to anyone?

 OH yeah, at the install I told Grub to NOT load to the MBR because I've had trouble that way before with it messing up a perfectly good install.
 Thanks a million in advance for any help.

---

