---
title: "split screen error! Unable to install 13.04"
date: 2013-04-26
forum: Hardware
---

### Post by bcomp on 2013-04-26
I've been having this problem on 12.10 with the latest kernel updates for at least three months now but I was hoping that the new (k)ubuntu version would somehow fix it. 
If I recall correctly, after updating the kernel from 3.0.5-21 onwards, I get this error upon loading kde:

[ATTACH=CONFIG]241813[/ATTACH]

As you can see the screen area is somehow split in two parts. It kinda cool but not what I wanted! ;)
At first I hoped that it would be fixed (or go away) with the next kernel update but it wasn't! :(
After testing both kubuntu and ubuntu 13.04 on my system today, I get the same split screen error. What's more there seem to be no install options with the live dvd tests, so the gui is messed up. 

I've got a brand new sony vaio (i7, 6GB RAM, with an ATI VGA  [Radeon 7500M/7600M Series]). 

I've tried to install the "official" ATI linux driver in the past without much success. 
It installed allright but couldn't get the 3d acceleration to work so I regressed to the one provided by the repos. 
I'm a heavy Blender user and it was hardly possible to use it on such a high end system, which is a same. 


Any clues? 

I would really really like to make the transition to 13.04 but I guess I need to sort out this damn ati graphics issue first. 

My current xorg.conf 

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "UseFastTLS" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

---

### Post by ridcully on 2013-04-27
I had the same problem

[http://askubuntu.com/a/75677/152985](http://askubuntu.com/a/75677/152985) gave me a hint to solve it:

sudo apt-get install fglrx

did it for me.

---

### Post by bcomp on 2013-04-27
Thank you for the suggestion. I tried it with my current version (12.10) and it doesn't work! :(

Fglrx gets installed but I'm unable to start kdm. 

Considering that this is a well known laptop series, I'm surprised that others haven't experienced this problem already.

---

### Post by bcomp on 2013-05-07
Come on folks! No suggestions?

---

### Post by bcomp on 2013-05-15
Any tips on where to post this problem so that it attracts more attention?

---

### Post by archeryguru2000 on 2013-08-29
Did you ever git this resolved?  I'm having a similar issue myself.

Advanced Micro Devices, Inc. [AMD/ATI] Turks Pro [Radeon HD 7570]

Anybody?

---

