---
title: "Is my hardware to old to run Gusty Gibon sufficiently (CPU Load like crazy)"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by comfortablynumb on 2007-10-24
I just did an upgrade from Fiesty Fawn, I don't recall ever having any issues with Fiesty. I've noticed with Gusty my system is running pretty slow, if I go to Resources and check CPU  it's constantly in the 90 to 100% range. I checked the processes and nothing shows it's using any high cpu resources, everything says sleeping a few are like 2%.

I disabled special effects, I took off my desktop background and did an fschk, not sure where else to go at this point, I really don't want to have to do a clean install if at all possible.

My system specs:
- AMD Duron 1400
- Crucial 512MB DDR PC2700
- Themaltake 430 watt PSU
- Geforce 2GTS 32mb
- ECS Mobo (KT266)
- Maxtor 20gb PC133 HD

---

### Post by Mud.Knee.Havoc on 2007-10-24
This system is loads to run Gutsy.  I'm running an AMD 1200 with 768MB of RAM and it's fine.  Under Edgy, I found that 512MB or less RAM wasn't enough and it would hit the swap too often.

I recommend installing htop in order to check your system resources/processes.  It's a nice, clean console-based tool that pops up a lot quicker and explains a lot more when you're having serious resource problems.  This should help you a bit more than the one you're using.

If you ask around, I'm sure somebody's got a 256MB stick of PC2700 RAM in some old computer that they're not using.  If you add that to your computer, you'll notice a difference... if you can snag a half-gig stick, you'd think you bought a new computer. :D  If you toss on a larger hard drive, as well (if you go to a smaller computer store, you can get a 160 gig drive for about $60 - the big box stores tend to charge about $40 more for the same thing), you could definitely have a decent machine.

As I said, I've got an old 1200 with less than a gig of RAM, a 64MB video card (I don't even bother with the nvidia drivers, though! I don't play games), and about 350GB of hard drive space.  With this machine, I can have Deluge or Azureus running in the background all day long (with 6-10 torrents), Quod Libet for music, Firefox, Pidgin and a mail program - all running at once on four different workspaces.  And it all runs smoothly!

---

### Post by Ryangarve on 2007-10-24
I am currently running on a Toshiba Satellite with 512 ram and a 1.6 Celeron processor.
Mines runs very fast with very little trouble, I was having a little trouble with occasional jumps to max capacity, but after running a few updates they have seen to go away.  I would try checking all your updates and installing any critical apps.

---

### Post by comfortablynumb on 2007-10-24
Thanks for the replies, since my last post my CPU has dropped to 12% and become more stable but it still is peaking ocasionally for some odd reason. I'm in synaptic now downloading Htop I'll see if i can get any further with that.

Also I have all the latest updates.

Edit:
Running HTOP now Mem usage is pegging out pretty good 290MB, the only thing I'm running is Htop and Firefox(2.0.0.8 ) with 3 Tabs

---

### Post by Mud.Knee.Havoc on 2007-10-27
Don't pay too much attention to memory usage.  Lots of guys who are used to Windows flip out and think that they're having problems with excessive memory usage (but it's very rarely a problem, it's just the way that linux deals with memory).

If you're having 100% CPU usage and you're not doing much of anything, you've probably run into a bug. :D

---

