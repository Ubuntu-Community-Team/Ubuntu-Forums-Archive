---
title: "Asus Z53e"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by aspie on 2007-12-23
I have just got a new ASUS Z53E laptop from Media Markt in Spain.  It appears to be a ASUS F3 as far as I can tell, I not sure why the different name.  Anyway, I thought I should post my experiences of getting it working OK with Ubuntu.  Maybe it will help someone else.

**Brief system specs:**
[INDENT][LIST]
[*]Intel Core 2 Duo T5500
[*]2GB RAM
[*]160GB SATA HDD
[*]DVDRW
[*]Intel X3100 graphics
[*]Intel 3945ABG wireless 
[*]SD card reader
[*]USB2.0 UVC 1.3 megapixel webcam
[*]Firewire port (untested as yet)
[/LIST][/INDENT]


Installation from the LiveCD failed, so I tried the Gutsy AMD64 Alternative disk.  This worked easily, with no problems at all. The wireless card worked with restricted drivers and I installed WICD to make life with wireless easier.

The SD card reader worked without any config. needed.

The graphics card is seen in hardware information as a "Mobile GM965/GL960", to get desktop effects running I needed to do this:
```
$ mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

I tested the webcam with Exiga, I selected V4L2 as the video plugin, and it worked fine!

I had a problem with the wireless networking after hibernation.  This seems to have fixed the problem:
> **tommie74 said:**
> I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Finally, I installed the Skype webcam beta, and this seems to have problems with the webcam.  Initially I thought that this was related to Compiz, but as Exiga seems to work OK I guess I need to wait for Skype to improve.
[B]
EDIT
Well it appears that I was a bit to quick off the mark with the wireless hibernate problem.  It still does not work correctly :([/B]

---

### Post by aspie on 2007-12-23
I have just installed the XGL Xserver and now I have my Skype working with the webcam.  

So that looks like it's all working OK.  I am now gonna setup Mac4Lin :)

---

