---
title: "Ubuntu 10.10 picture artifacts"
date: 2010-12-17
forum: Hardware
---

### Post by keraman on 2010-12-17
Since 2 weeks i frequently get some bigger artifacts on my screen:
_[[IMG]http://img828.imageshack.us/img828/405/artefakt1.th.png[/IMG]]("http://img828.imageshack.us/i/artefakt1.png/")_

Is this a known bug?

I use the proprietary drivers by ATI. Samsung R522, Mobility Radeon HD4650.
Edit:
These artifacts go away after I log off and on again.

---

### Post by OuahabiX on 2010-12-18
It has been happening over here for sometime now, it happened on both my laptop and desktop, and even on my friend's laptop as well, it's getting quite annoying but at least it can be fixed up without logging off/on each time it occurred, just type in the Terminal or use (Alt+F2):

*metacity --replace*

The problem first appeared after upgrading to the 10.04 release, I had never been stuck with this issue before though, and I believe it has nothing to do with the Driver itself since I experienced the same problem under nVideo GeForce, ATI and Intel GPUs' Chipsets, so it has something to do with the refresh rate or something related to Gnome.

_____
Edit:
Somebody reported it on Launchpad and somehow they thought Shutter was responsible for this! I still can't think of what's happening in reality!?

Try to open a ticket there and I'll follow you, just submit the link here afterwards to keep a watch on it.

---

### Post by keraman on 2010-12-20
Thanks for the reply I'll test that.

Edit:
Okay it works. I hope that this will be fixed soon.

---

