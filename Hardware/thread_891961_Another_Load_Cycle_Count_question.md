---
title: "Another Load_Cycle_Count question"
date: 2008-08-16
forum: Hardware
---

### Post by Redmumba on 2008-08-16
This is concerning the Load_Cycle_Count value itself; most places recommend that it be within a certain value (i.e., 600,000 being the typical "lifetime"), but mine is well over a million--and the laptop is only about a year old.  The exact, relevant output is:

> 
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4602
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1446637


That puts it at about 314 cycles per hour, which is way higher than the "bug" should be doing.

All other values are either "Pre-fail" or "Old_age".

Why are the values so far off?  I run both Linux and Windows on here, and I've seen similar values across various distributions besides Ubuntu, so its not an error with the current version of Smartctl in the repos, or anything like that.

Anybody have any ideas?

---

### Post by Redmumba on 2008-08-17
Anybody?

---

### Post by darco on 2008-08-17
dont know but I would follow this thread and see if they can help...they helped me on my Toshiba

[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

good luck 

darco

---

### Post by Redmumba on 2008-08-18
Right, this was really an extension of that problem;  I was curious about the extremely _high_ values that I was receiving.  Like I said, that's 314 cycles per hour, or about 5 per minute... that's well above the disasterous 1 cycle per minute that the above bug would provide.

So does anybody else know why my values are significantly higher?

---

### Post by sdennie on 2008-08-18
That's well within the range of what the problem could do if your disk is very aggressive and you are using the default settings.  The things that cause this problem (ext3 journal commit times and/or dirty_writeback_centisecs) are by default set to 5 seconds so, on a very aggressive disk, you could see 11-12 per minute.  

The "rated for 600,000" are just guidelines and it doesn't mean that your disk automatically fails on the 600,000th Load_Cycle_Count but, I personally would be cautious about storing data on that disk and, I would at the very least use the sticky thread above to prevent more from happening.

---

