---
title: "Karmic LiveCD &amp; Boot Issue"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by urlacher3292 on 2009-10-31
I am having a problem booting into Karmic from the LiveCD unless I use the Intall Ubuntu option, which works perfectly. After installing Karmic refuses to boot, only getting as far as the splash screen. When booting to Karmic from the CD, It almost logs into Gnome, but after the panels appear, with no applets, the CD freezes without even the desktop picture appearing. The CD's are ones I have burnt myself, but have been verified with Nero (Windows). If this is a graphics driver problem (Intel 82845G). What are my options.

---

### Post by aheckler on 2009-10-31
Can you boot into safe graphics mode, or whatever it's called now?

---

### Post by urlacher3292 on 2009-10-31
> **aheckler said:**
> Can you boot into safe graphics mode, or whatever it's called now?

I'll try that again, but I think I already have, and it didn't work.

Edit:As it turns out waiting long enough (it takes a while) allows both the Live CD and the installed system to boot. Now it's just the matter of getting my NVIDIA card to work over top of my Intel graphics chip. Thanks for the help aheckler.

Edit2:The only problem now is blacklisting my onboard Intel card. Adding blacklist intel_agp & blacklist agpgart to /etc/modprobe.d/blacklist.conf doesn't seem to work anymore. I'm almost ready to give up jaunty for karmic, I just need this one issue resolved.

---

