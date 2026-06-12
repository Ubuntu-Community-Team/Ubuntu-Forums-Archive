---
title: "Ridiculous problem.. !"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by mooshymama on 2008-12-07
Okay i'm going to try and make this as short and to the point as possible..

I have a crappy old toshiba laptop that doesnt have a cd drive and no usb boot support.

I'm trying to install ubuntu on this laptop!

I can remove the hard drive from it and connect it to my other machine via USB (so i have read write access to it basically) and I've currently used unetbootin to put the ubuntu install on it using this method as well as back everything off it.

I still can't boot into the ubuntu installer though and i'm guessing its got something to do with the MBR or something. Not really sure.

Can someone please help me get into the installer from here? If i'm totally on the wrong track, feel free to put me on the right one :P

Thank you!

---

### Post by oilchangeguy on 2008-12-07
please provide the specs of the computer. cpu speed, amount of ram, and hard drive size.

---

### Post by albinootje on 2008-12-07
In the past i've used a small converter from 2.5" to 3.5" IDE, so that
the laptop-disk could be attached to a normal IDE-cable in a desktop-machine. That converter did cost about 4 euros some years ago.
But of course you can temporarily put the laptop-disk in another old
laptop which does have usb-ports or a cdrom-drive.
The last approach won't work with newer laptops having SATA-disks.
You might want to try Xubuntu on such an ancient laptop, or some other
more lightweight Linux-distribution.

---

### Post by mooshymama on 2008-12-07
The laptop is a Toshiba Satellite A55 S3061, 1gb ram, 80gb hard disk.

I'm going to try using another laptop to install ubuntu on the drive today.. i'll let you know how it goes.

---

### Post by karamu on 2008-12-08
I had a pretty similar issue- a laptop with no CDROM which in the BIOS said that it can boot from USB but didn't recognise a USB CDROm when I tried to boot from it. 

I connected the computer via USB to my desktop and removed the connection to the desktop's HDD (so that the machine thought the USB drive was the only drive- if I left both drives hooked up it confused the GRUB boot list and I am not confident editing GRUB). 

The install ran fine and then I disconnected the laptop and booted- it boots up into Xubuntu. However it ran really slowly- and I had display issues- it was only at 800 resolution when the screen supported 1084- there were black borders. 

Using the display config utility (with gksudo command) I was able to force the display to the correct size. Strangely when I enabled window comositing it ran quicker, but still sluggishly. 

That's all I managed to do- I only use the machine for office apps so it does the job OK.... not well, it isn't quick- I guess I still have unresolved video issues but I basically gave up at that point.

Don't know if that helps but I would say you prob can get Ubuntu in by installing with a diff machine but it may not run properly once you're done.

---

