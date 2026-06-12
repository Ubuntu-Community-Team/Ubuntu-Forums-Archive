---
title: "nVidia GeForce FX 5700LE... I'm exhausted"
date: 2009-04-30
forum: Hardware
---

### Post by ununpentium on 2009-04-30
Hi all!

+16 years of working with computers.... since I was 12... using MS-DOS on an old 286 16 MHz, 1 MB RAM...
Always made experiments with each kind of software and lots of hardware systems....

NEVER had a problem so hard like this!

I think it could be easier to build an artificial black hole rather than let Ubuntu see these Nvidia drivers!

After 2 days of hard fighting  with the gloves off,.... nothing! I'm exhausted.

I googled a lot... I installed each kind of compatible driver (v. 7x, 173,....) in each way (System-->Driver Hardware; Synaptic; Nvidia downloaded .run files installed with "sudo sh" from the console....; legacy drivers; with ENVY; etc.....), lots of times, more and more.... NOTHING!!!

This is the symptom:
The video performance is poor (of course), no 2D, neither 3D acceleration...

I install the nvidia drivers.... reboot: MONITOR BLACK! (dvi port of card).

After lots of attempts... I found that _sometimes_ the signal passes to the other port (VGA)! Thanks to an old 15" LCD VGA monitor...

I tried to invert the ports... to enable the DVI one again... (I wrote each thing in the xorg.config... also the Divine Comedy if possible....) nothing! Both monitors black....

But even if the problem was just a port-inversion, that was OK, since I have a scaler-converter VGA-to-DVI with digital processor: I could connect the 23" DVI monitor to the VGA port of the card through it... and work...

The problem is that the driver is not really installed! Also when I install it (in thousands and thousands of ways...), the VGA port resolution is freezed to 640x480, the nvidia card is not really recognized, the acceleration is always off...

Only a few times I believe that I was able to completely install the drivers and to ENABLE the acceleration: in that case both the monitors (and ports) are died! BLACK... BLACK... only BLACK...!

As Ubuntu enables the nvidia drivers, the svga card ceases to output any signal.... But the OS runs, I hear the sound, and I am able to blindly write user ID and password and log in!

It is an impassable barrier... no way... : the gates of the hell !!

I always restored the situation by the recovery console (last option: XFIX - auto rebuild graphic configuration): the situation always came back to not-accelerated graphic card, and 1920x1080 res.

Now, after all these attempts... it is unable to come back there too! Also if I use recovery console, it comes back to 1024x768 (of course not customizable, FREEZED, as usual; no more 1920x1080). This after a massive uninstall of things using Synaptic)

1) Any advice on how to enable nvidia drivers?

2) or, at least, any advice on how to restore the bulk driver but at 1920x1080 ?

Thank you!

PS: the black screen problem was from the first day.... with Ubuntu 8.10... now I updated to 9.04 (hoping in a bug fix...): THE SAME! I made all these latter attempts (2 days) with the 9.04.

---

### Post by garythegoth on 2009-04-30
> **ununpentium said:**
> Hi all!

+16 years of working with computers.... since I was 12... using MS-DOS on an old 286 16 MHz, 1 MB RAM...
Always made experiments with each kind of software and lots of hardware systems....

NEVER had a problem so hard like this!

I think it could be easier to build an artificial black hole rather than let Ubuntu see these Nvidia drivers!

After 2 days of hard fighting  with the gloves off,.... nothing! I'm exhausted.

I googled a lot... I installed each kind of compatible driver (v. 7x, 173,....) in each way (System-->Driver Hardware; Synaptic; Nvidia downloaded .run files installed with "sudo sh" from the console....; legacy drivers; with ENVY; etc.....), lots of times, more and more.... NOTHING!!!

This is the symptom:
The video performance is poor (of course), no 2D, neither 3D acceleration...

I install the nvidia drivers.... reboot: MONITOR BLACK! (dvi port of card).

After lots of attempts... I found that _sometimes_ the signal passes to the other port (VGA)! Thanks to an old 15" LCD VGA monitor...

