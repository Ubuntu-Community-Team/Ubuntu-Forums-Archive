---
title: "TOSHIBA 4080XCDT: xorg.conf Trident 9525"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by sorry_name_taken_already2 on 2005-08-08
I have installed or using x-server-xorg from the boot cd
[color=red]apt -get install xserver-xorg[/color]

and successfully got a configuration screen
[img]http://www.mrbass.org/linux/ubuntu/install/018xorgconfig.png[/img]

[color=red]root@unbuntu:~#startx[/color]
It failed to load up gnome or icewm. Debian/Unbuntu uses its own script gdm.
That gave me an idea. 

[color=red]apt -get install gdm[/color]
It worked! It installed gnome. Im guessing gdm means Gnome Display Manager?

I was hoping to install ICEWM instead. It is less mem/cpu hungry than gnome because I have an older laptop /w Trident 9525 2mb video :(

xorg and gdm installed.
I get a screen message

I cannot start the X server (your graphical interface). It is likely that it it no set up properly *duh* Would you like to view the X server output to diagnose the problem?
<yes> <no>

Freezing the laptop as a result.

I rebooted in recovery mode and back in prompt.

_**I NEED HELP with setting up xorg.conf!**_
and a six pack!

I think something is wrong with my xorg.conf file. I tried editing it because i found on google that the horizontal and Vertical refresh rates did not match the manufacturer's monitor spec and default colour depth was set at 24. The values were too high and the laptop froze trying to load gdm as a result. My toshiba 4080XCDT uses the, Trident Microsystem Cyber9525 video. Luckily, xorg supports it!

[http://www.xfree.org/current/trident.4.html](http://www.xfree.org/current/trident.4.html)
**Supported Hardware**
The trident driver supports PCI, AGP and ISA video cards based on the following Trident chips: 
Blade 
Blade3D, CyberBlade series i1, i7 (DSTN), i1, i1 (DSTN), Ai1, Ai1 (DSTN), CyberBlade/e4, CyberBladeXP, CyberBladeAi1/XP, BladeXP 
Image 
3DImage975, 3DImage985, Cyber9520, Cyber9525, Cyber9397, Cyber9397DVD 
ProVidia 
9682, 9685, Cyber9382, Cyber9385, Cyber9388 
TGUI 
9440AGi, 9660, 9680 
ISA/VLBus 
8900C, 8900D, 9000, 9200CXr, Cyber9320, 9400CXi, 9440AGi These cards have been ported but need further testing and may not work. 

> Great, but greek to me, mate! Howto configure xorg.conf to recognise the onboard video Cyber9525 . I am used to windows where I point to a .inf or install from .exe file and then go to display properties!
Can someone teach me how to configure xorg to run X win session or at least a windows manager login screen.

I am thinking of installing icewm or xpde GUI desktop instead of gnome because i have a slow PII 366 processor.


Much appreciated!


Andy
[email]curious_@hotmail.com[/email]

**PS ** has anyone got any luck in setting xpde (X display XP clone). It looks pretty cool but there is no documentation for its latest BETA version. Have a look on their website [www.xpde.com](www.xpde.com). Any comments?

---

