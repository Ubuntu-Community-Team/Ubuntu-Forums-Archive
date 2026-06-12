---
title: "Upgrade issues: won't read monitor"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by jsdieorksw on 2009-06-11
I'm having some issues after the jaunty upgrade. I've searched the community, ubuntu wiki, and even google but I can't seem anything that helps with my particular issue.  I've upgraded to jaunty a few days ago and now it seems that ubuntu doesn't recognize the monitor.  It seems to boot fine (at first; I can see the first Compaq boot screen so I know that I can still work with the computer) but then the screen goes black and I get a message that reads "input signal out of range".  Any help would be greatly appreciated.

---

### Post by Bartender on 2009-06-11
What kind of monitor you got?  If it's LCD, find a good old 17" or 19" CRT monitor and plug it in.  Betcha Ubuntu is sending out a real basic 640X480 signal to the monitor and the LCD doesn't know what to do with it.  A CRT will display pretty much anything sent to it.  LCD's are fussier.
Much easier to troubleshoot when you can see something, eh?  What piece of hardware is running the video?  Onboard? Discrete card?  Need exact description of graphics chip.

---

### Post by jsdieorksw on 2009-06-11
It's an LCD, I have a Compaq 5017  I'm also not sure of the graphics card, I'm kinda ignorant when it comes to doing stuff outside of the normal desktop so i'm not sure as to how find this without being to see anything on the normal desktop. The only thing I do know about the graphics card is that it's an nvidia (that probably doesn't help but it's all that I know right now)

---

### Post by Bartender on 2009-06-12
Find yourself a CRT, get your desktop going, go into System>Admin>Hardware Drivers and see if Ubuntu says anything about a driver package for your nvidia hardware.  If you're able to connect to the internet, let it get the drivers it identifies, reboot, see if you can set resolution to your LCD's native display in Display settings.

---

