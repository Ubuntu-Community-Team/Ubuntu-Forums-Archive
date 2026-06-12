---
title: "Dead Windows, ubuntu boot not working"
date: 2012-05-03
forum: Hardware
---

### Post by Sejsel on 2012-05-03
Hi there, Windows 7 on my Sony Vaio PCG-4V1M laptop recently died. They are showing their System recovery options and I am unable to do anything with that, because I do not have CD-ROM to actually use Windows install CD. I decided to install Ubuntu from flash disc, I have set up the bios to accept it, the flash disc starts flashing, however nothing happens. The System recovery options appear again.

I would love to get some help with this, because I need it somewhat now. Thank you

---

### Post by 2ta8gdfte on 2012-05-03
> **Sejsel said:**
> Hi there, Windows 7 on my Sony Vaio PCG-4V1M laptop recently died. They are showing their System recovery options and I am unable to do anything with that, because I do not have CD-ROM to actually use Windows install CD. I decided to install Ubuntu from flash disc, I have set up the bios to accept it, the flash disc starts flashing, however nothing happens. The System recovery options appear again.

I would love to get some help with this, because I need it somewhat now. Thank you

 You might check the md5sum of the ISO if you can. There are a number of usb flash loaders that work nicely, unetbootin and multisystem at pendrive linux are two. Multisystem is a multiple loader that can have as many ISO's loaded that fit, and a persistance option like unetbootin. Also there is a post bios bootfrom menu that is often triggered with f12 at powering on, it may show in the bios gui as it passes by the actual key prompts if different.    [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by Sejsel on 2012-05-03
I am unable to use iso, because I can't get into Windows. I actually had to export the files from iso and directly put them in root of the flash disc. That is not working.

---

### Post by 2ta8gdfte on 2012-05-03
> **Sejsel said:**
> I am unable to use iso, because I can't get into Windows. I actually had to export the files from iso and directly put them in root of the flash disc. That is not working.

You can dd the iso or use a loader, use another's computer to load the usb.

Additionally I would think that the W7 has a recovery partition you should have a key sequence to activate it if there is one, a disc should not be needed. This will overwrite the W7, but if you get Ubuntu to boot up you can do some recover of what you want to keep. In the future make sure to image your OS's and backup everything and have a recovery disc W7 a OEM allows at least one recovery disc and full backup.
A excellent cloner [http://clonezilla.org/](http://clonezilla.org/)

---