I tried to invert the ports... to enable the DVI one again... (I wrote each thing in the xorg.config... also the Divine Comedy if possible....) nothing! Both monitors black....

But even if the problem was just a port-inversion, that was OK, since I have a scaler-converter VGA-to-DVI with digital processor: I could connect the 23" DVI monitor to the VGA port of the card through it... and work...

The problem is that the driver is not really installed! Also when I install it (in thousands and thousands of ways...), the VGA port resolution is freezed to 640x480, the nvidia card is not really recognized, the acceleration is always off...

Only a few times I believe that I was able to completely install the drivers and to ENABLE the acceleration: in that case both the monitors (and ports) are died! BLACK... BLACK... only BLACK...!

As Ubuntu enables the nvidia drivers, the svga card ceases to output any signal.... But the OS runs, I hear the sound, and I am able to blindly write user ID and password and log in!

It is an impassable barrier... no way... : the gates of the hell !!

I always restored the situation by the recovery console (last option: XFIX - auto rebuild graphic configuration): the situation always came back to not-accelerated graphic card, and 1920x1080 res.

Now, after all these attempts... it is unable to come back there too! Also if I use recovery console, it comes back to 1024x768 (of course not customizable, FREEZED, as usual; no more 1920x1080). This after a massive uninstall of things using Synaptic)

1) Any advice on how to enable nvidia drivers?

2) or, at least, any advice on how to restore the bulk driver but at 1920x1080 ?

Thank you!

PS: the black screen problem was from the first day.... with Ubuntu 8.10... now I updated to 9.04 (hoping in a bug fix...): THE SAME! I made all these latter attempts (2 days) with the 9.04.


Goto to your bios and change the AGP Aperture size around and reboot a few times. I dont know why but I had this issue with my old desktop with a 5700Ultra using 8.04. That fixed it. Let me know if it works for you as Ive never seen anyone else who had this same issue.

---

### Post by ununpentium on 2009-05-01
Thank you gary.
I tried with any aperture size, nothing! (from 4 to 256 MB). Always monitor BLACK and its power led flashing....


IMPORTANT NEWS:

since the monitor light flashing is an unsupported resolution-like symptom, I tried connecting another LCD DVI monitor, very big: an Apple 30".

SURPRISE!!!! The image appeared, stretched orizontally and replied 3 times in the screen....

