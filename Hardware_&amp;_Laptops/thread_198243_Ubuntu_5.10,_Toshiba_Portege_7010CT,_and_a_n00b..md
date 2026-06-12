---
title: "Ubuntu 5.10, Toshiba Portege 7010CT, and a n00b."
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by bl@ckm@ge987 on 2006-06-16
Hi, I've just made the change from Windows 98SE to Ubuntu 5.10. I'm using a Toshiba Portege 7010CT, 96MB RAM, 4GB HDD, and a lot of problems.
First of all, I know NOTHING of Linux, so I need simple and effective help.

First, no sound, I saw a thread covering this issue, but I understood nada.

Second, my resolution won't go above 640 x 480, and the text and icons are very jagged, not smooth.

I really would like help, Linux looks like a very nice OS, and I would hate not to be able to use its full potential.

Thanks.

---

### Post by x64Jimbo on 2006-06-17
As much as I love Ubuntu and love advocating it to newbies, your machine could be a little too old for it. Ubuntu is designed to be small enough to download for the average Joe, and that often means phasing out support for older hardware. Sad, but true. However, I have an idea. You should look into some of the LiveCDs that can be installed to hard disk. I have been running a hard disk installation of Kanotix for about two years now with a lot of success. It's very well supported and widely used. If you want to save on hard disk space, you might want to look into Slax, which is a LiveCD that is very concentrated on certain kinds of computing (media, windows compatibility, etc) 
The best part about LiveCDs is you can give them a test drive before you decide if you like them or not.

---

### Post by ltmon on 2006-06-17
Hi,

A couple of quick questions:

Do you know what graphics chipset you are using (Intel, ATI, Nvidia)?
Do you know what sound chipset you are using?

Cheers,

L.

---

### Post by bl@ckm@ge987 on 2006-06-17
[QUOTE=ltmon]Hi,

A couple of quick questions:

Do you know what graphics chipset you are using (Intel, ATI, Nvidia)?
Do you know what sound chipset you are using?

Cheers,

L.[/QUOTE]

Sadly, no. I read about other guys on the forum having these problems, and they knew what sound chipset they used. I'll try to find them.

edit: video: 	 NeoMagic (2200) w/256bit Dana Bus Width
       sound: Yamaha 3D OPL3-SA3

This page has my laptop down to a tee:
[http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAP701](http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAP701)

---

### Post by ltmon on 2006-06-17
Wow, that is some funky harware.

Unfortunately none of it is stuff that I have any experience or knowledge of.  I wouldn't even know what display drivers are used for the NeoMagic.

Well google told me the "nm2160" driver is correct for this.  The only thing I can suggest is to do a terminal command:
```

sudo dpkg-reconfigure xserver-xorg

```
This will guide you through the setup of your graphics card.  Make sure you choose the "nm2160" driver when it asks, and also make sure 800x600 is available when it asks (I think that's the maximum on this particular laptop).  Hopefully that particular driver is still supplied with X.

The best reference I could find for this laptop on linux is: [http://www.arcetri.astro.it/~lfini/LinuxLaptops/Toshiba.Portege7010/](http://www.arcetri.astro.it/~lfini/LinuxLaptops/Toshiba.Portege7010/)

Unfortunately this is from an installation of RedHat 5.2 which is pre-2000 at very least.  Most of the information is going to be fairly wrong by now.

Maybe someone else here knows....

L.

---

### Post by bl@ckm@ge987 on 2006-06-18
Where do I input this?

---

