---
title: "What does everyone think of the Dell Inspiron 530N"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by Kujen on 2007-07-28
I'm in the market for a new pc, and I was looking at the Dells with Ubuntu preinstalled. The Inspiron doesn't look like a bad computer, but I have one main question. Are you able to replace the harddrives and video card on it? Obviously in the future I'd want a better video card, and I have a harddrive right now I'd wanna put in it. (I'd like to get a better computer than that, but I'm stretched thin on money. And I don't feel like going through the hassle of building right now.)

---

### Post by PatheticMoFo on 2007-07-28
I bought the 530N for my mother, and I noticed a few problems with it I was able to fix, but not without a lot of trouble. I don't know if everyone who bought this computer got this problem, but almost everything in the lspci output was an "uknown device". 

Also, with the default integrated Intel card, the 3D acceleration did NOT work out of the box, I had to do some searching in the Ubuntu Forums before I found out that the G33 chipset drivers weren't working well in Fiesty and you need to use a backport package of xserver-xorg-video-intel for it to work. The sound is also way too low, and nothing on the forums helped me out for this.

As for expandability, I'm not sure, but it looks like it has a PCI Express-16 slot in there? Don't quote me on that, but I just don't see anywhere else where this is listed. The hard drive is a SATA drive, the RAM is DDR2 667 (PC2 5300). The Hard drive is mounted on its side, and its close to the inner wall of the side of the computer, I haven't looked if you can put more than one drive in there. There is also by default one more place to put in an extra optical drive. Hope that gave you some info.

---

### Post by Kujen on 2007-07-28
intel video? The site says it comes with an nvidia card...?

 Video Cards  	 128MB NVIDIA GeForce 8300GS

---

### Post by PatheticMoFo on 2007-07-28
Ah, they changed it. I ordered it around July 8 or so, a little after it was introduced with Ubuntu. Sorry, didn't notice that (they must have noticed the problems with the intel chipset.) That's weird, cause their [wiki]("http://linux.dell.com/wiki/index.php/Clients/Products/Dimension_E530n/lspci") still says that the video card is intel, in their supposed lspci output. 

Hey, then nevermind my comment, they probably fixed up the issues they had when I got it.

---

### Post by Kujen on 2007-07-28
Ah okay, no problem. :D So with that video card, what do you think about it? I'm trying to find some opinions before ordering. (Really tempted to order right now, but common sense tells me to wait.)

---

### Post by HeavyAl on 2007-07-28
I just ordered this model for my dad about mid month and it came in ealier this week.

I can confirm that none of the hardware is reporting correctly, though if you didn't know what you were looking at it wouldn't matter because the system does essentially work out of the box.

One really irritating problem I have with the machine though is that the nVidia card is stuck at 1024x768 and I know for a fact this card can go higher, and since this is a 19-inch wide-screen flat-panel I'm thinking it can definitely handle a higher res!

Ok, video aside, my dad appears to be loving it. Everything has pretty much just worked and since most everyone is reliant on the Internet for their daily wanderings anyway this machine is perfect.

---

### Post by wvmac on 2007-07-28
i have the 530n with the nvidia 8300gs card and a 19" widescreen monitor as well. Same problem with the initial screen resolution.  I had to use envy to install the nvidia drivers and now the resolution is working at the max 1440x900.  however the login screen, gdm, is not set at the correct resolution and only fills up 2/3 of my screen.  also the ethernet jack went "invisible" and I used a patch that is mentioned somewhere in this forum to fix it. Once you have the nvidia driver the desktop effects work great. overall I like the  machine.

---

### Post by mbaker on 2007-08-24
Which nVidia driver version did you install using Envy?  The 1.0.9755 version that's included in the Ubuntu repository doesn't work.  Actually, lspci shows it as an "unknown device", and the X-server complains that it can't read the GPU name when I try to load the driver.

I bought a PNY 8500GT card from Best Buy, and it gave me the same error.

I took the 6800XT card out of a working Ubuntu system and installed it in the 530N, and it worked with the standard driver just fine.  lspci also shows the correct GPU name.

Did you use the latest version (100.14.11)?  

Thanks,
Mark

---

### Post by martalli on 2007-10-09
We have an Inspiron 530n purchased during the summer...just before they upgraded to the 8xxx series video cards.  Our 530n has four SATA headers.  There is space for a second hard drive, and also space for a second 5.25" device (basically for a CD/DVD drive).  You could put a second hard drive in it no problem, and maybe even a third with the proper 5.25" -> 3.5" rails.  The computer was advertised as only being able to handle 2 HD...I don't see why but maybe the BIOS won't accept more than two HD...

Upgrading from feisty to gutsy, our ethernet nic disappeared.  I see a fix listed elsewhere ([http://ubuntuforums.org/showthread.php?t=540926](http://ubuntuforums.org/showthread.php?t=540926)), so I am going to try this and see if we get the ethernet back.

Otherwise, we have been perfectly happy with the 530n.

---

