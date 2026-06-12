---
title: "bizzare performance issue (cpu usage drops - system freezes)"
date: 2012-01-08
forum: Hardware
---

### Post by durilka on 2012-01-08
My config: 
11.10 on Acer 5750Z (2core B950, builtin graphics), 64bit, Xfce on regular ubuntu. Everything worked out of the box but.

Every minute or so i have strange cpu usage drops. It's especially good visible when watching video. Every now and then (with granularity of 30 sec - 1 min) player freezes for about 4 seconds (audio goes on). During this time cpu graph shows drops from 30% to 10% on both cores which explains why player can't decode video. But i've got no explanation on what can cause those "energy savings". I've tried playing with different governors (my initial hypothesis) but no luck.

Honestly i'm completely lost and this is really irritating (even typing something lengthy is affected and waiting 4 seconds for text to appear on screen is so nineties). And this happens not in the os the notebook was shipped with, so it's apparently problem with ubuntu and i'd really love to solve it.

So, ideas where to look?
Thanks.

---

### Post by durilka on 2012-01-09
Instead of mindless bumping i'll be adding details to the initial post.

By freeze I mean X window system. Mouse moves, I can switch windows and do something somewhere else (most of the time). My feeling is that it's current window only.

**update**
right now i'm installing maven2 which is somewhat monstrous install and imo monstrous tool as well (i definitely lack knowledge on the subject) but apart from my sentiments the system turned barely responsive. strangely it responds and mplayer still plays music(chosen as most lightweight and robust player so far given the circumstances), i can switch windows and they pretend to be white, but really often, clicking somewhere turns them gray. chromium for instance offered me killing ubuntuforums page for it was loading too long.

the strangest of them all is that cpu usage barely jumps over 50% and i'm talking about dual-core system (yes, still a cheap but new notebook with intel B950 processor)

attached are screenshots of the system monitor with resolution of 1 second and 250ms (where 10% is used by system monitor alone)

and here's my uptime:
18:54:41 up  9:27,  5 users,  load average: 7.77, 6.17, 5.58

which is enormous for two-core system and doesn't fit with the system monitor. somebody's lying here...

whom should i trust? and more importantly where should i look?

which reminds me of this joke:
Bill Gate's son comes to his dad and asks "Dad, what's multitasking?" And father answers "Wait a second, son, i'll just finish formatting this floppy disk..." (yes, it's dated back into mid-90s)

---

### Post by durilka on 2012-02-17
my little blog is so lonely here.

small update. i converted the root fs from btrfs to ext4 and removed home folder encryption. now it's much better and also strange READ FPDMA QUEUED are disappeared.

---

