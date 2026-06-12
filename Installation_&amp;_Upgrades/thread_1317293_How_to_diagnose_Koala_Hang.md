---
title: "How to diagnose Koala Hang"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-11-06
I am encountering frequent hangs while running 9.10 (Koala).  This is disappointing, but it is a brand new release so I only have myself to blame for jumping in as soon as it was available.

The cursor still moves in response to the mouse, so clearly much of the system is still operational, however the system does not respond to the keyboard or to clicking on any icons.  So far the only action I have found to deal with the hang is holding the power button down until the hardware shuts off.  This is annoying when the system is clearly still operational.  If OpenOffice would get around to using logged rather than periodic save recovery I wouldn't have so much work to repeat when the system comes back up, which is a further annoyance.

Meanwhile I would like to contribute to documenting this hang.  Is there any error information recorded through a power off/on that I could submit?  Or is there some some trick to restart the window manager when the keyboard is apparently dead?

---

### Post by Spooky257 on 2009-11-06
I look forward to where this thread goes.  I'm suffering the same problems.

---

### Post by jcobban on 2009-11-06
I wish someone would at least explain to me how I can get the attention of whoever is responsible for Koala.  This is a show stopper folks!

I know that it is only the window interface, because the Apache server running on the Linux box is still running, and accessible from other computers on the network.  I could probably telnet in from one of those systems, but I need to know what to do once I have got into the system.

---

### Post by Spooky257 on 2009-11-07
I found something that is working for me.  I've been running all night without a hang up since running this procedure.  I'm not sure what's going to happen on the next update but I'll cross that bridge when I get to it.  Now to try and get my sound working again.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by jcobban on 2009-11-07
> **Spooky257 said:**
> I found something that is working for me.  I've been running all night without a hang up since running this procedure.  I'm not sure what's going to happen on the next update but I'll cross that bridge when I get to it.  Now to try and get my sound working again.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Since not everyone is encountering this problem, it is understandable that it might be connected with the Intel graphics on the computer that is giving this problem.  I know that there has been change to that driver in Koala because in Jackalope I could not do a suspend;  When I resumed the display was corrupted, not as badly as it had been in Heron, but still to the point of being unusable.  Suspend/Resume works now, as long as I do not suspend for more than 24 hours.  This specific entry is with regard to problems in Jaunty, that required reverting to an even earlier version of the driver, however the principle is likely applicable.

---

