---
title: "Automated backup solutions?"
date: 2008-09-16
forum: General Help
---

### Post by Roasted on 2008-09-16
Currently, we have 6 computers in the house. All of which have a shared directory to my 250gb hard drive in my computer through Samba. Once the others in the house write data to it, it is essentially saved on my computer. From time to time, I run an rsync script, which copies that 250gb drive to another 250gb drive. Kind of like a manual mirror, if you will.

Thing is, I'm 22 years old. I may be moving out within the next 2 years. I'm curious to know what kind of automated backup solutions are available.

I plan to leave my old system here whenever it is that I leave. It's just a Socket 939 AMD single core, and my MSI mobo has 3.0gb/s HDD ports on it. So if I can somehow have the Win XP Pro machines (and possibly Vista machines in the future) synchronize their "my documents" folder to their designated share on my system, THEN rsync everything periodically throughout the day to the other hard drive, that'd be great.

That's my idea... auto-sync their stuff to my computer, then using crontab (I guess) have the rsync script run itself say... 3 times a day.

Is there an option like this? Something completely automated so I can live in fricken Hawaii and not have to come over to mess with it all the time?

---

### Post by bodhi.zazen on 2008-09-16
With your background +1 on running rsync from cron

does it really need to run 3x / day ? I would think once a day would be sufficient.

---

### Post by Roasted on 2008-09-16
Yeah, even once a day would be fine. At like 4 am or something would be perfect.

I'm not worried about the rsyncing thing. I've done it ever since I started on Ubuntu. The area I'm not sure of is automatically synchronizing data from their "My Documents" folder to the remote Ubuntu machine. Right now, they just start-run-192.168.my.machine and it routes them to their shared drive via Samba.

If I can automate that so they would NEVER have to start-run anything and everything would auto-sync to the Ubuntu machine, it'd be PEEERFECT.

---

