---
title: "Nvidia GeForce2 GTS/GeForce2 Pro problem"
date: 2008-11-22
forum: General Help
---

### Post by javawizkid on 2008-11-22
Hi,
Sorry if this is in the wrong place, but I've tried to install the correct driver for my graphics card multiple times and it ALWAYS runs in low graphics mode. If I try to enable desktop effects it just says cannot enable them. Where can I get the RIGHT driver for it. I've tried the legacy one and a couple from the nvidia website. Please help.
Thanks.

---

### Post by eternalnewbee on 2008-11-22
Hi there.
 Have you tried to install from Hardware Drivers?
To check, go to: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by javawizkid on 2008-11-23
It's empty.

---

### Post by javawizkid on 2008-11-26
anyone?

---

### Post by NatroXz on 2008-11-26
Hi,

You need to enable the old nvidia drivers.

- Go To Synaptic Pacage Manager
- Settings.
- Reposotires
- Updates
- Mark "Pre Released Updates"
- Search after "Nvidia"
- Mark for Installation "nvidia-96-kernel-source"
- Mark for installation "nvidia-settings"
- Restart.
- Go To "System / Administration / Hardware Drivers"
- Then you activate "nvidia-96-kernel-source"
- Restart.
- Change resolution inn "nvidia-settings"

---

### Post by javawizkid on 2008-11-27
There is no "Pre Released Updates" checkbox. I installed what you listed and the card still isn't in the "Hardware Drivers" panel. How do you activate the "nvidia-96-kernel-source"?
Thanks

---

### Post by javawizkid on 2008-11-28
anyone?

---

### Post by javawizkid on 2008-11-29
I need to get this driver working. Can someone please help? I'm using Ubuntu 8.10.

---

### Post by isecore on 2008-11-29
Go into Synaptic, find the package named nvidia-glx-71. As far as I can tell that's the legacy (nice wording for "old") driver, and it should work for your card. I'm not sure if you'll have to do any more than install it though, but give it a go and see if it helps.

---

### Post by javawizkid on 2008-11-29
no luck.

---

### Post by isecore on 2008-11-29
Bummer, then I'm fresh out of suggestions.

---

### Post by inigomontoya on 2008-11-29
You need the 71.86.xx series drivers as referenced here [http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html).  Here are the latest drivers, [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606).  Instructions should be in the readme.  But, I can sum it up for you.  

Basically you need build-essential installed and your kernel headers.  Be sure to remove any failed nvidia-glx related installations with synaptic or apt first.  Download the driver package.  Then switch to console (ALT+CTRL+F1) then log in.  Then to kill X type: ```
sudo /etc/init.d/gdm stop
```  Then navigate to wherever you saved your package and type ```
sudo sh ./NVIDIA-Linux-x86-71.86.07-pkg1.run
```

---

### Post by javawizkid on 2008-11-29
kill x?

---

### Post by javawizkid on 2008-11-29
When I press alt ctrl f1. it goes into a panic saying unexpected response fd and it repeats it forever.

---

### Post by inigomontoya on 2008-11-29
What video driver are you currently using?  Please check the contents of your xorg.conf.  It's in the device section.  The file is located at /etc/X11/xorg.conf

---

### Post by javawizkid on 2008-11-30
No idea.



Section "device"
             Identifier          "Configured Video device"
EndSection

Section "Monitor"
             Identifier          "Configured Monitor"
EndSetion

Section "Screen"
             Identifier          "Default Screen"
             Monitor            "Configured Monitor"
             device               "Configured Video Device"
End Section

---

### Post by gregphil on 2008-11-30
I had a similar experience when I allowed the 'update' from 8.04.1 to 8.10.  My video would not run except in the brain dead GPU non-restricted drivers mode (which means very slowly).  After much research I concluded that 8.10 would not use the previous version of "restricted nvidia drivers" **and** that my nvidia cards (five year old GeForce 440 and 480) were no longer supported by the 'new' drivers.  While I found this hard to believe, I finally just gave up and bought an 'newer' nvidia card for $50 (a GeForce 6200) and plugged it in.

