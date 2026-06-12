---
title: "kubuntu from usb stick"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Ajn on 2009-02-08
I've been trying to install linux from usb stick, and I'm almost there. Almost.

Distro I'm intending to use is kubuntu 8.10 alternate-amd64. Alternate because I have a software RAID0 installed. I followed instructions from [_helpful post_]("http://ubuntuforums.org/showpost.php?p=4404569&postcount=37") and downloaded required files initrd.gz and vmlinuz from [_here_]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-amd64/current/images/hd-media/").

I end up with error during recognizing the sata RAID device(s). They just are unable to use and installer stops. Funny thing, trying to install kubuntu my RAID almost flipped and it was hard to get windows boot (=to get RAID working again).

Anyone know why?
And about the instructions, in some you are asked to rename isolinux.cfg AND isolinux dir to syslinux.cfg and syslinux dir. (This has something to do with "copy the contents of the 'isolinux' dir on the install iso into the root dir on the usb stick" ?)

Stick formatted to FAT32 under vista and syslinux.exe created ldlinux.sys in the root of the stick.

edit: And oh, I forgot to ask about the "setting the boot flag", what it is? I was able to boot from the stick so I don't need to worry about the boot flag?

---

### Post by Ajn on 2009-02-08
I tried renaming isolinux.bin to syslinux.bin (from isolinux dir from .iso) but no effect to the process. Still I can't see my raid.

And it's interesting that every time I try to recognize the raid installed, it goes unfunctional and I have to boot my computer and tune boot settings back to raid. It doesn't destroy any files but it just is unusable after I try to see it with kubuntu installer.

What's wrong?

---

### Post by zerofool2005 on 2009-02-09
Try useing unetbootin to copy the iso to the usb and install the bootloader

---

### Post by Ajn on 2009-02-09
> **zerofool2005 said:**
> Try useing unetbootin to copy the iso to the usb and install the bootloader

I'll try unetbootin, but how's bootloader supposed to be installed (to the stick?)?

Thanks for reply.

---

### Post by beast-usa on 2009-02-11
This should work
[http://www.pendrivelinux.com/usb-kubuntu-810-install-via-usb-creator/](http://www.pendrivelinux.com/usb-kubuntu-810-install-via-usb-creator/)

I used something else and it boots then asks for username & password that I never set up?

---

### Post by beast-usa on 2009-02-11
I used this inside Vista boots fine just have no idea what the username and password are LOL
[http://www.pendrivelinux.com/usb-kubuntu-810-persistent-install-using-windows/](http://www.pendrivelinux.com/usb-kubuntu-810-persistent-install-using-windows/)

---

### Post by Ajn on 2009-02-13
I think [_this_]("http://www.pendrivelinux.com/usb-kubuntu-810-persistent-install-using-windows/") might work better, because I don't have cd/dvd-burner right now. I'll give this a try when I got time.

NONONO blah this guide was just to install kubuntu to usb stick, not istall from it..my bad :)

---

