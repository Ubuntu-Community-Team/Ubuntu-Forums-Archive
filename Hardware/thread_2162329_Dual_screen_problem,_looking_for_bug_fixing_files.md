---
title: "Dual screen problem, looking for bug fixing files"
date: 2013-07-14
forum: Hardware
---

### Post by MPPP on 2013-07-14
[B]I am having trouble with dual screen, have ubuntu 12.04 as Os. 
Have a NVS 285 quadro Nvidia graphics card. When I set propriety recommended drivers to nvidia recommended my two screens work for couple of minutes (+- 15), then the ubuntu 12.04 os freezes, becomes black or everything hangs.
I found this explanation but can't find the listed files, links are broken.[/B]

One of the features that ubuntu 12.04 promised was better support for   dual-monitor however after I upgraded from ubuntu 11.10  to ubuntu 12.04   I noticed if I change the display settings it will freeze for example I   noticed:

- I  move the external monitor to the left of laptop monitor , (or above it) it freezes
- I try to turn of the laptop monitor ,so I only have my external   monitor it will freeze again. the mouse and keyboard stop responding and   the only way key that respond is
 ALT+PRINTSCREEN+K (to restart the X server)

I openned a bug in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/992778") and I tried every possible solution  after pulling my hair and not sleeping in the whole night .**Here is how I fixed it : **To fix dual monitor freeze in ubuntu 12.04 you need to install the older version of  *xserver-xorg-input-evdev*

1- Download the following two packages to your desktop:[INDENT] - [xserver-xorg-input-evdev-udeb_2.6.99.901-1ubuntu3~lp921236_amd64.udeb]("https://launchpad.net/%7Esarvatt/+archive/sru1/+build/3118994/+files/xserver-xorg-input-evdev-udeb_2.6.99.901-1ubuntu3%7Elp921236_amd64.udeb") (24.0 KiB)[/INDENT]
[INDENT] - [xserver-xorg-input-evdev_2.6.99.901-1ubuntu3~lp921236_amd64.deb]("https://launchpad.net/%7Esarvatt/+archive/sru1/+build/3118994/+files/xserver-xorg-input-evdev_2.6.99.901-1ubuntu3%7Elp921236_amd64.deb") (38.0 KiB)[/INDENT]
2- Open a terminal[INDENT] cd Desktop[/INDENT]
[INDENT] sudo dpkg -i *.deb[/INDENT]
3- Restart your computer or if you are lazy just restart the X Server (ALT+PRINTSCREEN +K)

[COLOR=#ff0000][B]Maybe this would be a solution if I could find and run these xserver files ? 
Could anyone pls help me out infinding these files so I can download them ?
Best regards and great weekend ,                 [/B][/COLOR]

---