Once I enabled the restricted drivers using the menu 'System-Hardware Drivers' all of the fancy video features returned.

To save yourself many hours of pointless grief I recommend you either downgrade back to version 8.04.1, or buy a new video card.

Sorry.

---

### Post by javawizkid on 2008-11-30
A new graphics card in a Dell Dimension 4100 isn't a good idea...
Also how can I downgrade with wubi? I downloaded the 8.04 installer but it still downloads the 8.10 iso file.
I have also tried installing it from a cd so don't say that the gpu problem is related to a wubi install.

---

### Post by gregphil on 2008-11-30
You choose to download "ubuntu LTS"  (long term service) which is version 8.04.

If you just ask for ubuntu you get the latest full release which is 8.10

I still recommend purchase of a new video card, the dell machine must allow some expansion cards.....

---

### Post by javawizkid on 2008-11-30
the card holder doesn't fit new cards. I got a new card for my newer pc and tried to use its od card in the dell dimension 4100 but it didn't fit.

---

### Post by isecore on 2008-12-02
Most likely the problem with buying a newer card is that his machine most likely is of the AGP-variety, and all new cards are PCI Express. That's a bit of a problem when buying new stuff for old machines.

---

### Post by bryan.m.obrien on 2010-06-18
FWIW...I too have a 'seasoned' AGP video card.
lspci tells me it's a:

```
nVidia Corporation NV15 [GeForce2 GTS/Pro]
```

Lucid installed flawlessly, X was, umm, painful.

Here's some things I found that helped.

CTRL+ALT+F1 (virtual terminal)

Had to stop GDM.

```
sudo service gdm stop
```

I needed to get rid of the new nouveau driver as well as the vesa driver.

```
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get --purge remove xserver-xorg-video-vesa

```

Started GDM back up.

```
sudo service gdm start
```

Now..I'm not where I'd like to be, but I do have 1920x1200 on my Samsung
monitor.  I'm not where I'd like to be due to the tearing/artifacts that I still need to debug.

I think this leaves me with just xserver-xorg-video-nv, but I can't tell without my trusty old xorg.conf.  I know that /var/log/Xorg.0.log shows I'm loading the open source nv driver.

It ain't perfect, but it "works for me".

---

### Post by dcstar on 2010-06-19
> **bryan.m.obrien said:**
> FWIW...I too have a 'seasoned' AGP video card.
..........
I think this leaves me with just xserver-xorg-video-nv, but I can't tell without my trusty old xorg.conf.  I know that /var/log/Xorg.0.log shows I'm loading the open source nv driver.

It ain't perfect, but it "works for me".

Xorg 3D support for old Nvidia cards was dropped after 8.04 was released, only the basic open-source driver will work with this old hardware. All of this was documented in the release notes way back then.

xorg.conf can still be used in 10.04, it just isn't needed by default.

---

### Post by cascade9 on 2010-06-19
> **dcstar said:**
> Xorg 3D support for old Nvidia cards was dropped after 8.04 was released, only the basic open-source driver will work with this old hardware. All of this was documented in the release notes way back then.

xorg.conf can still be used in 10.04, it just isn't needed by default.

Hmm, from what I've seen I would guess that nVidia just lagged a bit behind with the drivers, and ubuntu was (as usual) using the newest version of xorg. 

I know that Xorg 1.6.x does work with the nidia 96.XX drivers. I used a GF4MX440 with the nVidia drivers on PCLinuxOS 2010.1, which uses Xorg 1.6.5. See also this post on the NV forum-

> Please see [Appendix A]("ftp://download.nvidia.com/XFree86/Linux-x86/190.36/README/appendix-a.html") of the README, which has a list of which GPUs are supported in which legacy branches. In your case, the GeForce 2 MX400 is supported by 96.43.*, which supports X servers up to 1.6.*. While I can't promise for sure, we do plan to support X server 1.7 in the 96.43.* series some day.[http://www.nvnews.net/vbulletin/showthread.php?t=139848](http://www.nvnews.net/vbulletin/showthread.php?t=139848)

Edited to remove junk.

---

