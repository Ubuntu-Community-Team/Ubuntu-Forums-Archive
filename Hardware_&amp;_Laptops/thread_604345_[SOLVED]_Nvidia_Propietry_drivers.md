---
title: "[SOLVED] Nvidia Propietry drivers"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by FooAtari on 2007-11-06
Having had a lot of difficulties installing Linux on my laptop, I thought I'd have an easier life on a desktop machine... Think again.

So I built a computer last weekend, Asus P5K SE mobo, E2140@1.6Ghz, 1GB RAM, 7300GT video. Dell 19" 1680x1050 display

I downloaded several Live CD's, all but 2 failed to boot all the way to the desktop, great start I thought.

Luckily the one I intended to go with was one of those two, Kubuntu.

So after a bit of messing about with the hard drives I eventually get to the Desktop.  I update the system and I see a message that there are proprietary drivers for my video card.  Great, so I install them.  It then advises to me reboot, which I did.

At the point where the login screen normally gets displayed (i think) my monitor displays a message that it cannot display the resolution.  Optimal resolution is 1680x1050.

I try to restart X server (is that the correct term?) with CTRL+ALT Backspace but nothing changes. Well actually after several attempts and a delay the desktop did suddenly appear.  At the point I loaded the Nvidia settings and checked everything looked OK, which it did. Resolution was set to 1680x1050. So I rebooted and same thing again.  This time I couldn't get anything to display. I see it boot and at the point where the login screen is displayed I get the same message on my monitor. The funny thing is my monitor can obviously display lower resolutions, and surely it hasn't select a higher one by default...

I thought maybe it was a problem with Xorg.conf? Anyone got any suggestions?  Should I forget about the proprietary drivers and try a different one?  At the moment I might have to reinstall, unless anyone can tell me what I need to do from the prompt if I boot in recovery mode or something.

Thanks a lot

---

### Post by renzokuken on 2007-11-06
at the prompt login and run

```
sudo dpkg-reconfigure xserver-xorg
```

you can use this CLI wizard to change your xorg settings. try checking the refresh rates,resolutions and driver used. the proprietary driver is called "nvidia" but if you wanted a more failsafe driver till you get the nvidia one working you can also use "nv" or "vesa"

---

### Post by FooAtari on 2007-11-06
Thanks for that I'll give it a go tonight after work.

If I revert to another driver will I still be able to make use of 3d applications, such as Beryl? I know there is an open source driver, perhaps that is more suitable.

While searching the forums for possible solutions it seems 7.10 is giving a lot of people problems. I might try 7.06 as that is the LTS?  I'd like to get 7.10 working though, so I'll persist with that first.

---

### Post by renzokuken on 2007-11-06
6.06 is actually the long term support. 7.04 (feisty) is not.

i'm pretty sure you can use beryl/3d with the nv driver, but definately not with the vesa one.

---

### Post by FooAtari on 2007-11-06
Just had another thought.

My monitor seems to get detected as a Dell, but a dell CRT, perhaps that is causing problems... Anyway to make it detect the correct monitor.

I also don't remember seeing any modline entries at all in the xorg.conf (just saw it in another thread).  Although maybe I just didn't see them I wasn't looking for it. I seem to have learned enough so far to know the general area to look when I have problem, but not what to look for when I get there :lolflag:

---

### Post by FooAtari on 2007-11-08
sudo dpkg-reconfigure xserver-xorg

fixed it. Thanks.

---

