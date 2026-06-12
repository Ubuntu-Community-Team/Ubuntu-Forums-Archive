---
title: "Battery Life Wiki?"
date: 2008-04-26
forum: Hardware
---

### Post by zackiv31 on 2008-04-26
I've read numerous posts about the awful battery life in Ubuntu... and since I've recently fresh installed Hardy Heron 8.04 on my laptop I get nothing better.  Vista still about doubles my battery life over Hardy... which is NOT what I expect out of the box.

Is there a battery life wiki or step by step instructions of how to improve/get back my battery life on Ubuntu (Hardy)?

If it matters, I have a Lenovo X61 tablet.

---

### Post by NiklasV on 2008-04-26
[http://www.lesswatts.org/](http://www.lesswatts.org/) is pretty nice, not a wiki though. Its run by Intel.
I also have an X61 Tablet and I get about 4-5 hours out of my 8-cell battery when I lower the brightness of my screen to lowest level and implement some of the tips on lesswatts and from powertop.

---

### Post by zackiv31 on 2008-04-26
I guess I was looking for something a little more Ubuntu specific... but this is a start...

I've noticed that Fedora runs a lot better (concerning battery life) right out of the box... where has Ubuntu gone wrong?  My configuration is pretty much top of the line and I'm getting this horrendous battery life.

---

### Post by NiklasV on 2008-05-06
If your fans are constantly running, like mine did, try installing thinkpad fan control: [http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)
Not having the fans running constantly easily cuts down on power usage by over one watt. I found out that my fans were set to go off at 15 C, far too low.
Now my power usage hovers around 12 watts according to powertop, providing about 6 hours on a full charge with my screen dimmed to minimum and the suggestions in powertop activated.(again according to powertop, I haven't had these settings for long enough to see if its correct)

---

### Post by tlawson on 2008-05-09
NiklasV, do you happen to have a profile for your fan settings to give to tpfand/tpfan-admin?  If not, what settings have you been using?

---

