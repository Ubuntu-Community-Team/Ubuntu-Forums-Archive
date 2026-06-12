---
title: "Booting USB without BIOS settings?"
date: 2010-09-06
forum: Hardware
---

### Post by I am Raf on 2010-09-06
Hey guys!
I found an old laptop in my basement, and i wanted to install ubuntu on it, so I took my live cd and tried to run it, but the motor in the disk drive was broken :(

So I tried booting off a USB, but I wasn't able to. The BIOS settings wouldn't allow me to D:<

Do any of you know how I could boot off a usb without changing the BIOS settings?

Thanks in advance :D

tl;dr I want to run ubuntu, CD drive is broken, and BIOS wont let me boot of a usb.

---

### Post by coffeecat on 2010-09-06
As far as I know, there would be no way of booting from USB if the BIOS does not allow this. It's the BIOS that controls the hardware before the OS loads - you can't get around that. Since this is an old laptop, I'm not surprised there's no setting for booting from USB. USB booting has only been possible in BIOS's in the last few years.

However - unless someone does know of a way to get around this BIOS limitation - there is a possible solution. You could take out the hard drive, put it in a USB enclosure and use another machine to install Ubuntu to the drive. You'd have to be careful to install grub to the MBR of the correct drive, otherwise you might make the host machine unbootable! The only drawback is that you need a USB enclosure that takes 2.5 inch drives with an older IDE (PATA) connector. They are easily bought, but that might be an expense you wouldn't want.

The other possible problem is that the hardware in your old laptop might not be Linux friendly, and you would only discover this after you have put the drive back in and tried to boot up.

---

### Post by hsoulen on 2010-09-06
Hi There,

Well you could always check with the manufacturer of the laptop to see if they have a newer BIOS that supports it, otherwise:


[LIST=1]
[*]Does it have a floppy drive? If so you can create a boot floppy (Linux or DOS) with some USB drivers and use that to mount your USB Key/drive
[*]You can always pull the drive and either put it in another laptop to install or use an external IDE/SATA or USB to "slave" it to another computer
[/LIST]
Failing all of this, I am out of ideas.

Cheers,

Hank

---

### Post by I am Raf on 2010-09-06
Thanks everyone :)

---

