---
title: "Monitor change when docking/undockiqng"
date: 2008-05-14
forum: Hardware
---

### Post by Strunker on 2008-05-14
Hi!

I have a Dell Latitude D630 and a docking station D/Port. I have a problem with my XServer when docking/undocking.

I'd like to use the external monitor when docked and the internal when undocked. Everything works fine if the XServer gets started. Then the correct monitor is used. But when I dock/undock my laptop the enabled monitor isn't changed until I restart my XServer which means to quit all X applications.

Is there any way to tell X to redetect the available monitors? Or is there a way to change the currently used MetaMode using a command-line tool? I tried to use xrandr and nvidia-settings to do so but without luck. 
In /var/log/messages I can see the dock/undock events. So my idea is to react on that events and change the MetaMode myself via a hal script. Is there anyone who has tried someting similar?

By 

 Karsten


OS: Ubuntu 8.04


Part of xorg.conf:
=================

Section "Device"
        Identifier      "nVidia Corporation G80 [Quadro NVS 135M]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Option          "TwinView"      "1"
        Option          "TwinViewOrientation"   "clone"
        Option          "SecondMonitorHorizSync"        "31.0-83.0"
        Option          "SecondMonitorVertRefresh"      "56.0-75"
        Option "NvAGP" "2"
        Option "NoLogo" "1"
        Option "Coolbits" "1"
        Option "NoPowerConnectorCheck"
        Option "UseDisplayDevice" "dfp-1"   # external display
        Option "MetaModes" "1680x1050,NULL; NULL,1440x900"
        Option  "UseEdidFreqs"                  "yes"
EndSection

---

### Post by cacycleworks on 2008-05-15
This is a great question... I'm replying in hopes to learn more about my D630 and docking / monitors with the answer. 

My current solution is that I dock/undock while powered off... I don't have need to undock and keep the laptop on. At home, I plug a 19" monitor in the back of the D630, but I treat it the same way.

Soooo... a reply to your post might help me learn how to make my computer more productive for me.

:) Chris

---

### Post by lecter255 on 2008-05-16
I have a similar problem. I am using a HP dv2000 and I wish to connect an external monitor and use it. So far, I can connect an external monitor and display a resolution up to the max resolution on my laptop's monitor, which isn't very useful because my laptop screen's resolution is 1280X800 while my external monitor is 1920X1200. Does anyone know how to utilize the external monitor fully? 

Right now I go to System->preferences->monitor resolution to set the external monitor resolution but it only goes up to 1280X800

---

### Post by Strunker on 2008-05-18
I can dock/undock my laptop while running. With my above xorg configuration I can switch between my internal and my external monitor but only by restarting X. If an external monitor is attached it is used, otherwise the internal one is used.

I'm searching for a way to change monitors without restarting X when docking/undocking. Does nobody has a solution for that?

---

### Post by cacycleworks on 2008-05-20
> **lecter255 said:**
> I have a similar problem. I am using a HP dv2000 and I wish to connect an external monitor and use it. So far, I can connect an external monitor and display a resolution up to the max resolution on my laptop's monitor, which isn't very useful because my laptop screen's resolution is 1280X800 while my external monitor is 1920X1200. Does anyone know how to utilize the external monitor fully? 

Right now I go to System->preferences->monitor resolution to set the external monitor resolution but it only goes up to 1280X800

Hi Lecter,

If you can have the monitor attached when either powering on your laptop or maybe at least restart the X server, it should see the extra size. If you are already using screen 1 (the built in one), it will try and resist you going larger. Yes, there probably is a way to have X refresh, but I am not sure how this would be.

Best,
Chris

---

