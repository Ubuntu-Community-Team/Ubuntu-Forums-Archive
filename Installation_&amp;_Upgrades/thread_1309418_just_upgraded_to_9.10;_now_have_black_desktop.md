---
title: "just upgraded to 9.10; now have black desktop"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by axel_2078 on 2009-11-01
Since I wasn't able to do a clean install and get grub to boot the damn OS, I reinstalled 9.04 and did an upgrade, which seemed to work just fine. After I login, my desktop is black. I can see the application menu at the top and the system bar at the bottom just fine, but the desktop itself is black. This prevents me from opening anything in full screen because then I can't see it. As long as I open it and keep it minimized (in a small window) I can see it, but as soon as it goes full screen, all I can see is the title bar for the application that's launched. This is really annoying. I tried changing the theme to see if that made a difference....it didn't. I tried changing the desktop background too, but no matter what I choose, the desktop stays black. What's up with this?

---

### Post by Turtle.net on 2009-11-01
have you tried ```
metacity --replace
``` or maybe System->Preferences->Appearance and then disable the Visual Effects (by choosing None).
If it solve your problem, then it's  compiz related, and maybe video driver related.

---

### Post by axel_2078 on 2009-11-01
> **Turtle.net said:**
> have you tried ```
metacity --replace
``` or maybe System->Preferences->Appearance and then disable the Visual Effects (by choosing None).
If it solve your problem, then it's  compiz related, and maybe video driver related.

Yep, it was the Visual Effects causing the problem. I selected None and the problem went away. Now I have to figure what I need to do to get compiz working and/or make sure the correct video driver is loaded for my ati chipset. This wasn't a problem in 9.04. Oh well.

---

### Post by Turtle.net on 2009-11-01
Good !
Now we have to figure out what happened to your video driver.
First you should do ```
lshw -C network
``` and post the result.
You should also search the forums for your video card and driver.
I had a similar problem with nVidia driver. I installed the latest version 190 and solved my problem.

---

### Post by axel_2078 on 2009-11-01
> **Turtle.net said:**
> Good !
Now we have to figure out what happened to your video driver.
First you should do ```
lshw -C network
``` and post the result.
You should also search the forums for your video card and driver.
I had a similar problem with nVidia driver. I installed the latest version 190 and solved my problem.

Below are my results. I didn't notice anything about the video though.

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b7:99:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:9 ioport:4000(size=256) memory:d0200800-d02008ff
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:9
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:3d:4d:29:94
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.15.134 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:9 memory:88000000-8800ffff

I also ran lspci and found this info about my video:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

---

### Post by Turtle.net on 2009-11-01
My mistake ... I told you something stupid :(
```
lshw -C video
```
would be more appropriate
But now at least you know what to do if you need info on your network connection hardware :)

---

### Post by Turtle.net on 2009-11-01
On another note, if you have an ATI Radeon card, is it detected by System->Administration->Hardware Drivers. If yes the correct driver should be suggested.

---

### Post by axel_2078 on 2009-11-01
> **Turtle.net said:**
> On another note, if you have an ATI Radeon card, is it detected by System->Administration->Hardware Drivers. If yes the correct driver should be suggested.

Hardware Drivers didn't find anything. I got "no proprietary drivers found".

Running lshw -C video yields the following:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:d8000000-dfffffff(prefetchable) ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)

It seems to recognise that I have a Radeon Mobility chipset, but I guess there's no driver loaded for it.

---

### Post by Turtle.net on 2009-11-01
I never had a Radeon card, but I guess that Synaptic, then search fglrx and install xorg-driver-fglrx should be what you want to do.
I guess that you'll have to change the driver in xorg.conf to point toward fglrx (don  forget to create a backup copy of xorg.conf just in case).
After you installed that, log out and log back in (loging out will restart Xserver).
Keep us posted.

Good luck ;)

---

### Post by KingStill on 2009-11-03
I have radeon 9200 and I too get the black wallpaper and black maximized windows on Karmic. Booting with radeon.modeset=1 fixes this, but introduces font tearing that gets progressively worse and adding radeon.agpmode=-1 fixes that bug, but performance suffers. ](*,)

---

### Post by emptybox on 2009-11-03
Have a look in this thread.

[http://ubuntuforums.org/showthread.php?t=1308027&page=2]("http://ubuntuforums.org/showthread.php?t=1308027&page=2")

It provided a solution for me, albeit not a perfect one. :)

---

### Post by axel_2078 on 2009-11-03
I found a better solution...I reinstalled 9.04. It fixed this problem and many others.

---

