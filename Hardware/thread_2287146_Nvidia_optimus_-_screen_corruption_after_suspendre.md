---
title: "Nvidia optimus - screen corruption after suspend/resume sometimes"
date: 2015-07-17
forum: Hardware
---

### Post by planetf1 on 2015-07-17
I have a Lenovo Thinkpad W530. This has an Nvidia Optimus graphics setup - ie a combo nvidia/intel environment.

In the office I use
 - internal LCD screen
 - miniDisplayPort -> HDMI -> ext  monitor
 - docking station -> DVI -> ext monitor

I use KDE plasma as the desktop environment

Using the nvidia proprietary driver in kubuntu 15.04 I can happily use all three screens as a single virtual desktop. Performance seems fine, and it also happily flips back to internal screen only when at home/out&about. The driver is 346.59

However fairly often (can be multiple times a day) when I open the lid of my laptop (after blank or more likely suspend/resume) I get a very pretty form of screen corruption - here's an example: [IMG]https://dl.dropboxusercontent.com/u/3224841/Bugs/2015-06-22%2014.51.32.jpg[/IMG]

Or sometimes without the screen lock:[IMG]https://dl.dropboxusercontent.com/u/3224841/Bugs/2015-07-10%2008.32.34.jpg[/IMG]

I then tried a private PPA (mmarley/nvidia) which provides a build of 352.21 with exactly the same results!

nouveau does NOT result in the same issues, but I struggled with 3 monitor setup.. perhaps worth revisiting, but I wondered if anyone else had such nvidia issues and what possible causes/things to try might be? It seems pointless raising a launchpad issue since this driver is nvidias....

Nigel.

---

