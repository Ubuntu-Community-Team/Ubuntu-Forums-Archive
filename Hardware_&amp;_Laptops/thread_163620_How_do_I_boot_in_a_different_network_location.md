---
title: "How do I boot in a different network location?"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by markwren on 2006-04-21
Gnome menu/System/Administration/Networking lets me set my laptop locations - "Home" is a broadband (ADSL) ethernet connection, and "Away" is dial-up using a PCMCIA modem.

If I boot from home, with broadband plugged into the ethernet socket ... and then change location in Gnome, disconnect the ethernet, and push in the PCMCIA modem I can dial out with no problems (maybe a bit of fiddling wit).

But when I am away from home Ubuntu still tries to boot using the ethernet, taking ages because it cannot find the connections. Then if I try to manually switch to the "Away" location in Gnome it simply gets confused and dial-up will not work no matter what I try.

Is there something I am missing? Is there a "location" boot flag? Do I need to do all this from the command line (how?) instead of Gnome?

Many thanks
Mark
Dell C810, Ubuntu5.10

---

### Post by markwren on 2006-04-21
Done a bit more fiddling & research ...
The main problem is that if the system is booted under the ethernet enabled "location" and the ethernet link is down (i.e. I am not attached to my internal LAN/broadband router)  then it refuses to de-activate in network-admin!

There is a package "netenv" which looks promising, claiming to allow me to set my network details each time I boot in order to match my location - but I really want to create a couple of presets which I can select as different boot options.

Such an option used to be available in SuSE 9.1 as "scpm" (system configuration profile manager) and I was hoping for something similar here. i.e. to setup /boot/grub/menu.lst with a separate boot option stanza which just had " PROFILE=home" or " PROFILE=away" as an extra parameter to the vmlinuz boot command.
 
Any thoughts?
Mark

---

### Post by florian.bw on 2008-03-12
This post is quite old, but I think the problem still exists. I wanna do the same,, I will see if I can do this by some boot parameter,

Meanwhile, I started a Ubuntu brainstorm request to add the possibility to change the location in the gdm login screen (and try to promote it a bit). Please vote for it if you want to see that change.

[http://brainstorm.ubuntu.com/idea/4365/](http://brainstorm.ubuntu.com/idea/4365/)
[[IMG]http://brainstorm.ubuntu.com/idea/4365/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4365/)

---

