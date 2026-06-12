---
title: "Does Hardinfo log non-partition boots?"
date: 2009-12-08
forum: Hardware
---

### Post by baisong on 2009-12-08
This should be easy to test, but my ubuntu laptop is in maintenance, I want to know if in the "Boots" section of hardinfo's system reporting, are there any boots that go unrecorded? For example, if it's a dual-boot system, does hardinfo only record the boots in the system it's installed on? More importantly, does it record boots from live CDs or live USBs?

<unecessary background story>
So I bought my Lenovo laptop in the USA but now live and work (web programming) in Beijing. My laptop's screen would randomly shutter and flash, so I brought it into the nearest Lenovo customer service center, puting my warranty to some nice, international use!

And wouldn't you know it, I bring it in and the problem seems to go away-- we booted several times, and flexed the laptop screen and there were no malfunctions. Howevr, since it happened randomly, I agreed to leave the computer there for a few days and they would try booting again several times each day until they could see (and I guess diagnose) the problem.

So, five days later, I come in to see what's been done and the story seems bleak: "(in Chinese) Well, sir, we took a look at it every day, three or four times each day and nothing ever happened. Seems like whatever was wrong fixed itself!" So I whipped out hardinfo to check how many times it had been booted, and it appeared to have logged two boots since I'd dropped off the computer the previous week.

I told the Lenovo guy that it only had logged two boots, and he quickly clarified that "we didn't log onto your hard disk, we used our own Live XP USB to test your computer's hardware. So your program wouldn't have logged it." My instinct told me that there must be some level of firmware that informs hardinfo of bootstrapping events, so I challenged the Lenovo dude to quickly boot from the live USB and verify that no new boot entry would appear in the hardinfo log. I think that was a very non-Eastern face-stealing move, because he quickly ran back into the office and deferred me to a supervisor, who assured me that they would check more frequently and get back to me in two days.

So, I want to know if I was right or wrong that the Master Boot Record knows about all boots-- If I was wrong then I wrongfully discraced one Mister Yu, and if I was right, then perhaps what Beijing Lenovo customer service reps claim should be taken with a grain of salt!
</unecessary background story>

Thanks in advance! I know this is a stupid question and a long story!

---

### Post by acidx on 2009-12-09
Unfortunately, HardInfo will only list boots from the currently-running system. There is no way to know if the computer booted from another drive/partition.

---

