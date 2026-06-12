---
title: "How do I enable SATA/AHCI mode on an ICH7-M controller?"
date: 2014-04-20
forum: Hardware
---

### Post by marcosscriven on 2014-04-20
I have a Samsung NC10/N100 netbook, which sports the ICH7-M chipset. I'm certain it allows AHCI/SATA, but there's no option in the BIOS.

I read that it's possible to switch it on by using setpci, but there seems to be both slot and address based methods.

lspci -nn gives me : 00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02) 

So I tried both:

setpci -s 00:1f.2 90.b=40

And:

setpci -d 8086:27c4 90.b=40

I tried putting this just before 'set root (hd0,msdos1)' in my /boot/grub/grub.cfg file in Ubuntu 14.04 but it just hangs.

Any ideas how to get this working pls?

EDIT - I've read elsewhere the BIOS can be downgraded, but I don't want to have to do this, otherwise it may introduce errors that don't exist in newer BIOSes.

---

### Post by Whoopie on 2014-04-20
a

---

### Post by marcosscriven on 2014-04-20
Whoopie - just saw you responded, but there's nothing other than 'a'?

---

### Post by marcosscriven on 2014-04-20
In case anyone wants to find out the same - I eventually found this really useful link: [http://www.voria.org/forum/viewtopic.php?t=248](http://www.voria.org/forum/viewtopic.php?t=248)

Update to 05CA - it even includes the BIOS itself, and a DOS USB update image!

---

### Post by Whoopie on 2014-04-21
I wanted to write the same about BIOS 05CA, but I then read that AHCI doesn't work even if you enable it in the hidden BIOS menu. And as I don't own this netbook, I was uncertain to post it. That's why I changed it to "a".

---

