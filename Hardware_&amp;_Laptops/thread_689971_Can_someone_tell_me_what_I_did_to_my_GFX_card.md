---
title: "Can someone tell me what I did to my GFX card?"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Adhesive33 on 2008-02-06
I have ubuntu on the second primary partition of a single HDD. WinXP is on the first partition. GRUB is the bootloader. 

Recently, I decided to install ATI drivers for my x1950 Pro by clicking on the restricted drivers tab that popped up in Ubuntu (I know, I should have researched it before hand). After Ubuntu installed the drivers, my computer rebooted, POSTed, and began to load Ubuntu. Around the point where the login screen should be displayed, I lost the video input signal to my monitor. 

I restarted and launched winxp via GRUB and the same thing happened; lost video signal at login screen. So, I reinstalled Ubuntu and it loaded fine using the default video drivers. 

After entering safe mode in Winxp and removing the ATI drivers, I was able to once again boot into winxp regularly and receive a video signal. However, any time I reinstall ATI drivers, I lose the video signal after restart. I've tried a number of different drivers, and have used driver cleaner pro to remove any trace of the old drivers before hand. 

Does anyone have any idea of how to fix this? I understand that it's basically a winxp issue, but it stemmed from an ubuntu operation, so maybe someone know what to do. Any help is appreciated.

---

### Post by Adhesive33 on 2008-02-07
bump

---

### Post by faulkes on 2008-02-07
Instead of using the Restricted Driver Manager, have you tried using Envy instead to install the latest ATI drivers?

I don't have a link handy for Envy but a forum search should turn it up quickly for you.

Faulkes

---

### Post by Adhesive33 on 2008-02-07
I have read up on envy and decided not to use it. My main problem now is that any ATI driver causes loss of video in winxp after using the restricted driver in ubuntu, and I can't seem to fix that. I'm curious why installing a driver would effect things in winxp...could this be a hardware problem?

---

### Post by Yellow Pasque on 2008-02-07
ATI's Catalyst drivers suck, plain and simple. I recommend using the radeonhd driver if you can live without Compiz eye candy and 3d acceleration for the time being. The developers of that driver are awesome (I chat with them sometimes in IRC). There's a link in my signature for setting up the radeonhd driver.

---

### Post by Adhesive33 on 2008-02-16
I've tried multiple drivers and still can't get it to work, although the 7.1 drivers allowed me to boot into 4-bit mode.

---

### Post by danwood76 on 2008-02-16
It sounds like the ati driver is leaving something in the video cards registers, or modifying the EEPROM data.
does it happen the same from a cold boot?
ie install the drivers power off your machine (switch of at the wall) wait for 30 seconds then switch it back on?

I have an x1950 pro running fine with the latest ATI drivers btw.

---

### Post by Adhesive33 on 2008-02-16
I have removed every usb device, reseated the video card and checked it's power connection, made sure all ram is in place, unplugged the computer from the wall, cleaned out the power supply, checked all fans and cables, completely reformatted the hard-drive, installed fresh copies of winxp with and without service packs, used old and new mobo and chipset drivers, flashed my card's bios with tweaked bios and then back to the original, and nothing has worked. Since installing the restricted drivers in linux, I cannot get my monitor to recognize a video signal when the card is operating with anything other than default window or linux drivers. 

One strange thing is that my monitor will recognize an S-video signal from the radeon with any ATI driver installed. Obviously I don't want to use an S-video connection for everyday use though. I haven't tried VGA because the x1950 pro doesn't have a vga output.

---

### Post by danwood76 on 2008-02-16
I just re-read your first post and I think your vid card is dead.
It sounds like when it enters a high graphics mode it falls over.

This would explain why it only dies when it actually gets into the OS and not before, as this is obviously the only time when the hardware acceleration kicks in.

I dont think its possible to break a graphics card with drivers, I would think the culprit is heat. My x1950 used to get very hot so I had to doa  bit of DIY modding on its power supply chips.

And the x1950 does have VGA out, you just need to use a DVI-VGA plug as DVI sockets hold all the signals for VGA too but need a breakout to get the 15 D-type.

---

### Post by Adhesive33 on 2008-02-16
> **danwood76 said:**
> I just re-read your first post and I think your vid card is dead.
It sounds like when it enters a high graphics mode it falls over.

This would explain why it only dies when it actually gets into the OS and not before, as this is obviously the only time when the hardware acceleration kicks in.



This is my biggest fear, but why would the card work via the s-video cable? Surely the card is still in accelerated 3D mode when outputting through the S-video with Catalyst drivers installed, right?

---

### Post by Adhesive33 on 2008-02-16
Well, I tried it witha  vga adapter and it works fine that way. It appears that only digital signals are lost. At leas VGA is acceptable for now, but it's really strange that I'd lose DVI right after installing the linux drivers. :confused:

---

### Post by brainstuff on 2008-03-10
Sounds pretty similar to what I'm getting - I hadn't thought about it possibly being a DVI problem. My Vista 64 install (yeah, I know) wasn't effected by installing the restricted drivers in Ubuntu though, and I only had the black screen of death in Ubuntu after the login screen, but could still get into my other OS from Grub. Doing a dpk-reconfigure xorg.conf gets me back in using Vesa drivers.

My AGP x1950 is attached to my widescreen LG 20" monitor (1680x1050 native) via DVI. I'm running amd64 edition of 7.10.

I'll try connecting it using analog to see if it works, but I don't want that to be a permanent fix, because I use the analog input for my Xbox (yeah, I know).

:)

---

