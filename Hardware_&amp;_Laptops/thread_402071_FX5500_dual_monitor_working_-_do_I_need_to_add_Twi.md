---
title: "FX5500 dual monitor working - do I need to add Twinview to Xorg?"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by 4ebees on 2007-04-05
Hi all,

I have two Philips 17" monitors running off a 128Mb Nvidia FX5500 dual-head card. I have an onboard Intel card I haven't disabled in the BIOS and which isn't connected to a monitor.

I'm running 6.06 Kubuntu on a P4 Hyperthreaded 3GHz CPU with 1.5G RAM.

All appears well - though on occasions I have some mild flickering on the second monitor (placed to the right of the monitor one) and occasionally games like Galaga appear to stutter mildly. Mind you, I just ran it while running Googleearth and all was well(?)  .

The second monitor appears to not function as quickly as the first monitor - is this to be expected? It is running from a vga converter attached to the DVI port on the card.

Overall, I'm not sure that the response rate is as quick as it was with my previous 32Mb Nvidia card.

I'm curious about a couple of things:

1. Do I need to enter any 'TwinView' settings in xorg.conf (there are none)?

2. Would disabling the  onboard Intel chip improve anything?

3. Interestingly, when I boot up, the Nvidia logo only appears on the second monitor - though this is set as the secondary screen. Any reason why this would be the case?

My xorg.conf file is attached for anything who is a keen :))

Any assistance or comments would be greatly appreciated, as would any advice or suggestions.

Regards,

Patrick

---

### Post by Tilo on 2007-05-31
Comments:

 - you should not see any flickering - unless you touch the cables ;-)
 - why do you explicitly set modelines in your xorg.conf ? you should not need to do that..
 - you can define the Xinerama and Clone options in the ServerLayout:

Section "ServerLayout"
    Identifier     "Multihead layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "on"
    Option         "Clone" "off"
EndSection

- it's very strange that the NVIDIA logo only apears on one screen - do you have two physical 
  grafics cards, or just one with two DVI connectors? 

  Perhaps think of upgrading your NVidia driver

---

### Post by kansei on 2007-08-12
I have an FX5500 (dual vga and an s-video) and an FX5200 (single vga and an s-video) that *both* exhibit some severe stuttering. 

They both are set up using the s-video out hooked up to a tv if that makes any difference. I even tried the FX5500 (PCI) in two different computers with the same effect.

It makes watching tv with mythtv unbearable, I'm not sure what the problem is.. both cards are using NVIDIA-GLX if perhaps there's a known problem.

both are also on Feisty

---

