---
title: "HP XW8200 running Ubuntu 14.04 crashes/freezes"
date: 2015-04-22
forum: Hardware
---

### Post by IZavorin on 2015-04-22
This morning I installed Ubuntu 14.04.2 on a 64bit HP XW8200 workstation. It's an machine that used to run Win XP but has enough power to run Ubuntu smoothly.

However, twice today I noticed that the machine either froze or crashed, i.e. it did not respond to mouse or keyboard and I had to cold restart it. I don't whether it's Ubuntu glitching or it's a hardware problem. I checked various logs in /var/log/ but did not see anything pointing to one or the other. Ubuntu Power settings (in System Settings) seem to be normal. 

How can I determine the cause?

Thx much!

---

### Post by weatherman2 on 2015-04-22
When it "freezes" can you hit Ctrl - Alt - F2 to enter terminal mode?  If so, then it's not a hardware freeze most likely.  But if Ctrl Alt F2 does nothing, perhaps it is.

Did XP work well on the old machine?  A machine that old might also have an old hard drive - have you tested it?  I recommend GSmartControl to check the S.M.A.R.T. status and attributes to see if any (highlighted in red) might be flagged.

Running Memtest for at least a short time might be a good idea, too.

Any chance the freezes happen when the screen might go black (a power saving mode, after a period of inactivity)?  Or do freezes happen at random times, even when you are typing something?

Other possibilities with a machine that age: CPU overheating (heat sink dirty or clogged, fan not working), failing power supply, or failing motherboard.

Of course, it could be entirely software and not hardware at all.  Ruling out hardware problems is often easier than software.

---

