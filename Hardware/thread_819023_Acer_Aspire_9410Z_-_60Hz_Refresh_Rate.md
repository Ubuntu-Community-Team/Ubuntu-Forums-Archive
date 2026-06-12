---
title: "Acer Aspire 9410Z - 60Hz Refresh Rate"
date: 2008-06-05
forum: Hardware
---

### Post by brent_watson on 2008-06-05
Hi everyone,
I'm having trouble trying to get a refresh rate higher than 60hz on a Acer Aspire 9410z laptop.  Any help would be MUCH appreciated!.

What I've tried so far is; using the 915resolution program, doing a reinstall of xserver-xorg-intel, and doing  dpkg-reconfigure xserver-xorg - but no luck with any of these.

Here's some detail on my hardware from lshw:
[FONT="Courier New"]
product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0
[/FONT]

...and the Screen section of /etc/X11/xorg.conf is pretty standard right now (Note that I've had zero experience editing an xorg.conf):
[FONT="Courier New"]
Section "Screen"
   Identifier  "Default Screen"
   Monitor     "Configured Monitor"
   Device      "Configured Video Device"
EndSection
[/FONT]


Thanks again for any help with this!!

---

### Post by rlhawk1 on 2008-06-11
Try running 'sudo displayconfig-gtk' and setting the monitor to your specific screen, then see if you can use the same displayconfig-gtk program to change your refresh rate.

---

### Post by brent_watson on 2008-06-23
Thanks for the reply.

My specific monitor is not listed.  Choosing a Generic "LCD Panel 1400x900" still only gives me a single option of 60hz.

After trying a couple of different monitors -- they all seem to only allow a refresh rate of 60hz for me.

Any other suggestions?

Thanks again for the help!

---

