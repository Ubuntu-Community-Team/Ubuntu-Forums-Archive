---
title: "t400, momentus xt - sometimes hdd is slow?"
date: 2011-02-17
forum: Hardware
---

### Post by cahe on 2011-02-17
Hi,

I've had this problem with playing video on my laptop - HD video would stutter every few seconds. I've managed to deal with it by playing with various parameters in mplayer and one that helped was using large cache buffor size (64MB). It pointed me to disk related issues, i've run some test and this is what i got:

/dev/sda:
 Timing cached reads:     2 MB in  2.54 seconds = 805.89 kB/sec
 Timing buffered disk reads:  244 MB in  3.00 seconds =  81.28 MB/sec

Half the time cached reads are <1MB/s fast! That'd be the problem that caused choppy video playback, i presume. Please help me find the cause! :)

Thanks,
Maciek

---

### Post by winterstream on 2011-02-28
I have the same issue on a Lenovo N100 3000.

I would like to try the harddrive in another laptop to
see what happens. I upgraded the firmware to SD24 but it
didn't help.

---

### Post by cahe on 2011-03-02
Replaced the drive with WD Black Scorpio - much better. No jittering/stuttering at all.

---

