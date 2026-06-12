---
title: "Problems with Jaunty and SIS 315 PRO"
date: 2009-05-28
forum: Hardware
---

### Post by agrgal on 2009-05-28
First of all, excuse my english!

I've experienced an annoying problem upgrading Ubuntu from 8.10 to Jaunty 9.04. After an apparently non-problem upgrading, the system loads fine but stops just after the 'splash' process. The screen simply gets blank.

Looking for fixing the problem, I've read around the net and found some attempts to similar problems but any of them seems to fit mine. I did things like:

[LIST]
[*][https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
[*][https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
[*][https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
[/LIST]

My graphic card is: SILICON INTEGRATED SYSTEMS [SiS] 315 PRO PCI/AGP VGA Display Adapter. My monitor: PHILIPS 107E

Any solution? I'm meaning to reverse to 8.04 if no solutions are available. Thank you in advance.

---

### Post by Dennis Schulmeister on 2009-06-04
Hi,

first of all try to see if can get the console running. Do this by pressing [CTRL]+[ALT]+[F1] when the screen goes blank. If the console isn't working either please boot into rescue mode and inspect the /boot/grub/menu.lst file. Does the kernel have a vga=... option? That option is for the framebuffer resolution and is only needed if you're using the console often but it's not needed for the X server (GUI). Normaly both shouldn't infere but I once had a case where the vga=...option caused troubles with the X server.

If it still doesn't work (I guess so) try to load the generic VESA driver for Xorg. This one should always work albeit slower and with no 2D/3D acceleration. And it might need some fine tuning, too. But it should work.

The last step would be to try if there are official SiS drivers. Those are binary-only and don't have 3D acceleration but at least there are some drivers at all. Unfortunately I don't know about the model numbers of all SiS cards so I don't know whether there is an official driver for the 315 pro.

In any case my wiki on that topic might give you advice: [http://ncc-1701a.homelinux.net/~linux-sis](http://ncc-1701a.homelinux.net/~linux-sis)

Please let me know if you found something interesting out or if you need help.

Best,
Dennis

---

### Post by agrgal on 2009-06-09
> **Dennis Schulmeister said:**
> Hi,

first of all try to see if can get the console running. Do this by pressing [CTRL]+[ALT]+[F1] when the screen goes blank. If the console isn't working either please boot into rescue mode and inspect the /boot/grub/menu.lst file. Does the kernel have a vga=... option? That option is for the framebuffer resolution and is only needed if you're using the console often but it's not needed for the X server (GUI). Normaly both shouldn't infere but I once had a case where the vga=...option caused troubles with the X server.

If it still doesn't work (I guess so) try to load the generic VESA driver for Xorg. This one should always work albeit slower and with no 2D/3D acceleration. And it might need some fine tuning, too. But it should work.

The last step would be to try if there are official SiS drivers. Those are binary-only and don't have 3D acceleration but at least there are some drivers at all. Unfortunately I don't know about the model numbers of all SiS cards so I don't know whether there is an official driver for the 315 pro.

In any case my wiki on that topic might give you advice: [http://ncc-1701a.homelinux.net/~linux-sis](http://ncc-1701a.homelinux.net/~linux-sis)

Please let me know if you found something interesting out or if you need help.

Best,
Dennis
Thank u, Dennis

I actually re-installed 8.04 because I needed the computer running. Anyway, I'll write down your advices but I must remark the following:

1.- The shell worked properly, but getting into the rescue mode.
2.- I tried to activate a generic VESA driver, but it dind't work.
3.- I looked up SIS drivers but I couldn't find any suitable. Furthermore, I tried installing a different SIS model driver, and, of course, didn't work at all.

As I don't have much spare time , I'll delay this question several weeks. But I promise to go over this point again as promptly as I can, and then, I'll carefully read your survey about SIS drivers. 

Could I find out how to tackle this question just using a live session from a CD? I wouldn't like to get rid of ubuntu in a foreseeable future because of lack of drivers support. Will this bug be solved in following releases?

Thank you.

---

