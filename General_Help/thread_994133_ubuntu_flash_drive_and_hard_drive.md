---
title: "ubuntu flash drive and hard drive"
date: 2008-11-26
forum: General Help
---

### Post by TokenBad on 2008-11-26
I am looking at trying to put ubuntu on flash drive but have it access most of the data of ubuntu from a hard drive..so that I can just put in the flash drive to boot to ubuntu but then have it save all the data and stuff on my 400 gig drive...that I have partitioned into 2 250 gig partitions..is that even possible?

TokenBad

---

### Post by Titan8990 on 2008-11-26
Yes, you could install Ubuntu on the thumb drive and then have your internal HDD mount as your Home partition, or in another location if you would like.

---

### Post by TokenBad on 2008-11-26
but with the home dir..isn't there also alot more stuff that gets saved in other areas..and not just in home dir..for example your video drivers, or updates you download for ubuntu and so forth?  I mean for example if I had a 1 gig flash drive and tried to do updates and stuff..all that would be saved to the 1 gig drive and in 1 update could fill the drive?

TokenBad

---

### Post by jimv on 2008-11-26
Ubuntu won't even install on a 1 gig drive.  You'll want to get at least a 4 gig thumb drive, and with the Black Friday sales coming up, you could probably land a 16 or even 32 gig thumbdrive for pretty cheap.

Most updates are <10 mb, though kernel upgrades are ~100mb...but it shouldn't be a problem.

Make sure when you're doing the installation that on the last step, you click the Advanced button and set GRUB to be installed on the thumbdrive.

---

### Post by caljohnsmith on 2008-11-26
What exactly are you trying to accomplish? If you want most of Ubuntu's data to reside on the HDD, then how about installing Ubuntu to your HDD, but then you could install Grub to your USB drive so that Ubuntu only boots when you put in your USB drive? Is that maybe what you are looking for? If so, let me know and I can help you set that up if you want.

---

### Post by TokenBad on 2008-11-26
> **caljohnsmith said:**
> What exactly are you trying to accomplish? If you want most of Ubuntu's data to reside on the HDD, then how about installing Ubuntu to your HDD, but then you could install Grub to your USB drive so that Ubuntu only boots when you put in your USB drive? Is that maybe what you are looking for? If so, let me know and I can help you set that up if you want.

Yes that is exactly what I want..only want to boot into ubuntu if the usb drive..so if not in there..it will boot straight to windows...or leave the dual boot menu for my windows alone...

TokenBad

---

### Post by caljohnsmith on 2008-11-26
OK, go ahead and install Ubuntu to your Windows HDD, but in the last step of the installation process click on the "advanced" button, and specify "/dev/sdaX" as the location to install Grub to, where sdaX is the Ubuntu partition (for example /dev/sda5). Once you are done installing, open a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
When you have your USB drive connected. We can work from there.

---

### Post by TokenBad on 2008-11-26
> **caljohnsmith said:**
> OK, go ahead and install Ubuntu to your Windows HDD, but in the last step of the installation process click on the "advanced" button, and specify "/dev/sdaX" as the location to install Grub to, where sdaX is the Ubuntu partition (for example /dev/sda5). Once you are done installing, open a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
When you have your USB drive connected. We can work from there.

ok you lost me at the part of installing grub to sdax...the ubuntu partition on my hard drive? or on the usb flash drive?

TokenBad

---

### Post by caljohnsmith on 2008-11-26
> **TokenBad said:**
> ok you lost me at the part of installing grub to sdax...the ubuntu partition on my hard drive? or on the usb flash drive?

TokenBad
sdaX would be the Ubuntu partition on your HDD. In other words, during the installation, your USB drive is not at all involved; you can even unplug it if you want. Once you have Ubuntu successfully installed to the HDD as I described, then I can give you instructions for installing Grub to the MBR (Master Boot Record) of your USB drive and have Grub point to Ubuntu on your HDD for its boot files. That way whenever you boot the USB drive, you will either get the Grub menu where you can choose to boot Ubuntu, or you can set it set so you automatically boot directly into Ubuntu.

---

### Post by TokenBad on 2008-11-26
> **caljohnsmith said:**
> sdaX would be the Ubuntu partition on your HDD. In other words, during the installation, your USB drive is not at all involved; you can even unplug it if you want. Once you have Ubuntu successfully installed to the HDD as I described, then I can give you instructions for installing Grub to the MBR (Master Boot Record) of your USB drive and have Grub point to Ubuntu on your HDD for its boot files. That way whenever you boot the USB drive, you will either get the Grub menu where you can choose to boot Ubuntu, or you can set it set so you automatically boot directly into Ubuntu.

But if I did a full install now with windows already on my pc wouldn't it try to install grub at the end of the install so it would boot into windows to?

TokenBad

---

### Post by caljohnsmith on 2008-11-26
> **TokenBad said:**
> But if I did a full install now with windows already on my pc wouldn't it try to install grub at the end of the install so it would boot into windows to?

TokenBad
If you follow the instructions I gave before about clicking the "advanced" button and changing Grub to be installed to the Ubuntu partition, and not the MBR, then you will be just fine. Only if you install Grub to the MBR will it take over the booting process on start up. If you instead install Grub to the Ubuntu partition as I described, when you reboot you will still boot directly into Windows since the MBR is not touched.

---

### Post by TokenBad on 2008-11-27
> **caljohnsmith said:**
> If you follow the instructions I gave before about clicking the "advanced" button and changing Grub to be installed to the Ubuntu partition, and not the MBR, then you will be just fine. Only if you install Grub to the MBR will it take over the booting process on start up. If you instead install Grub to the Ubuntu partition as I described, when you reboot you will still boot directly into Windows since the MBR is not touched.

oooooohhhhh...ok that is where I was confused...I understand now..ok..will do that..and let you know when done

TokenBad

---

### Post by TokenBad on 2008-11-27
> **caljohnsmith said:**
> If you follow the instructions I gave before about clicking the "advanced" button and changing Grub to be installed to the Ubuntu partition, and not the MBR, then you will be just fine. Only if you install Grub to the MBR will it take over the booting process on start up. If you instead install Grub to the Ubuntu partition as I described, when you reboot you will still boot directly into Windows since the MBR is not touched.

ok got the install going and its almost done..hope your still around.  But once the install is done..what should I do.

TokenBad

---

