---
title: "Power-Off Retract count increasing (head parking) on Dell XPS L702X &amp; quick fix."
date: 2012-08-12
forum: Hardware
---

### Post by Greggyboy on 2012-08-12
Just thought I should share this with the community, I had a issue with the 'Power-Off Retract Count' increasing with my Dell XPS L702 & Xubuntu 12.04. I tried the usual stuff like installing laptop-mode, turning the power mangement off (stupid), etc, but nothing worked and the Power-Off Count kept increasing. Head parking issues again??? Sheesh!!! :mad:

Then I installed lm-sensors & applet (xfce4-goodies to be exact), added the applet to my panel, selected the hdd to monitor and no more clickity click and no increase to the Power-Off Retract count. Must be keeping the drive 'alive' so to speak.

Now I know this is a drive manufacturer issue but it doesn't look like they are going to fix it ever, so ubuntu needs a more permanent fix and not a 'work around' like disabling power management on the drive altogether which probably does just as much harm as the parking.

Anyhoo, I hope this helps someone out. :)

---

