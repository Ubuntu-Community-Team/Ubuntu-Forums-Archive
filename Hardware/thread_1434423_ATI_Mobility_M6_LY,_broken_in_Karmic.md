---
title: "ATI Mobility M6 LY, broken in Karmic?"
date: 2010-03-20
forum: Hardware
---

### Post by J-Rod on 2010-03-20
Well I purposefully never upgraded my laptop (Thinkpad R40, with the card in the topic) mainly because I had the compiz working fine. I decided that I was going to go ahead with the upgrade though, mainly because I am in that kind of a mood, heh.

Anyway, it seems that the FGLRX drivers are completely broken, and the open-source RADEON drivers enable, but just give me unusable graphical glitches, screen redraw, etc. I have tried doing everything I could think of, scouring the forums. Right now I am running with MESA in 2d, and it's usuable. I miss my compiz though.

I was surprised to see that xorg.conf is completely not needed now? How is one to change the drivers and settings now? Is it all done via the kernel? I also tried using EnvyNG in text mode, it appeared to installed the FGLRX drivers correctly, but on boot, it goes to a "low graphics mode" and is unusable. Anyone who can help or at least point me in the right direction, that would be greatly appreciated!

---

### Post by J-Rod on 2010-03-25
Ok, well after trying A LOT of things, including envyng,edgers, downgrading to the old Jaunty and Hardy mesa drivers... and some other stuff I forgot, I finally managed to get compiz working again.

At the moment, I am still running on the Hardy drivers, mainly because I know that they were the last ones that didn't give me much trouble. The modeset with KMS simply doesnt work with this card, and until I found this page, 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001)

I wasn't even able to generate a working xorg.conf, my old one was gone due to my idiocy of not backing it up before a major upgrade. Anyway, working xorg with thinkpad r40, Mobility 7000/M6 LY. Hopefully this will help someone else out that may be having the same issue!

```

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
        Identifier "ATI Technologies Inc Radeon Mobility M6 LY"
        Driver "ati"
        BusID "PCI:1:0:0"
        Option "AGPMode" "4"
        Option "AGPSize" "64" # default: 8
        Option "RingSize" "8"
        Option "BufferSize" "2"
        Option "EnablePageFlip" "True"
        Option "EnableDepthMoves" "True"
 Option "SWcursor" "off" #Faster than default (on)
 Option "AccelMethod" "EXA" #or XAA, which is the default and may be more stable
 Option "DynamicClocks" "on"
 Option "BIOSHotkeys" "on"
        Option "RenderAccel" "true" # Enables hardware acceleration
        Option "DynamicClocks" "on" # Adds clock scalability / power management for the video card
EndSection

```

---

