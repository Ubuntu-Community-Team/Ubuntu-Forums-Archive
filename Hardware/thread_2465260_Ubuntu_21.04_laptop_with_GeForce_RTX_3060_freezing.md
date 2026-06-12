---
title: "Ubuntu 21.04 laptop with GeForce RTX 3060 freezing"
date: 2021-07-27
forum: Hardware
---

### Post by tezrik on 2021-07-27
[COLOR=#333333][FONT=DIN-Web-Pro]Ubuntu 21.04
kernel: 5.13.5-051305-generic
CPU: AMD Ryzen 7 5800H
Graphics: Nvidia GeForce RTX 3060[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]nvidia-driver-470 installed via the Ubuntu Additional Drivers repository[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]After install nvidia driver and restart , the display always freezes
While in recovery mode I run nvidia-bug-report.sh. The output is here:
[ATTACH]288885[/ATTACH][/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]Can anyone suggest what I should to do to get this working properly?[/FONT][/COLOR]

---

### Post by Autodave on 2021-07-27
Sorry.....didn't read it right the first time.  Please give us info on the laptop: make and model?  Since it has a rather powerful RTX 3060, I would also assume that there is a lesser power consuming graphics adapter in there also and the laptop is trying to use the lesser one with the nVidia driver.

---

### Post by tezrik on 2021-07-28
HP Laptop 15-en1039ur

---

### Post by tezrik on 2021-07-28
[COLOR=#333333][FONT=DIN-Web-Pro]decided
I am remove /etc/X11/xorg.conf
and add in directory /etc/X11/xorg.conf.d[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]10-nvidia.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]Section &#8220;OutputClass&#8221;
Identifier &#8220;nvidia&#8221;
MatchDriver &#8220;nvidia-drm&#8221;
Driver &#8220;nvidia&#8221;
Option &#8220;AllowEmptyInitialConfiguration&#8221;
ModulePath &#8220;/usr/lib/x86_64-linux-gnu/nvidia/xorg&#8221;
EndSection[/FONT][/COLOR]

---

