---
title: "Screen reslution not right......"
date: 2008-10-15
forum: General Help
---

### Post by Immolatus on 2008-10-15
I'm running ubuntu through an HD TV that (according to the manual) is capable of at least 1280x768 resolution and also 1024x768, either of which I would be happy with compared to right now (19 inches at 800x600:shock:) It's like being fish eyed...lol. I've tried dpkg reconfigure -xorg --config or what ever and I only get the option to set up the keyboard not the screen resolution. I know for a fact that my monitor supports 1024x768 @ 60Hz vertical which is what I'll shoot for. somebody?....anyone?? any thoughts?????

---

### Post by loomsen on 2008-10-15
cat /etc/X11/xorg.conf 

and post it here. I'm sorry, but it's 6a.m. in Germany, quiz time's over for a cpl of hrs.

---

### Post by Immolatus on 2008-10-16
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by spinifex on 2008-10-16
> **Immolatus said:**
> I'm running ubuntu through an HD TV that (according to the manual) is capable of at least 1280x768 resolution and also 1024x768, either of which I would be happy with compared to right now (19 inches at 800x600:shock:) It's like being fish eyed...lol. I've tried dpkg reconfigure -xorg --config or what ever and I only get the option to set up the keyboard not the screen resolution. I know for a fact that my monitor supports 1024x768 @ 60Hz vertical which is what I'll shoot for. somebody?....anyone?? any thoughts?????


You could try this post.  [http://ubuntuforums.org/showthread.php?p=5973331#post5973331](http://ubuntuforums.org/showthread.php?p=5973331#post5973331)

My mess of a Xorg.conf device section. 

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
Option "AddARGBGLXVisuals" "True"
Option "OpenGLOverlay" "off"
Option "VideoOverlay" "on"
Option "logo" "1"
Option "Coolbits" "1"
Option "UseEdidDpi" "false"
Option "DPI" "96 x 96"
EndSection


I fixed the screen resolution up with an EDID & DPI entry in the device section to scale the resolution properly but my LCD is a Samsung 40 inch 1920 x 1080.  Now everything is hunky dorry....   I think this is just a xorg issue. 

Anyway try it out.  

ta

---

### Post by loomsen on 2008-10-16
You may want to read [this, which could be kind of helpfull, or at least enlightened](http://ubuntuforums.org/showthread.php?t=940578) if you only know your X-Server from yellin at it.

And, nice of you to post your output, but you didn't configure anything in your xorg, so some hardware information too please, and we could start working on your issue ;)

What X basically does is providing a Server, which connects input devices to output devices in a more specific way (in contrast to BIOS:basic input output system) than the BIOS does, making it possible to run a graphical user interface for example.

Anyway, pls read the post above and also tell us a little bit more about your hardware.

*edit*
Wow, almost 2 years of ubuntu and not even one custom option in your xorg? How the ...oO

---

### Post by Immolatus on 2008-10-16
I never had to customize xorg before because all my previous experience has been on laptops with linux. I just built this machine from parts.

Anyhow the hardware I think you need to know about are the monitor: sony bravia LCD model #kdl-19m4000 (this is an HD TV with a pc input). GPU is an MSI radeon HD r4650 512 DDR2.

---

### Post by Immolatus on 2008-10-16
Update: so i tried this [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and it didn't help. I'm at a loss for today, about to throw the thing out a window:evil:

---

