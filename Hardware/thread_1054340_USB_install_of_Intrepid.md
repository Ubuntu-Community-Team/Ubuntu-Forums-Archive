---
title: "USB install of Intrepid"
date: 2009-01-29
forum: Hardware
---

### Post by Nalroff on 2009-01-29
Hi all.

I currently have a Toshiba Satellite A105 that had the CD drive completely ripped out of socket, so I have no CD drive. I would like to install from a usb stick, which I have prepared and attempted to do with ubootin. For some reason, when I try to open the usb stick for booting (I have my BIOS set up to open from the usb memory initially) it goes straight to my currently installed GRUB as if I don't even have the stick in. My current boot order is as follows:

1. USB Memory
2. USB HDD (no idea what the difference is here)
3. Internal HDD
...etc.

I am certainly open to other options (such as ghosting, open source style of course ;)) but I am completely stupid when it comes to firmware/primitive networking, so step-by-step instructions are appreciated. I am also currently dual-booting Ubuntu Intrepid and Windows XP Home; I just need a fresh format.

Thanks in advance for any advice.

---

### Post by snowpine on 2009-01-29
Dumb questions perhaps, but 1) have you tested the USB stick on a different computer to see if it works? 2) is the partition's boot flag set? (you can do this in gparted)

---

### Post by Nalroff on 2009-01-30
Good call, snowpine!

I did check the USB drive to make sure it had the boot flag on gparted. However, when I tried to boot to it from my brand new desktop, it did a very similar thing. I got the boot menu up on it (it's a brand-new Gigabyte P45 mobo, very nice) and it allowed for 4 different kinds of "USB boot." I did not try all of them, but I did try USB-CD-ROM, considering it is a derivative of a CD image file, and I also tried USB-HDD to no avail. Do you think it may be the thumb drive? It's a 2 GB Sandisk Cruzer, but I uninstalled all that U3 crap that comes on it to begin with. Even if there were remnants of that, unetbootin reformats the drive to FAT16 anyway. Could that have anything to do with it?

Thanks for the quick feedback!

EDIT: After messing with it a bit, I've noticed that the computer sits on a terminal screen with a blinking cursor for a long time when I have the stick in. Also, the stick itself seems to heat up quite a bit before it actually goes to the GRUB loader. Hope this helps.

---

