---
title: "Cant configure jaunty with an Intel 945GM/GMS graphic chipset"
date: 2009-05-13
forum: Hardware
---

### Post by ierpe on 2009-05-13
Hi,

I have a Lenovo Thinkpad z61m with a 945 intel graphic chipset, and I freshly installed a Jaunty distrib.

The Display tool sees my laptop screen as unknown, and only gives me a 1024x768 max resolution.
I also have a 22" lenovo screen that I was using as an extended desktop, and it is not detected at all.

What can I do? Everything was working fine with Intrepid... although I didnt upgrade but made a fresh install so I lost my old configuration...

Please help me


Actually I cant get the package 915resolution in Jaunty... why?
and gksu displayconfig-gtk doesnt work anymore?

---

### Post by mista2 on 2009-05-13
> **ierpe said:**
> Hi,

I have a Lenovo Thinkpad z61m with a 945 intel graphic chipset, and I freshly installed a Jaunty distrib.

The Display tool sees my laptop screen as unknown, and only gives me a 1024x768 max resolution.
I also have a 22" lenovo screen that I was using as an extended desktop, and it is not detected at all.

What can I do? Everything was working fine with Intrepid... although I didnt upgrade but made a fresh install so I lost my old configuration...

Please help me


Actually I cant get the package 915resolution in Jaunty... why?
and gksu displayconfig-gtk doesnt work anymore?

I have the same issue with my HP TC4400. The manuals refer to installing 915Resolution, and indicate which repositories to allow, but even after updating apt it still cant find it, even though it says is is a dependancy to some other apps.
Has it been replaced by something else in Jaunty?

---

### Post by chrismiceli on 2009-05-13
Apparently 915resolution is deprecated, and when I found the .deb file, it said that there is a conflict with xserver-xorg-video-intel. I'm still at a loss of what to do to fix this though.

---

### Post by ierpe on 2009-05-14
I reverted to the driver from intrepid but still couldnt get my second screen to be detected...

The odd thing is, I booted on my windows session, where the extended desktop works. I rebooted, and this time, my "bios" screen appeared on my second screen(happens sometimes), causing the ubuntu to start on my second screen, and I had the choice for a good resolution.
but then my laptop screen wouldnt be detected and the extended desktop couldnt be setup...

Anyone? How to force a screen detection?

---

