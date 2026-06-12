---
title: "Kodak EasyShare C330"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by bsharitt on 2005-12-12
I've got a Kodak EasyShare C330 camera(no dock) trying to get pictures off of it via the USB cable. It detects it as a "USB PTP Class Camera", which technically should work, since I belive PTP is the protocol the camera uses, but the problem is that it can't see any pictures on the camera. I've tried on gtkam, Digikam, gPhoto2(the command line interface), the GIMP, and Camera.app, and got the samething(not surprising since they all use libgphoto2). Has anyone had a similar experiance and got it too work?

This would all be a non-issue if Ubuntu could use the Texas Intruments card reader on my Gateway laptop, but I'm afraid the drivers for that are even farther behind those of the camera.

---

### Post by john_c on 2005-12-13
I have a Kodak easyshare cx7330 which I also believe operates as a PTP device.  It works by opening gthumb and importing from that application.  Camera has to be plugged in and turned on before you try to import and it takes a few seconds to recognize the camera.

I am using Hoary but as I recall it worked with Warty also.

Good Luck,

John_c

---

### Post by bsharitt on 2005-12-13
[QUOTE=john_c]I have a Kodak easyshare cx7330 which I also believe operates as a PTP device.  It works by opening gthumb and importing from that application.  Camera has to be plugged in and turned on before you try to import and it takes a few seconds to recognize the camera.

I am using Hoary but as I recall it worked with Warty also.

Good Luck,

John_c[/QUOTE]

No luck there. gthumb also uses gphoto to import from cameras.

---

### Post by bsharitt on 2005-12-13
A bit of an update. It looks like I can pull pictures from the internal memory, but not the memory card. Obviously, that's not much of a fix since the internal memory is limited to 16 MB.

---

### Post by wolovids on 2006-02-25
[QUOTE=bsharitt]I've got a Kodak EasyShare C330 camera(no dock) trying to get pictures off of it via the USB cable. It detects it as a "USB PTP Class Camera", which technically should work, since I belive PTP is the protocol the camera uses, but the problem is that it can't see any pictures on the camera. I've tried on gtkam, Digikam, gPhoto2(the command line interface), the GIMP, and Camera.app, and got the samething(not surprising since they all use libgphoto2). Has anyone had a similar experiance and got it too work?

This would all be a non-issue if Ubuntu could use the Texas Intruments card reader on my Gateway laptop, but I'm afraid the drivers for that are even farther behind those of the camera.[/QUOTE]Urgh, I am using Dapper and I am afraid that I am having the same issues with a Kodak C330.  I have filed the following [bug]("https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/32038") on the problem.

---

### Post by obiwan on 2006-03-17
the same here. I have the EasyShare C300 and it works perfectly w/o the memory card. When the card is in the camera it gives this error: "PTP Protocol error, data expected".

I'm using dapper

---

### Post by hoodwink on 2006-03-18
Don't know about these cameras, but my Easy Share LS443 works fine with digikam on Dapper.

---

### Post by landazuria on 2006-03-20
I had the same problem with my Kodak C330 in Dapper till I made my first import in XP with the kodak software. Now I can use digiKam in Dapper succcesfully.

---

### Post by ricardisimo on 2007-12-31
I think that's a temporary fix... I can only work with the photos on my Kodak EasyShare 310 that I had previously viewed and downloaded via XP (which is no longer an option for me). All of the subsequent pictures I've taken on the camera raise the PTP error mentioned above. Elsewhere it mentions downgrading libgphoto to version 2.2 as a fix, but the Fesity repositories no longer offer this as an option. Why would a potential fix be removed from the repos?

---

### Post by ricardisimo on 2008-01-22
It appears that this problem isn't going away anytime soon. In the meantime, is there a way for me to manually mount the camera as a USB mass-storage device, instead of PTP? Thanks.

---

