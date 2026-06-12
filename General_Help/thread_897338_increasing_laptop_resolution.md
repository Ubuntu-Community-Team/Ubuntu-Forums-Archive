---
title: "increasing laptop resolution"
date: 2008-08-22
forum: General Help
---

### Post by xecure on 2008-08-22
my laptop resolution right now is 1280 x 800, and i was wondering if it was possible to  1680 x 1050. I was reading somewhere that it can be done with the installation of a video driver, but I'm not sure what my video card is (i suspect it is an intel video card)

can someone walk me through this?

---

### Post by dagoth_pie on 2008-08-22
Hi there,
I'm no proffessional but I've had a lot of fun mucking round with graphics drivers lately, first up, what type of graphics card do you have, and if its nvidia or ati do you have the restricted drivers enabled?

---

### Post by dagoth_pie on 2008-08-22
ok my bad, not reading properly, to find out what graphics card youve got, run
lspci
then post the result here, im assuming itll still work the way that it does on a desktop pc

---

### Post by xecure on 2008-08-22
lspci out puts: ```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by dagoth_pie on 2008-08-22
well you were right it is an intel, i know that theres a hack for some intel cards that lets them have higher resolutions, and also there was a way of getting into a resolution setting in recovery mode which let me make an older system run 1024x800 when the best it would do is was 800x600, i know ive got it written down somewhere, ill try find it and get back to you

---

### Post by xecure on 2008-08-22
thanks alot, i appreciate it

---

### Post by dagoth_pie on 2008-08-22
so far i havent found the command, i did find one but that left me reinstalling my video drivers, ive never used this but its the hack i mentioned earlier for intel cards, ill keep looking for the other command though, get back to me as to weather or not that works, good luck

sudo apt-get install 915resolution

---

### Post by xecure on 2008-08-22
this is what terminal shows for that:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
915resolution is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

---

### Post by dagoth_pie on 2008-08-22
[http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html)

heres a readme for it, just skip the install part of it, hopefully its as straightforward to set up as it looks

---

### Post by mcduck on 2008-08-22
Actually the most important thing here would be the native resolutio of your display. That defines what resolution you shoould be using, and usually using higher resolution isn't even possible. Even if it is, you'll only get worse picture quality as it needs to be scaled to the displays native resolution.

If the LCD panel has 1280x800 pixels, that's what you'll get, no matter what resoltution you configure your graphics card to use.

Another thing is that the default drivers should work fine for Intel graphics card, the trick of the correct resolution by installing a different driver from the default one applies to soem Ati & nVidia cards only. If your resolution is not correct the only thing you need to do is to install the "915resolution"-package.

If you are not sure what would be the right resolution for your display youc an of course post the model here and we'll check it for you.

---

### Post by dagoth_pie on 2008-08-22
hmm, good point, i didnt even think of the screen as a limitation, although i did do a lil bit of research and find that the windows xp drivers for that particular chipset sometimes wouldnt allow a better resolution, all i know about intel graphics drivers on linux is really about that 915 hack thing, which i figured might be able to help out, i guess we just wait for a responce and fine out...

---

### Post by xecure on 2008-08-22
> **mcduck said:**
> Actually the most important thing here would be the native resolutio of your display. That defines what resolution you shoould be using, and usually using higher resolution isn't even possible. Even if it is, you'll only get worse picture quality as it needs to be scaled to the displays native resolution.

If the LCD panel has 1280x800 pixels, that's what you'll get, no matter what resoltution you configure your graphics card to use.

Another thing is that the default drivers should work fine for Intel graphics card, the trick of the correct resolution by installing a different driver from the default one applies to soem Ati & nVidia cards only. If your resolution is not correct the only thing you need to do is to install the "915resolution"-package.

If you are not sure what would be the right resolution for your display youc an of course post the model here and we'll check it for you.

I'm pretty sure i operated under a higher resolution on vista on this same machine, and as for the model of my display I'm not sure what it is, how can i check? (i run a dell inspiron 6400 if that helps at all...)

@dagoth_pie
i tried doing the stuff on the link you posted but my Xorg wouldn't restart so i manually logged off and tried to log back on and my Xorg wasn't working properly so i rebooted under recovery mode and fixed it there.

---

### Post by mb_webguy on 2008-08-22
I looked up the specifications on the Inspiron 6400, and most of the sources I found agreed that the native screen resolution is 1280x800 (though one said 1680x1050, though since it was the only one I found that used that figure, I think it's probably incorrect).  

So you're probably not going to get any better than that...

---

