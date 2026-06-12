---
title: "My hard drive won't stay asleep"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by dameat on 2008-01-03
I just got a new SATA hard drive and moved all my stuff to it, but I'm keeping my old PATA around for backups, media, etc. However, compared to the new one, it is noisy! I'd like for it to stay asleep/spun down as much as possible, but I'm having problems making it do so. When I issue the command "hdparm -y /dev/sda" it spins down, but it inevitably spins back up again after anywhere from 5 to 60 seconds. Also, 'hdparm -S 1' seems to have no effect. 

I figured that there was some application polliing the data off the drive, so I tried unmounting its partitions, but even then, it still continues to spin up! What gives? I know i've done this in the past with older linux's. Maybe something to do with the new libata driver? Any suggestions?

Thanks!

--greg

---

### Post by vazzeroni on 2008-01-13
I'm having the same problem, except with my primary hard drive - I have a media-playing computer that has a loud hard drive and I'd like it to stay spun down, but it spins back up again almost immediately. Anybody have any suggestions for how to keep hard drives asleep? I thought, in the past, that it was FAM or something, but it doesn't seem to be running. Gutsy Gibbon on a Gateway E Series....

---

### Post by jpittack on 2008-01-18
I am interested in spinning down the hard drive for longer periods of time as well.  From what I have been reading on the web, the hard drive spins up when something is being written to it, which is set on a timer.  Such as, every 15 seconds, write a log to the hard drive.  The same page is making claims about the hard drive spun down for 10 minutes after applying their fixes.  If I can find the page again I will post a link.

If you unmount a drive and it spins back up, it has been remounted.  You need to stop it from being remounted.  Pure guess on this one.  Couldn't tell you how to do this either.

---

### Post by dameat on 2008-01-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I figured this out - it turns out it was hddtemp waking it up to check the temperature every minute or so. Here's a bug related to this issue: [https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621)

---

### Post by Daelyn on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=669607](http://ubuntuforums.org/showthread.php?t=669607)

---

