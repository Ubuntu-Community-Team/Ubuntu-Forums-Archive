---
title: "Restricted driver problems"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by ptipton on 2009-04-20
I have installed Linux Mint 6 on a PC with a built in ATI graphics chip and have had problems installing the restricted driver so that I can activate desktop effects. (Note I also have identical problems with Ubuntu 9.04 beta which I installed dual boot on the same machine). The problem being that after installing the restricted driver it boots up until where you would expect the login screen and then goes to a blank screen. ( Note I can get to terminal from the blank screen). I tried several alternative methods of installing the driver, Envy, Manual from ATI site etc etc and followed the various tips in the Mint forums re black screens with ATI drivers all to no effect.
Given that I have had bad past experience with ATI cards in Linux I then went for what I thought would be a simple solution and and installed an Nvidia 8600 video card but guess what , exactly the same problem with this- boots up until just before login screen then goes to black screen. If I go into xorg.conf and change the driver from "nvidia" to "nv" it boots fine but then of course no desktop effects.
I'm wondering if it has something to do with the monitor which is a no name LCD TV/Monitor which apart from the resolution I have not been able to find any info. Unfortunately I don't have an alternative monitor to try it on at present.

I have posted the xorg log from a boot to black screen using restricted nvidia drivers here : [http://pastebin.com/m3806336d](http://pastebin.com/m3806336d)

Mother board is ASUS P5RD1-VM
Video card is nvidia 8600
LCD is a 19" TV/Monitor E-VIEW made in Malaysia- only details I can find are that its 1440x900 16:9

I have tried reconfiguring X etc with no success.

Any help much appreciated.

---

### Post by ptipton on 2009-04-26
I managed to find a solution, I decided to try another live distribution to see if I could get the nvidia drivers to work. PCLINUXOS Gnome installed the drivers and worked fine so I copied the xorg.conf file and used this and in both Mint 6.0 and Ubuntu 9.04  and both now work fine. I guess PCLINUXOS must detect my monitor properly whereas Ubuntu doesnt.

---

