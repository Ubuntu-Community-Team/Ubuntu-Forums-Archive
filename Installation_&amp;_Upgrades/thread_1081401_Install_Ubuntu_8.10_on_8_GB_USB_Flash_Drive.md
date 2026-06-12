---
title: "Install Ubuntu 8.10 on 8 GB USB Flash Drive"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by danielky on 2009-02-26
Linux Newbie here. I have an 8 GB USB flash drive which has no files on it and is freshly formatted with the FAT32 file system. I have an Ubuntu 8.10 Live CD which I can use to boot into Ubuntu. I want to use the whole 8 GB to make a bootable Ubuntu USB flash drive. I have used the "Create a USB startup disk" successfully with a 2 GB USB flash drive that is formatted with the "FAT" file system. But I can't seem to get it to work with the new 8 GB flash drive. Anyone have a link for step-by-step instructions?

---

### Post by smani on 2009-02-26
If you want to use the USB drive just to install the OS (i.e. as a CDROM) you could also try with unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)).

---

### Post by wpshooter on 2009-02-26
> **danielky said:**
> Linux Newbie here. I have an 8 GB USB flash drive which has no files on it and is freshly formatted with the FAT32 file system. I have an Ubuntu 8.10 Live CD which I can use to boot into Ubuntu. I want to use the whole 8 GB to make a bootable Ubuntu USB flash drive. I have used the "Create a USB startup disk" successfully with a 2 GB USB flash drive that is formatted with the "FAT" file system. But I can't seem to get it to work with the new 8 GB flash drive. Anyone have a link for step-by-step instructions?

Danielky:

You should be able to do this to the 8gb USB drive by just having the 8gb drive in place when you boot to either a live Ubuntu CD or to the ALTERNATE Ubuntu CD and then just install Ubuntu to the USB device just like you would any other drive device.  I would recommend using the ALTERNATE to do this and also I would recommend that you as a safety measure unplug the hard drive(s) of your machine before doing this.  Of course, you want to make your USB flash drive the bootable drive just after your CD-Rom bootable drive in BIOS.

I tried this recently with a 2gb USB drive and it worked fine except after I got it installed and then when I tried to download the available updates for Ubuntu, the 2gb USB drive just was not big enough and I ran out of space.  But with an 8gb USB I would think you should be good to go.  As soon as I can find me the proper 8 or 16gb USB, I am going to give it another shot.

Good luck.

---

### Post by danielky on 2009-02-26
I used UNetbootin with the Ubuntu Live CD as the Source (so I wouldn't have to download the files on my 768kbps DL connection) and the 8 GB USB Flash Drive as the target. Ubuntu would then boot from the 8 GB flash drive but it did not have persistence. So, I booted from the Live CD and used System, Administration, Create a USB startup disk to reinstall Ubuntu to the flash drive. My newbie mind was thinking that maybe UNetbootin fixed the booting part and reinstalling could get the persistence feature working. The 8 GB flash drive is 7.5 GB formatted - 0.7 GB for base Ubuntu leaves about 6.8 GB. When asked how much space to leave for settings and documents, I divided that in half and said 3.4 GB. I know I'll have to update Ubuntu and I'm not sure if those updates are stored in the "settings and documents" area or a separate place. Anyway. it's booting from the flash drive and it has persistence. Although, I'd love to ditch Windows XP and use Ubuntu solely. I'm a long way off from that point. But, this will allow me to ease into Ubuntu and who knows, maybe get rid of my Newbie Linux status.

---

### Post by danielky on 2009-02-26
As soon as I can find me the proper 8 or 16gb USB, I am going to give it another shot.

Good luck.[/QUOTE]

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227332](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227332)

That's the one I just bought. $18 and free shipping for 8 GB. I thought it was a good deal. Now I'll wait for the price on the 32 GB flash drives to fall :)

---

### Post by wpshooter on 2009-02-26
Danielky:

I am not sure if this is what you were taking about when you were referring to things being stored in documents and settings but in Ubuntu your partitions for Ubuntu should basically go:  / = root for O/S, /home = for users settings, storage, etc.,etc. & /swap for swap, comparable to page file.

According to what I have read on here it is fairly important to make sure that you have a swap partition on a USB device especially, something to do with possibly extending the life of your USB device.

Thanks.

---

