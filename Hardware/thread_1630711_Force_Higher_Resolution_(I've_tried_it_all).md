---
title: "Force Higher Resolution? (I've tried it all)"
date: 2010-11-25
forum: Hardware
---

### Post by devhace on 2010-11-25
Hi guys,

So my problem would appear to be a simple one but it's been plaguing me for the past few days. I recently moved my computer to a new, bigger HDTV and I cannot make it output more than 640x480. I use my XBox 360 to play 720p all the time. I've determined through the Xorg log that it cannot read the EDID of the TV, which should be fixable through editing the Xorg.conf file but I cannot still make it work. I've been using this [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
utility to create modelines and have tried all sorts of resolutions and stuff. The manual for the TV isn't helpful and it has no online resources (I guess it's old? It's a Philips FTR9955/17). I'm at the end of my rope, 640x480 is so ugly haha! What happens unless the xorg is left to the default (with no extra modelines) it only boots to terminal until I delete the extra lines and restart it. It looks like this
```

Section "Screen"
            Identifer          "Default Screen"
            DefaultDepth   24
EndSection

Section "Module"
       Load   "glx"
EndSection

Section "Device"
            Identifier        "Default Device"
            Driver "nvidia"
            Option "NoLogo"     "True"
EndSection

```I'm still pretty new to all of this and it's all very confusing. I would appreciate help!!

My computer:
Ubuntu 10.04 server
Dell Dimension 8200
3 (?) Ghz
512mb RAM
Nvidia fx 5200

My ultimate goal is to run boxee on this guy (and I had it working astonishingly well on the other TV) now I just have to get it working right here!!

---

### Post by heyho on 2010-11-25
I have had similar problems to this in the past (also having a display issue at the moment!).

How are you connecting?  In the past, I've had resolution setting problems caused by VGA cables not being fully connected - ie not all 15 pins are connected.  Causes real headaches when using televisions as displays.  More common for cheap cables to not have all pins connected, especially the long cheap items from ebay!

Edit:  Do you have proprietary drivers activated?  Have you run "sudo nvidia-settings"?

---

