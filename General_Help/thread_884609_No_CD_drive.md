---
title: "No CD drive"
date: 2008-08-09
forum: General Help
---

### Post by WeyOh on 2008-08-09
Hi,

I have a laptop with dual boot (Win XP/Ubuntu 8.04). The ubuntu installation is old, and it was originally a 6.06 which has upgraded every time a new distro came out. It has many programs I had installed just to try them and I have also played a lot with the configuration, so it's not fully stable. I wanted to reinstall Ubuntu, but the CD drive doesn't work anymore on the laptop. I was wondering, can I reinstall Ubuntu using wubi and a virtual drive for the image file of Ubuntu? Are there any other solutions?

Cheers,

Sam

---

### Post by spike.robinson on 2008-08-11
No problem. You are in the same situation as me. My CD drive on my Toshiba is broken. I still managed to install the latest Ubuntu using Wubi. As per the WubiGuide, you need to download the Desktop ISO file and put it in the same location as Wubi. Wubi and the Ubuntu ISO need to be the same version. Then everything installs fine and you don't need the CD.

---

### Post by issih on 2008-08-11
Not what you asked, but as you already have a full dual boot setup, you could just upgrade into the already existing partitions (rather than using wubi) via a usb flash drive provided your bios supports booting from usb. 

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

That guide is pretty good and shows how to do it from windows :)

---

### Post by WeyOh on 2008-08-23
Issih, unfortunately my BIOS doesn't allow me to boot from USB.

But if I install with Wubi, won't it install on a virtual drive as opposed to the existing partition? I have never used Wubi, therefore bear with me...

---

### Post by gnuvistawouldbecool on 2008-08-24
> **WeyOh said:**
>  unfortunately my BIOS doesn't allow me to boot from USB.

Not that I'm saying you're wrong about that, but my bios doesn't say it can do that but if I stick a bootable USB drive in it will work if I look under boot from local drive in the BIOS.  Just an idea.

Also, If you have a floppy drive you may be able to force it to boot from a USB stick.

And as for a wubi install, well if you have the internet access for it, you could always use that and then use LVPM or whatever it's called to get it into it's own partition.

---

