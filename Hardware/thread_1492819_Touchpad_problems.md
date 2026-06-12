---
title: "Touchpad problems"
date: 2010-05-25
forum: Hardware
---

### Post by pollyrobin on 2010-05-25
Hello

I am having problems with the touchpad on my laptop.
It is working like it should work but if i want to change my setting its coming up with an error ( because while typing me mouse flys all over the place) so i would like to turn it of while typing or something like that. But the main problem is when i am trying to get to the touchpad configuration it keeps saying the famous:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I looked on alot of different sites but i just can't get it working.

I am working on ubuntu 10.04 at the moment but had the same problem in ubuntu 9.10

this would be the laptop i am using:

Asus N61VG-JX062V, Intel Core2 Duo T6600 (2.2GHz),16" HD TFT (1366x768,  Color-Shine), Web Camera 1.3M,  NVIDIA GeForce GT 220M, 1GB dedicated  graphics memory, 500GB (5400rpm), 4096MB (2048x2) DDRII 800 RAM, DVD  Super Multi Dual Layer, 64bit Windows 7 Home Premium, 802.11 BGN,  Numeric Keyapd, Finger Print, HDMI, E-SATA,  Bluetooth, Express  gate,Express card , 2 year global, Asus N61VG-JX062V

And this would be my Xorg.conf File ( and in my opinion way to empty) but that is how i found it the first time i tried editing it:


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Load     "synaptics"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
 

If anyone around could help me solve this problem. It would be really appreciated.

Greets Robin.

---

### Post by pollyrobin on 2010-06-03
bump

---

### Post by John Bean on 2010-06-03
Can't you just go to System->Preferences->Mouse and check the option on the "Touchpad" tab that says "Disable touchpad while typing"?

Works for me ;-)

---

### Post by pollyrobin on 2010-06-04
The problem is i dont have the Tab "touchepad" because i cant open the configuration for the touchpad:P

---

### Post by Jonsan on 2010-06-04
I have the same problem with the touchpad reversing directions.   According to another board, this happens when you put it into standby or  hibernation, and can be corrected with rebooting.  However, that  doesn't work for me.  I'm STUCK STUCK STUCK and very unhappy.  If you  hear of anything, please let me know.

---

### Post by pollyrobin on 2010-06-09
Sure Np will do that but it doesn't look like im getting any response on how to solve this problem :(

---

### Post by Professor IllDog43 on 2010-06-11
This might help you [http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/](http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/)

---

### Post by pollyrobin on 2010-06-15
Thanks alot i will look into that in a couple of days if im not busy thanks for posting the link.

---

