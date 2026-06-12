---
title: "Install ubuntu - from Windows - to a USB connected HDD, without changing orig MBR"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by StephenBartlett on 2009-10-26
I have an <very> old laptop without a floppy or cd. It's HDD died, so I got a new one (blank - 2.5" ATA) and want to install Ubuntu.
 
<It has a network card, but it doesn't support PXE).
 
I took the HDD out of the laptop, and connected it to my desktop which is currently running XP (with Ubuntu 9.04 in a VM :-) ), via a USB->ATA/IDE HDD enclosure box. I can see the laptop HDD fine under Windows, and can create partitions, format, etc..... Call it drive L.
 
Now - what I want to do is make the laptop's HDD (drive L) bootable, and install Ubuntu, from within my Desktop's Windows. Then I'll take the laptop's HDD it back to the laptop, and voila - Ubuntu - right !?
 
I would normally forget Windows altogether, remove the Windows HDDs from my Desktop, boot right into a Ubuntu CD, and install Ubuntu on the L: drive, **but the Ubuntu install does not properly recognise the USB conncted drive**. It sees it, partitions it, but always quits after about 30%.
 
So - again - what I want to do is make the laptop's HDD (drive L) bootable, and install Ubuntu on it, from within Windows.
 
Is there a way to do what I am trying to do - especially without screwing up my exisitng MBR on my C drive ? 
 
First post. Thanks all.

---

### Post by mikewhatever on 2009-10-26
Check out the link below, the first guide seems to be somewhat close to what you want.
[http://www.pendrivelinux.com/category/install-to-usb-hard-drive/](http://www.pendrivelinux.com/category/install-to-usb-hard-drive/)

Why do you think the installer doesn't recognize the USB drive? Do you get any errors?

---

### Post by StephenBartlett on 2009-10-26
I actually tried the exact sequence listed in your reference myself before writing this post: specifically [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372) . 
 
Everything I did is identical to the description there, and Ubuntu does in fcat start loading the OS to the USB drive. However, after about 30% of the files are copied, I get an somewhat verbose (but non-educational) error essentially saying the installer can't write to the USB drive. Then the installer quits mid-install.  I will write down the exact message and post.
 
I've checked the drive for errors (there are none), and Windoze uses the entire HDD fine.....

---

### Post by StephenBartlett on 2009-10-26
BTW: That IS a good read. Thanks !

---

### Post by tommynz1975 on 2009-10-26
Just an thought from a daft harware point of view.

If all else fails are you able to get at the cd-rom connector on the lappy and hook the data lead from the desktops cd-rom drive? this may require an adapter so the lappy thinks it has a working cd-rom drive again??

---

### Post by StephenBartlett on 2009-10-28
Actually, this is an old laptop - and doesn't have a CDROM. It has a USB port (but can't be set to boot from it), and a PCMCIA card slot (which has a ethernet card in it).

What I actually did was take the HDD fom that laptop, put it in a newer laptop that DOES have a bootable CDROM, and installed Ubuntu on it that way. Then I moved the HDD back to the old laptop, made some adjustments, and it worked. Not elegent - but practical.....

Thanks for the suggetsions !

---

