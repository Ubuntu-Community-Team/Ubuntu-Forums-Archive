---
title: "Problems with the bootloader"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by lukee on 2006-02-18
Hello! I'm new to Ubuntu Linux (just got my CDs in the mail yesterday), so bear with me. ;) 

I'm having a bit of a problem with booting. I'm in a bit of a strange situation- I have a Windows 98SE partition in /dev/hda1 (28GB), an Ubuntu partition in /dev/hda2 (10GB), and a swap partition in /dev/hda3 (380MB). (All partition size values are approximations.) The installation goes well- except when installing the bootloader. The GRUB install detects the Windows partition, but then gives an error saying that it can't install GRUB.

Now, there is one thing to note- because my motherboard doesn't recognize big hard drives (and mine's 40GB), EZ-BIOS (from Western Digital) was installed in the MBR to help with that. I have a feeling this may complicate things.

Does anyone have a solution? Thanks in advance!

**EDIT**: The solution was to create a new partition in the first 1023 cylinders of the drive to be used as /boot; no EZ-BIOS stuff is required.

---

### Post by lukee on 2006-02-18
Well, I managed to get GRUB to install (by erasing the MBR first), but now it gives me a "Missing operating system" error. Currently, the settings in the BIOS have it set to be a 528MB drive, as per the EZBIOS instructions when the drive was installed many years ago- but if I have it set to autodetect, the BIOS hangs when detecting the hard drive.

---

### Post by amoser on 2006-02-18
Well for one thing, I would try to get a new motherboard ([www.newegg.com](www.newegg.com) has them for really cheap).  Umm, also, try to reinstall Ubuntu, and when asked where to install GRUB to, make sure that you install to your MBR.

~Alan

---

### Post by lukee on 2006-02-18
[QUOTE=amoser]Well for one thing, I would try to get a new motherboard ([www.newegg.com](www.newegg.com) has them for really cheap).  Umm, also, try to reinstall Ubuntu, and when asked where to install GRUB to, make sure that you install to your MBR.

~Alan[/QUOTE]

Right now, getting a new motherboard isn't exactly an option. I tried installing GRUB to the MBR, but it still fails.

---

### Post by lukee on 2006-02-18
All right, so I decided to start from scratch and use Ubuntu for the whole 40GB (with some swap, of course). Everything went okay in this new install- but now, on boot, it hangs at "GRUB". How can I fix this?

---