So I made the reboot and the image become just one: but with a strange behaviour: the resolution was 1024x768 (I don't remember how I understood this), but the screen was partially visible vertically, while orizontally it was totally visible!

 I was unable to change the resolution, because the display settings utility window is not resizeable, and all the settings were "down", and I was unable to see them!

Furthermore, when I launched the display setting utility, it gave me an error... the usual error that it gives me when I install the NVIDIA drivers... asking me to use the nvidia control panel... so I think that even if I was able to see the settings records, it would never allow me to change them... 

So, question: Please, tell me how to manually change the resolution in the xorg.conf. In these days I tried taking the strings by googling, but it gave me the classic error while booting... the strings were not good....



anyway.... this is the conclusion:

WITH ANOTHER MONITOR the image appears!!!!

I hope this can help.....

---

### Post by garythegoth on 2009-05-01
> **ununpentium said:**
> Thank you gary.
I tried with any aperture size, nothing! (from 4 to 256 MB). Always monitor BLACK and its power led flashing....


IMPORTANT NEWS:

since the monitor light flashing is an unsupported resolution-like symptom, I tried connecting another LCD DVI monitor, very big: an Apple 30".

SURPRISE!!!! The image appeared, stretched orizontally and replied 3 times in the screen....

So I made the reboot and the image become just one: but with a strange behaviour: the resolution was 1024x768 (I don't remember how I understood this), but the screen was partially visible vertically, while orizontally it was totally visible!

 I was unable to change the resolution, because the display settings utility window is not resizeable, and all the settings were "down", and I was unable to see them!

Furthermore, when I launched the display setting utility, it gave me an error... the usual error that it gives me when I install the NVIDIA drivers... asking me to use the nvidia control panel... so I think that even if I was able to see the settings records, it would never allow me to change them... 

So, question: Please, tell me how to manually change the resolution in the xorg.conf. In these days I tried taking the strings by googling, but it gave me the classic error while booting... the strings were not good....



anyway.... this is the conclusion:

WITH ANOTHER MONITOR the image appears!!!!

I hope this can help.....

Are you sure the GeForce isnt borked? Though I doubt it, those cards are like rocks.

---

### Post by ununpentium on 2009-05-01
I don't think... with Windows it worked well...

---

### Post by ununpentium on 2009-05-01
Xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
   Identifier   "Configured Video Device"
EndSection

Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device      "Configured Video Device"
EndSection


LSPCI:
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)

Monitor: Apple Cinema Display 23" (LCD).

Thanks!

---

### Post by garythegoth on 2009-05-01
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection

Thats what mine looks like.

Hmmmmm it dosent seem to have registered the 5700 in your Xorg.cong.

Try editing your Xorg.conf if you know how and add

Driver    "nvidia"

Under Section Device. Its really weird the problem your having.

---

### Post by ununpentium on 2009-05-01
Now the NVIDIA drivers are active and they works... accelerated too... I used other monitors in order to obtain this.

The problem WAS THE MONITOR!!!! Apple HD Cinema Display LCD 23"!

Please, I found a page that speaks about the problem:

[http://ubuntuforums.org/showthread.php?t=85109&page=2](http://ubuntuforums.org/showthread.php?t=85109&page=2)

The monitor goes in sleep mode!!! Exactly!!!!

See the last reply, user MBUTALA: finally he found a solution.... but...

the link that he wrote doesn't work!!!

I tried to reply in that discussion, but I get a message in which I read that I have not the permission!!!!

I tried to send a private message to mbutala, but I get a message in which I read that I must have 75 replies in order to be able to send a private message....

Please, tell me where can I find that page, or how could I contact that user!!!

Thank you!!

---

### Post by ununpentium on 2009-05-01
Solved!!!!

IT WORKS!!!!

RISOLTOOOO!!!!

The problem is not a particular monitor, but the nvidia cards with the DVI LCD monitors in ubuntu!!! They go sleep as it loads the graphic interface!

This guy found a solution (Mbutala):
[http://ubuntuforums.org/showthread.php?t=85109&page=2](http://ubuntuforums.org/showthread.php?t=85109&page=2)

See the last reply, of MBUTALA: there's a link but it doesn't work!

I found a page of him using google's cache, I attach the page (html) in the zip attachment.
I put also my actual working xorg.conf in the zip.

Thank you ALL, I hope that this can help!!!

Bye!!!

---

### Post by Citizin on 2009-05-01
Wish I would of found something like this a couple years ago. I used to own a 5700LE and it would never work wth 3d acceleration or 2d, I had the exact same problem as you. Now I use a 8600GT 512 and I never had the same problem. Thats good that someone found something, I always came to a dead end.

---

### Post by garythegoth on 2009-05-01
> **ununpentium said:**
> Solved!!!!

IT WORKS!!!!

RISOLTOOOO!!!!

The problem is not a particular monitor, but the nvidia cards with the DVI LCD monitors in ubuntu!!! They go sleep as it loads the graphic interface!

This guy found a solution (Mbutala):
[http://ubuntuforums.org/showthread.php?t=85109&page=2](http://ubuntuforums.org/showthread.php?t=85109&page=2)

See the last reply, of MBUTALA: there's a link but it doesn't work!

I found a page of him using google's cache, I attach the page (html) in the zip attachment.
I put also my actual working xorg.conf in the zip.

Thank you ALL, I hope that this can help!!!

Bye!!!

Haha, weird as hell glitch. Good to hear you figured it out though:lolflag:

---

### Post by ununpentium on 2009-05-02
:popcorn: :guitar:

---

### Post by cosimo on 2009-09-29
Hey guys,
 This may   be a bit late but the fx series card is no longer supported on current kernels by nvidia.
There are no kernel modules for the fx series cards.
So..no matter what you do... you cannot use  the fx series nvidia cards on linux any longer
I have found no solution to this other than using a very old kernel

coz

---

