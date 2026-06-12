---
title: "i810 Videocard not working properly"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by Eugene RIMMER on 2006-12-13
Hi everybody.

I've got a laptop based on Intel 845GM Chipset. Both Ubuntu 6.06 and Kubuntu 6.06 Live CDs show 640x480 maximum resolution with i810 drivers, but work with native 1024x768 when booted in safe graphics mode.

Kubuntu 6.06.1 installation works fine with mesa driver (I can set any resolution up to 1024x768), but resets to maximum 640x480 when I set driver to 'i810'. The other problem is 0 Hz refresh rate in mesa driver (as it is shown on Hardware tab of Display control module). If I use i810 driver, the same tab shows me 60Hz (normal for this machine) but only 640x480 resolution is available.

Is there any relief for these pains?

Am I able also to use AIGLX/Beryl with this hardware?

---

### Post by Eugene RIMMER on 2006-12-25
OK, this is solved.

Just update the i810 Xorg driver to the latest available and do ```
sudo dpkg-reconfigure xserver-xorg
```

After a dozen of simple questions you'll have it all working (well, almost) as I now have.

---

### Post by Eugene RIMMER on 2006-12-27
The complete guide!

Once again what I've got:

- a **laptop** (Roverbook Voyager 512, but this doesn't matter)
- Intel chipset based motherboard with I**ntel i845G** integrated video controller
- Kubuntu **6.06.1 Dapper Drake**
- X.org **7.0**

The problem was:
- only vesa Xorg driver could provide my native 1024x768 resolution, the i810 driver couldn't give anything but 640x480 - **FIXED!**
- maximum color depth in vesa and i810 was 16bpp - not fixed yet.

How could I get this fix:
1. You should have all the main repositories enabled (as I don't remember where the package was residing).
2. You should have access to the repositories (i.e. be connected to Internet)
3. Load your package manager program (Adept in KDE, Synaptics in GNOME, aptitude under console if you wish for)
3.1. Be sure once again to enable all the standart repositories
4. Download the freshest lists of packages ("Fetch updates" in Adept/KDE, 'sudo aptitude update' for console, dunno for other)
5. [essential] Find and mark to install/upgrade the updated packages for xserver - you may see the driver for i810 (it's called something like 'xserver-driver-i810', anyway i810 in the name there is), other xorg drivers are exremely optional, you may leave them old if you don't need 'em.
6. Find and mark to install things about mesa and dri if you wish for (DRI stands for direct rendering infrastructure, it speeds up the graphics, so you may have like-in-f***ing-M$-Windows graphics performance for your i845G)
7. [optional] Install any other updates you may wish for
8. Do update eveything now. If you encounter any problems - just (Debian magic!) repeat the steps 1-8.
9. [essential] Open console (Konsole for KDE), type ```
sudo dpkg-reconfigure xserver-xorg
```. Now is the moment of truth. If you tried to manually edit the xorg.conf before, then I think you are smart enough to answer to the questions on the screen. On some step it will ask you of how much video memory you should have (in kilobytes). I answered 32768, which means 32 megabytes of video memory. Works pretty fine with most eye-candies.The only problem waiting for you there is: DON'T ALLOW IT TO AUTO-DETECT YOUR MONITOR ON SOME 3rd or greater STEP (I mean screen device not the videocard). Set your monitor manually, it's not so difficult.
10. Now reboot|restart X (I preferred the first as I did upgrade my kernel also)

When I passed through these steps I found i810 as my driver in xorg.conf AND I had 1024x768. Still I've got only 16bit display, but everything works fine.

I also manually configured some extensions, so now I have shadows and transparency. And don't forget - this is all hardware-enabled. I have high fps in glxgears while having shadows and transparent windows. So you will!

---

