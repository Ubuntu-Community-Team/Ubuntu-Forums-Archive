---
title: "HP Docking station audio"
date: 2015-04-29
forum: Hardware
---

### Post by vpopescu on 2015-04-29
I have a HP EliteBook 9470m with a HP [UltraSlim docking station]("http://h20565.www2.hp.com/portal/site/hpsc/public/psi/home?sp4ts.oid=5450893&ac.admitted=1430279494591.876444892.492883150"). I've managed to work my docking script to my liking, but I have yet to figure out how to redirect audio through the dock (it's not happening automatically). I have two speakers connected to the dock, and audio is redirected fine when I dock a windows machine. But in Linux, the sound continues to come through the docked laptop's internal speakers.

The only new things that show up after docking are my external mouse, keyboard, and an extra SMSC hub.

```
< Bus 001 Device 009: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
< Bus 001 Device 008: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
< Bus 001 Device 007: ID 0424:2134 Standard Microsystems Corp. 

```

ALSA info dump: [http://www.alsa-project.org/db/?f=acf1f2f8014e4e6eeb3326da90b95d50f7f16d62](http://www.alsa-project.org/db/?f=acf1f2f8014e4e6eeb3326da90b95d50f7f16d62)

Can someone help me figure out what's supposed to be happening? I can't see any hints comparing alsa, udev, or acpi during the transition, but I don't fully understand how the dock audio redirect is supposed to work.

I am getting the same behavior with both 14.10 and 15.04. I'm currently on 15.04.

---

