---
title: "pendrivelinux kubuntu usb cd boot not working"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-02-21
First question, has anyone managed to have a working USB CD Boot done with the procedure found at [pendrivelinux]("http://www.pendrivelinux.com/usb-boot-cd-for-kubuntu-810/") ?

I followed their instruction (did copy/paste) but when booting with it to get to my USB Kubuntu (install I did on it just like on an HD), I wind up on the busybox prompt.  I know my Kubuntu on the USB works because I booted with it (no CD) on an office PC and was able to do system updates and all. At home, I cannot boot from it so I have to create a USB CD boot (for some office PC also).

I somehow get the feeling their procedure is buggy. Pendrivelinux currently has no forums. So I am stuck asking in several places.

**CD content:**
boot.catalog
boot
-- initrd.gz
-- vmlinuz
-- grub
------ menu.lst
------ stage2_eltorito

**CD menu.lst content:**
title Run Kubuntu 8.10 from USB DISK
 root (cd)
 kernel /boot/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
 initrd /boot/initrd.gz

---

### Post by Browser_ice on 2009-02-21
I had sent an email to the pendrivelinux folks and this is the answer that I got :

> The Boot CD looks for a compressed squash filesystem not a full install!


Without any other explanation given, I guess this means I have to create a regular GRUB on the CD.

I found a [LINK ]("https://help.ubuntu.com/community/BootFromUSB")that might help me on this.

---

