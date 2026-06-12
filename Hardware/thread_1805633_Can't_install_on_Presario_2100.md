---
title: "Can't install on Presario 2100"
date: 2011-07-16
forum: Hardware
---

### Post by 567 on 2011-07-16
Have tried regular ubuntu install cd, alternate cd, and xubuntu alternate and its always the same unresponsive at the boot screen. With the alternate cds it brings up language selection menu but i'm not able to select anything, as if the keyboard doesn't work, I can only turn off the power. I thought the alternate cds were supposed to be all text so I don't know why it brings up that menu. How could I make this work? The laptop model is 2135US.

---

### Post by Ralph L on 2011-09-20
I have a Presario 2100 (2195us) on which I am trying to install Lucid.  I first tried to install Natty, but while the Live CD would startup and get to the point that it showed the desktop, I was unable to get a response when I clicked on the Main Menu bar.  Lucid responded ok and I installed it, but I am still in the process of working through the problems.

One thing I noticed with both Lucid and Natty Live CDs was that after boot they would display a tiny icon with a man in a wheel (and another tiny icon that I didn't recognize) and stop.  I found that if I hit the escape key at that point, I would get the language menu and then the normal menus.

A major problem, running from the Live CD and from the installed Lucid, was that it was unbearably slow in bringing up menus, doing drag and drops, etc.  I found two workarounds.  First, was to go to System>Preferences>Appearance>Visual Effects, and click "None".  This speeded things up a lot.  I think there is probably a driver problem with the ATI Radeon IGP 320M (U1) graphics card.  I am working on that.

Second, I found a blank spot on the Main Menu panel, right clicked, selected "add to panel" and added "CPU Frequency Scaling Monitor" to the panel.  Clicking on this panel icon allowed me to select "Performance".  Immediately my percentage cpu usage (System Monitor) dropped in half, and the system became much more responsive.  I don't like having to do this, because I think having the cpu run always at high speed speed will reduce battery life, but for now I am doing it.

I also have a problem with a jittery touchpad pointer (it is fine under XP) that I am working.  In addition, I can't get the wifi to work and I am also working on that.

Don't know if this will help any, but maybe.  I'll try to keep monitoring this for a while, in case anybody has questions.

Ralph

---

