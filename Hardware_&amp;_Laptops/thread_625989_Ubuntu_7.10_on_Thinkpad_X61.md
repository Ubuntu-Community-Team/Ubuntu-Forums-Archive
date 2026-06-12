---
title: "Ubuntu 7.10 on Thinkpad X61"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by GoblinInventor on 2007-11-28
I'm currently running Ubuntu 7.10 on a Thinkpad X61, and experiencing most distressing problems.

At times (and I only say that because I have not been able to quantify exactly what I'm doing that makes this happen) it will totally lose track of the wireless. i.e. suddenly it will "forget" that there is a wireless card in the computer, and I have to go to USB wireless, which doesn't work very well either.

It also is having some major slowdown problems. Like it is lagging while I type something into gedit. Although sometimes it does very well. I was able to run Nexuiz without incident for a while (although now, with no internet, I can't test it really (the USB wireless won't consistently work, so that makes it hard)).

Other than that I'm having trouble with Wine, but that's waaayy above my current concerns. Basically I just want to have my wireless working and my computer not to crawl.

Thanks,

Michael

---

### Post by crouton on 2007-11-29
If you can get some kind of log output of what happened when it 'lost' the onboard wireless, it'll help.  Off the cuff it sounds like the module is powering down...

---

### Post by sheol on 2007-12-08
> **GoblinInventor said:**
> I'm currently running Ubuntu 7.10 on a Thinkpad X61, and experiencing most distressing problems.

At times (and I only say that because I have not been able to quantify exactly what I'm doing that makes this happen) it will totally lose track of the wireless. i.e. suddenly it will "forget" that there is a wireless card in the computer, and I have to go to USB wireless, which doesn't work very well either.

It also is having some major slowdown problems. Like it is lagging while I type something into gedit. Although sometimes it does very well. I was able to run Nexuiz without incident for a while (although now, with no internet, I can't test it really (the USB wireless won't consistently work, so that makes it hard)).

Other than that I'm having trouble with Wine, but that's waaayy above my current concerns. Basically I just want to have my wireless working and my computer not to crawl.

Thanks,

Michael

Two things I've noticed with mine:
1) There is a little switch on the front of your computer.  You need to make sure this switch is set so that you can see green.  This switch is to enable and disable wireless.

2) Try disabling wireless, and then wait 30 seconds, and then reenable wireless.

3) see if it is a problem with the wireless applet.  Try running iwlist scan in a terminal, and see if you get any results.

---

### Post by zorkerz on 2007-12-23
What are you wine problems? 
Im getting logged out of ubuntu every time i try to use an opengl app in wine.

---

