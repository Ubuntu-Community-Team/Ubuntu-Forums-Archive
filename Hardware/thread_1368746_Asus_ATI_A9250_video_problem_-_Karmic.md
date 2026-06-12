---
title: "Asus ATI A9250 video problem - Karmic"
date: 2009-12-31
forum: Hardware
---

### Post by nuffy on 2009-12-31
I have tried for days to get my video card working with my fresh install of Karmic (worked ok for Jaunty!)....searched and searched but alas no fix!!

I stumbled across this tread [https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI) and thought it may help.... 

I got to the Instructions section to edit the 'src/radeon_bios.c' file and couldn't locate these lines...

' /* revision 4 has some problem as it appears in RV280,
           comment it off for now, use default instead */' 

to perform the next step of....

....after this comment follows a code block that has been commented out. We need to re-enable this code by removing the commenting-out. In my case deleting lines 574 and 561 did the job.

It was not there!?!?!  

I am not sure what to do next.... can anyone assist me??

Thanks and Happy New Year!!

Nuffy
PS:  I replaced change every instance of "xserver-xorg-driver-ati" with "xserver-xorg-video-ati"

---

### Post by tanoloco on 2010-04-08
Hi,

I've got a Radeon ATI 9250 rev[I]280 with 128 mb of ram,
when I've installed Karmic I've got a black screen and I solved installing
[/I]```
*sudo apt-get install xorg-driver-fglrx*
```[I]

Lately I've realized that my hardware 3d acceleration didn't work because I couldn't activate compiz desktop effects.

I came into the same guide you followed I  suppose
[/I][https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI")

and like you I stopped following when it says

```
/* revision 4 has some problem as it appears in RV280,
           comment it off for now, use default instead */
```because I don't have this comment like you don't.

I searched a lot and finally I came into this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

just follow it not caring when it says to go to the other link if you have a Radeon 9200/9250 because it's the same link as above and you will find yourself in a vicious circle.

That's what I did:
1. from synaptic remove any package installed that contains **fglrx**My case was:
[B]fglrx-kernel-source
xorg-driver-fglrx
fglrx-amdcccle
fglrx-modaliases[/B]

If you  manually have installed **xorg-driver-fglrx** in the past you can uninstall it by using:
```
sudo fglrx-uninstall.sh
```2. Reinstall:
[B]libgl1-mesa-glx
libgl1-mesa-dri
xserver-xorg-video-ati[/B]

3. Reboot.

It worked for me! :) and I could activate compiz !!! 
You can test your hardware by typing:
```
glxinfo | grep render
```You must get a  lines output like
> direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 (RV280 5960) 20090101 x86/MMX/SSE2 TCL DRI2If you get **direct rendering: Yes** and your second line is different from **OpenGL renderer string: Software Rasterizer** then your hardware 3d acceleration is correctly activated.

If it still doesn't work, you can keep trying configuring your /etc/X11/xorg.conf as suggested in the above link and in this thread
[http://ubuntuforums.org/showthread.php?t=1308027](http://ubuntuforums.org/showthread.php?t=1308027)

I think that might work:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode"       "8"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
EndSection
```BTW that's my output of:
```
grep XXA /var/log/Xorg.0.log
```> nothing```
grep EXA /var/log/Xorg.0.log
```> (II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:```
lspci -nn | grep VGA
```> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)However it seems to be solved in the future realese of Ubuntu 10.04

Hope it may help :)
Cheers

---

