---
title: "Nvidia Geforce 740m"
date: 2014-09-09
forum: Hardware
---

### Post by SLaCK3r on 2014-09-09
I have an HP Envy 15TS laptop and I've ran into plenty of problems with the RTL8188EE wireless card, but I fixed that problem by replacing it with an intel one. 

Now I want to be able to use my graphics card! I see the drivers listed as a recommended driver (331.38) but does it automatically switch like in Windows? Or do I have to do something special to use it? Because I don't play games, but if a program wants to use my gpu, I would like for it to be able to -- only if I don't have to manually switch back and forth between integrated graphics and my GPU. Otherwise I'm just going to use the integrated. 

Currently using the nouveau drivers I believe.

---

### Post by grahammechanical on 2014-09-09
This was reported during the development period of 14.04. So, it should be standard in the released 14.04

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

 The Nvidia driver mentioned is 319 but 331 is now also available. When you install the Nvidia driver check in the Nvidia Xserver settings manager. You should find this

> [COLOR=#333333][FONT=Arial]Thanks to the latest nvidia-prime, we can also see a change in [/FONT][/COLOR]**Nvidia Settings that [landed]("https://launchpad.net/ubuntu/trusty/+source/nvidia-settings/331.20-0ubuntu5")about two weeks ago in Ubuntu 14.04 Trusty Tahr: an [B]additional tab was added, [B]allowing users to switch between GPUs:**[/B][/B]**[B]**[/B]

You might also want to install the Prime Indicator

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

