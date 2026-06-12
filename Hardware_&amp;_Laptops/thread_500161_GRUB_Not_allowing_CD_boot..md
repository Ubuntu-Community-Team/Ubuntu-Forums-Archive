---
title: "GRUB Not allowing CD boot."
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by VoiceOvGod on 2007-07-13
(X- posted from Installations & Upgrades: [http://ubuntuforums.org/showthread.php?t=500156](http://ubuntuforums.org/showthread.php?t=500156))



I decided to throw FreeBSD on my Sacrificial Laptop last night, it currently has Ubuntu 6.10 and Kubuntu 7.04 installed.

When I tried to boot from the CD, it went to GRUB, even after attempting to force it to boot from the CD.

When in the desktop environment, it was not even acknowledging the CD drive.

I also tried booting from a USB drive, but same result.

I do not know if it is not detecting the USB drive in the desktop environment either.

Ideas?

---

### Post by bdtgp on 2007-07-14
Did you try turning on your computer and going into Setup? (before anything boots)
From there you can change the first boot device to the cd and then second to the hard drive.
Also double check to make sure your cd is a bootable cd. sometimes people just burn the iso image directly onto a cd and it doesnt work that way.

---

### Post by marpstar on 2007-07-14
GRUB only loads once the hard drive has been selected as the boot device, which means that either your disc is not bootable, your computer is set to boot from hard disk before your optical drives, or something is wrong with your optical drive.

Do what bdtgp said and check your BIOS options and your media.

---

### Post by VoiceOvGod on 2007-07-14
I've tried adjusting the boot order, and forcing it to to boot the optical first, but it ignores it.

The iso is actually from a Linux mag, I also tried an iso of Slackware, and same result.

---

### Post by Canuckelhead on 2007-07-14
watch as you boot... sometimes you have to hit a key or something to boot from cd even if it's #1 on the boot order....  this is the case with my roomie's box...  I have to monitor it and select the boot from cd...

---

### Post by VoiceOvGod on 2007-07-14
I didn't see anything that says "Press XX to boot from CD" if that's what you are talking about.

So far, USB still works, so I am thinking I might need to grab a cheap usb CD/DVD drive.

---

