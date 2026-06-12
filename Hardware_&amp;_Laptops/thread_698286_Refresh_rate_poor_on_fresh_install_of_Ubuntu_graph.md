---
title: "Refresh rate poor on fresh install of Ubuntu graphics drivers to blame?"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by jtreach on 2008-02-16
Heya I've recently installed Ubuntu on my friends computer and everything seems to have worked perfectly apart from the graphics refresh rate. I seem to remember on my computer (I had the same problem) this being a problem with nvidia and that I needed to install some propriety drivers for it to work, this time however it doesn't look like my friends card is nvidia. Here's some details on his graphics card:

```
*-display               
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga cap_list
       configuration: latency=0
```

Can anybody help?

EDIT: I just found this from another site but I think the website that is mentioned no longer exists:
> Huraaaaaaaaaaaaaaaaaaaaaaa!!!!!!!!!!!!! \\:D/ \\:D/

After logn time of ](*,) I can relax!!!!!!

First of all, the first link for users who has problems [http://www.x.org/X11R6.8.2/doc/](http://www.x.org/X11R6.8.2/doc/)

And exactly, for users with video cards like my "SiS"

[http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)

The recept, I do:

Debian Sarge (stable), Debian Sid (unstable), Ubuntu:
Add the following to your /etc/apt/sources.list:
For binaries: deb [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./
For source: deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./


Install two packeges x-driver-sis and sisctrl

Exactly you need just x-driver-sis.

And correct xorg.conf


Section "Device"
Identifier "Generic Video Card"
Driver "sis"
EndSection


That's all!!!

EDIT2: I think the problem is with this specific driver package "xserver-xorg-video-sis" when I plug that into google the first to pages are bug reports, thing is I can never decipher those things so I have no idea whether or not my problem can be solved.

---

### Post by jtreach on 2008-02-16
Think this might be the problem can anybody tell me how to implement the fix? Pretty please [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/162265](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/162265)

---

