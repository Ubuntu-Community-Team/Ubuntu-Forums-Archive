---
title: "External HD Drive mounted as read-only after leaving it alone"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by DizzyTech on 2007-09-17
My laptop's hard drive is dying.  I see that... I had to get rid of Windows because it wouldn't boot because of corruption.  However, I can't buy a new HD (too expensive, out of warranty) and I can't get a new laptop 'til Christmas.

So, I got another solution.  Yesterday, I went out and bought a Seagate Free Agent 250 GB drive.  I promptly formatted it and installed Ubuntu on it.  After a little battle with GRUB root drives, I got it working just fine (I'm typing from it right now - it's twice as fast).  However, I noticed a little problem.  If I leave my lappy alone for a little while... I'm not sure exactly how long, it's varied... the hard drive apparently errors out and remounts as read-only.  In the GUI, I can launch no applications and do nothing.  I discovered its read-only condition after changing to the first terminal (CTRL+ALT+F1), logging in, and trying to edit, move, or copy a file.  I can't really get a quote from the logs, as the file-system is read-only at the time, but it basically gives an I/O error, spits up and EXT3-fs error, and announces it remounted as read-only.  I have to "sudo poweroff" from that point.

I'm going to assume that the drive is going to sleep at that specified time due to idling.  What do I do?  :(

---

### Post by eggdeng on 2007-09-18
Have you configured the settings in Preferences -> Power Management?

---

### Post by DizzyTech on 2007-09-18
How could that possibly help me?

---

### Post by eggdeng on 2007-09-19
> I'm going to assume that the drive is going to sleep at that specified time due to idling. If you think this is causing the problem, tell it not to go to sleep.

---

### Post by DizzyTech on 2007-09-19
It's not.  I've put my laptop into standby multiple times, and it is not the problem.

After some Googling, I found that my version of the HD (the FreeAgent Desktop) has an automatic sleep function due to its lack of a fan.

I think I found a solution:  A added a line to root's crontab letting the following command run every ten minutes (0,10,20,30,40,50) in every time period: ```

dir />/dev/null

```

I haven't been able to test it yet, but I'm sure that it will work.

---

### Post by strotti on 2007-10-01
If it doesn't work:
[http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)

---

