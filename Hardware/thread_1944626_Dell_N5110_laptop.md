---
title: "Dell N5110 laptop"
date: 2012-03-21
forum: Hardware
---

### Post by tedr108 on 2012-03-21
Ubuntu noob here (for the most part)...

Got a Dell N5110 laptop a while back and dual booted 32-bit Ubuntu 11.10 with the 64-bit Windows on the other partition.  Everything is running well.  Been writing Android apps with the Android SDK/Eclipse without issue.  (Absolutely love working in Ubuntu and would dump Windows altogether, if I did not have some old VC++ apps to maintain.)  OK, enough background...

I want to get into Android ROM development and 64-bit is recommended for that.  The Ubuntu sites seem to recommend 32-bit 11.10 for my laptop.  I just plugged in a 64-bit Ubuntu 11.10 CD as a test, and my laptop seems to be running just fine (though slow as can be) ... played around with some things, the display is fine.  Is there anything I really need to test?  Or, do you think it is worth a shot to go forward with installing 64-bit over the 32-bit Ununtu 11.10?  Thanks for any advice you can give.

---

### Post by tedr108 on 2012-03-22
Well, I just decided to go for it.  64-bit Ubuntu 11.10 appears to be running just as well, if not better than 32-bit, on my Dell N5110.  Haven't tested HDMI (and probably never will), but USB peripherals (mouse, external hard drive) have all functioned fine.

For my first attempt at installing 64-bit, I tried to simply overlay 32-bit with the 64-bit ... did not work well (ended up with a mixture of both systems!).  So, ended up going back in and installing with "Something Else" ... deleted all Ubuntu partitions (/boot, swap, /, and /home) ... and recreated them.  It was quite easy, actually.

Think I've got myself a good Android development laptop.

---

