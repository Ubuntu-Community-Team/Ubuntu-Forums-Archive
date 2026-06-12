---
title: "problem with graphics &amp; desktop effects"
date: 2012-02-09
forum: Hardware
---

### Post by Bahdour on 2012-02-09
hi,

I'm new to Linux. I've installed BackTrack R1 KDE 64x (which is customized version of Ubuntu 10.4) on Toshiba Satellite C660-M13X. Everything works well except the Graphics. It has Intel® Core™ i3-2330M Processor with Intel® HD Graphics 3000.

root@bt:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

When I run video files, the view is not clear. I can't enable Wobbly windows & a lot of desktop effects. I tried even with compiz but it didn't work. I guess the problem is with my graphic driver

Can anyone help me with this?


thanx

---

### Post by madvinegar on 2012-02-09
Have you tried to see if in the additional drivers there is any driver recomended so as to enable same? (first you have to get internet connection and update all the packages in synaptics).

I think for intel the driver is called 173.xx something...

---

### Post by Bahdour on 2012-02-09
actually, I don't have (Additional Drivers). I need to install everything even synaptic. I searched in synaptic for (Additional Drivers) but I couldn't find it. Do u know how to install it?

---

### Post by Bahdour on 2012-02-09
I've installed Hardware Drivers (apt-get install jockey-kde) & it shows me that no proprietary drivers are in use. I searched in Synaptic & I found that the following packages are installed:

xserver-xorg-video-i740   - This package provides the driver for the Intel i740 family of video chipsets.
xserver-xorg-video-intel  - This package provides the driver for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965 series chips.

any idea what can be the problem?

---

### Post by Yellow Pasque on 2012-02-09
The problem is your hardware (specifically, sandy bridge graphics) is too new for Ubuntu 10.04, so 3D doesn't work. Finding workarounds is left as an exercise to the reader (hint: intel doesn't use proprietary drivers, so jockey is useless for that).

---

### Post by Bahdour on 2012-02-09
thanx [Temüjin]("http://ubuntuforums.org/member.php?u=327594").. it seems that I have to have another graphics card..

---

