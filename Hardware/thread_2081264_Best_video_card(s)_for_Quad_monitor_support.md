---
title: "Best video card(s) for Quad monitor support"
date: 2012-11-06
forum: Hardware
---

### Post by jacobfogg on 2012-11-06
Hey there, I currently have 2 nVidia 560's which are both dual monitor. As some of you might know, it seems the only way to run a 4 monitor setup is to run each pair of monitors as their own Twinview, then stitch them together using xinerama. This basically creates two large "screens" that each span two monitors. Unfortunately, xinerama is very old and outdated. And back around the time that Ubuntu 11.04 came out, a bundled update to xorg caused us to loose support for quad monitors using nvidia and xinerama all together without the use of a convoluted hack/patch job. Support has once again returned, but it's a huge hassle to get working, and every time it breaks or I upgrade, it seems like I have to start all over again. AND, buy using xenerama, I loose all of the OS eyecandy that you can get by just running two monitors.

I am tired of this... Sadly, this is the one feature that "just works" with windows, and causes me to *almost* want to go back to windows...

Ok, so onto my question. Are there any video cards out there that will assist in making my quad monitor setup a bit easier? I've heard whispers ATI has better linux support for multi-monitor. Has anyone seen this as the case? I have also heard that buying a single quad+ monitor video card will work better with Ubuntu.

The problem that I am having is either option (buying two equiv. ati graphic cards or buying a 4 or more monitor video card) is looking like a $200+ investment. Honestly, if it means getting all of this working, I am willing to make that investment at this point. But I do not want to spend the money if it is only going to be marginally better than my current setup.

So, what is the bet video card(s) to buy to support a four or more monitor setup?

---

### Post by FlappySocks on 2012-12-04
I would like to know this too.  Xinerama on my 4 monitors (2xNvidia) is really slow.

---

### Post by chrb on 2012-12-17
I have been looking for something similar. I have tried several cards (note I want open source drivers, I haven't tried the closed binaries as I have had previous bad experience with them breaking on upgrades and cards suddenly being unsupported and removed completely from the driver):

[LIST]
[*]Nvidia Quadro 4 NVS 280, two DVI monitors: glitchy, crashes
[*]ATI FireMV 2250, two DVI monitors: works well but only two monitors
[*]ATI FireMV 2400, four DVI monitors: fails to boot, completely unsupported
[/LIST]

I'm still looking for a working three monitor card. According to [reports on askubuntu](http://askubuntu.com/questions/106683/any-really-decent-way-to-get-three-monitors) the eyefinity cards should work with the open source drivers. In particular, the Sapphire Flex cards are recommended for DVI/HDMI monitors because they can drive multiple monitors from any combination of the card's output ports (other ATI Eyefinity cards can only drive 2 of the 3 DVI/HDMI ports simultaneously). 

[LIST]
[*]Saphhire Flex HD6450 will drive 3 monitors (DVI, DVI, HDMI): it ships with a HDMI-DVI adaptor so 3 DVI outputs work out of the box. Users report that this works fine with Linux and open source drivers, I plan to try it next.

[*]Sapphire Flex HD7950 will drive 5 monitors (DVI, DVI, HDMI, DP, DP). You should be able to do 5xDVI with HDMI-DVI adaptor and active DP-DVI adaptors.

[*]HD 7870 Eyefinity 6 will drive 6 monitors but that is all DisplayPort.
[/LIST]

---

