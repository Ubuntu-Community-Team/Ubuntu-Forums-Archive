---
title: "What is possible with the ATI-drivers under Ubuntu ?? Dualview / 3D / TV-out"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by AndreasMeier on 2005-06-19
Hi guys,

I've got big questions regarding my ATI9600 card installed on my Kubuntu Hoary system.
With this ([LINK](http://www.ubuntuusers.de/wiki/treiber:grafik:ati_treiber_installieren)) howto (in german), I have installed the ATI-drivers I have found in synaptic.
This is the xorg-driver-fglrx, installed with kernel 2.6.10-5 and the restricted modules, sources, headers etc.
Works just fine and gives me 3D accelleration.

But now I'm looking around to use the whole features of the ATI9600, which is Dualview and TV-out.

I tried a lot with the config of xorg, but all failed.

And now my questions, I just need a clear "yes" or "no", if someone got this working :

Is it working to configure ...
1.) Xinerama/Dualview with activated "fglrx" drivers in the xorg.conf ??
2.) Xinerama/Dualview with activated "fglrx" drivers AND 3D accelleration ??
3.) TV-out on a second x-server with activated "fglrx" drivers ??
4.) Dualscreen on a first x-server, and TV-out on a second x-server, both with activated "fglrx" drivers ??

As you can see, all questions are trying to bring light to what is possible with the "fglrx" driver and with each question I try to implement more features in one config.

My aim is to have one xorg.conf with 2 x-servers running, one for Dualview / Xinerama with activated 3D accelleration on both monitors / screens, and a second one for tv-out, which should throw videos by mplayer to my tv screen.

My post here has the aim to clear the quest what is possible as I said before.
Hope I'm not hunting a ghost and try something which is not working in general, if you know what I mean  ;-) 

Thanks in advance,
regards,
Andreas

---

### Post by Gezzer on 2005-06-19
ATI have released new drivers for there GPU cards with a GUI interface for linux ...

[http://tinyurl.com/a52zy](http://tinyurl.com/a52zy)

---

### Post by AndreasMeier on 2005-06-19
Right now I have version 8.8.25 installed from ubuntu apt-source.

Will the new driver works better for my aims ?

---

### Post by MuLLeR on 2005-06-19
You can make your tv-out, or dualview work, if u use fglrxconfig in console, but if you don't want you X-Server startup with an error follow these steps:
1. Make a backup copy of xorg.conf.
2. Type fglrxconfig in console and answer the questions (here you can setup TV-OUT and/or DUALVIEW).
3. Make a copy of the newly created xorg.conf.
4. Replace the current xorg.conf with the backup copy from 1.
5. Open the xorg.conf and replace everything between
(
Section "Device"
...
EndSection
) from xorg.conf file from 3.

SAMPLE:
#==============
Section "Device"
Identifier"ATI Technologies, Inc. Radeon 9600 (R350)"
Driver"fglrx"
BusID"PCI:1:0:0"
# here goes custom driver configs
  Option"backingstore" "true"
  Option"UseInternalAGPGART" "no"
  Option "VideoOverlay" "on"
  Option "OpenGLOverlay" "off"
EndSection
#==============

P.S.
hope i made my self clear if you don't understand something, feel free to ask,
P.P.S.
man, type so sloppy...

---

### Post by AndreasMeier on 2005-06-19
No no, just perfect. I have tried fglrxconfig with my version of the driver which is 8.8.25.
With this driver he created me only a XF86Config-4 file, which I try to adapt tomorrow evening to my xorg.conf.
Hopefully it will work.
Both of the config files looks very similar :-) so I will see.

Next days I will try the new version of the driver on my ubuntu test system.
I'm not willing to take any risk of testing a new installer on my work system  [-X 
and keep you informed how it works or ask if I have questions.

Thanks for now and kind regards,
Andreas

---

### Post by mediaservant on 2006-02-01
any update on this?  I'm to this point right now with breezy, etc.

---

