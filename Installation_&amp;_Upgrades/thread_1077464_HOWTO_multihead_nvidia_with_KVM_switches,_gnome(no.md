---
title: "HOWTO: multihead nvidia with KVM switches, gnome(no) KDE(no) and Xfce (yes)"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by monty95 on 2009-02-22
Intalled 8.10 (Intrepid) for AMD64 on a system with a PNY/NVIDIA Quadro NVS 440 four-headed display card.

This card provides two physical display interfaces, each of which can drive two physical displays (tubes or panels).

Used NVIDIA driver version 180.29 from
[http://www.nvidia.com/object/linux_display_amd64_180.29.html](http://www.nvidia.com/object/linux_display_amd64_180.29.html)
which was more recent than the driver available in the repositories.

The NVIDIA configuration scripts did not satisfactorily configure the second physical display interface, probably because one of the two tubes on that device (an AcerView 76i) is too old to provide EDID and the other (a ViewSonic A90) is connected through a D-Link DKVM-2K KVM switch that seems to block EDID. The two physical displays on the first physical device (one Acer X221W LCD panel and one ViewSonic A90-2) are connected via Belkin 4-Pro KVM switches that *do* pass EDID.

Had some trouble getting the modes right. Setting ```
Option         "ModeDebug" "TRUE"
``` let me see what was malfing.

I hand-tailored the attached /etc/X11/xorg.conf to provide two X11 screens, each using NVIDIA Twinview to cover the two physical displays on one of the two physical display interfaces.

Ubuntu's Gnome GUI now had two desktops, each covering the two physical displays attached to one of the two physical display interfaces, but trying to launch an application on the second desktop made the gnome-panel daemon process go into an infinite loop. Killing the daemon process made it relaunch itself and restore function to the first desktop, but I was unable to find a way to make the second desktop usable. Googling gave me the impression that the problem may be a long-standing bug in gnome-panel, but I did not dig very deep.

I next used the Synaptic package manager to add the kubuntu-desktop package, rebooted, selected a KDE session from the session manager on the sign-in screen and logged in.

KDE provided a single desktop covering the two physical displays on the first physical display interface, and a logical X screen without a desktop on the second physical display interface. I could launch applications on the second logical X screen by using the -display :0.1 argument on commands issued from a console window on the desktop, but the windows containing those applications could not be resized or moved around. I was unable to find a workaround for this problem either. I found a recipe for *getting* to this configuration, given a KDE system with a desktop on each logical X screen, but my attempts to invert that recipe were unsuccessful.

I next used Synaptic to remove kubuntu-desktop and all the kde packages and then to install xubuntu-desktop.

Relogging to an Xfce session produced the effect I'd been trying for all along: a desktop on each of the two logical X screens, with applications launchable on each of the two desktops.

I did not try Xinerama. If it worked, Xinerama could fuse all four physical displays into a single logical X screen. However, I have been following the xorg mailing list, and have formed the impression that the developers are ripping Xinerama out because it conflicts with xrandr.

---

