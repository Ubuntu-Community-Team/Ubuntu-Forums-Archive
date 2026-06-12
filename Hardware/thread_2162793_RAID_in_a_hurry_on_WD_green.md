---
title: "RAID in a hurry on WD green?"
date: 2013-07-15
forum: Hardware
---

### Post by 1clue on 2013-07-15
Hi,

I'm in a bit of a hurry to get some RAID up.  My town is pretty small, so the best I could find is a couple external drives.  I peeked under the covers and there are WD green drives in there, 3TB.

So I'm wondering if using green drives is a mistake on RAID?  I'm after raid1, I'm familiar with making RAID but have heard that green drives cause problems because of their automatic sleep mode.

Anyone have real information on this?

---

### Post by steeldriver on 2013-07-15
It may depend exactly which greens - I have a RAID1 setup on a pair of 2TB EARX drives and smartctl initially showed the LOAD_CYCLE_COUNTs growing alarmingly - however I was able to disable the idle timers using idle3ctl - there is also a WDC provided utility called wdidle.exe but you need to be able to boot into Windows (or at least DOS) for that 

[http://ubuntuforums.org/showthread.php?t=1997358&p=12002141#post12002141](http://ubuntuforums.org/showthread.php?t=1997358&p=12002141#post12002141)

---

### Post by 1clue on 2013-07-16
Thanks.  Reading now.

---

### Post by 1clue on 2013-07-16
Extremely helpful.  My wife has a Windows 8 laptop, so I can run that utility if necessary.

I had some green drives before as raid and they all failed early, which is why I freaked about it.  I wonder if they had the problem.

Thanks again, you've been a great help.

---

