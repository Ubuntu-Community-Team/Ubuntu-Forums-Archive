---
title: "SMART disk parameter"
date: 2009-02-12
forum: Hardware
---

### Post by Xhip on 2009-02-12
Hello!

I'm running Xubuntu here on my laptop and I regularly have a check on the SMART attributes of my hard disk. I do this since my Windows times (:)), and I always noticed that the parameter 'Load_Cycle_Count' decreased by 1 in an average time of 3 or 4 weeks.

I have changed to Linux, but obviously I continued to check the parameters and their evolution, and I think that now the same parameter is decreasing more fast than before.

Is this good or bad? What can you say about this parameter, 'Load_Cycle_Count'? I had a check on the forum, and read about an known issue related with this parameter increasing in time, but mine is decreasing... Should I be worried? 

By the way, my SMART overall-health self-assessment test always passes ok. The above parameter stays at a value of 42, at the moment:

ID#: 193 
ATTRIBUTE_NAME: Load_Cycle_Count
FLAG: 0x0032
VALUE: 042 
WORST: 042
THRESH: 000
TYPE: Old_age 
UPDATED: Always
WHEN_FAILED: -
RAW_VALUE: 581792

Regards!

---

### Post by x33a on 2009-02-12
well its threshold says 000, so it should decrease over time i guess.

if you are using smartmontools, then run a short dst and long dst to see the drive health.

---

### Post by Xhip on 2009-02-12
Yes, I'm using 'smartmontools' package. I don't know what you mean by "short dst" and "long dst", how can I do that? And what do they mean?

Regards!

---

### Post by x33a on 2009-02-12
short dst, and long dst are drive tests, which thoroughly check the drive for any errors, without causing any damage to your data.

type man smartctl in a terminal to see about the various options.

---

### Post by Xhip on 2009-02-12
Thank you!

The reading of that man page clearly solved some of my doubts about SMART stuff, it was very useful. I've done some offline tests, together with the short and extended self tests, and all of them were completed without errors... 

But should I look to something else related with the parameter 'Load_Cycle_Count' that I mentioned? Anyone knows more about it?

---

### Post by x33a on 2009-02-12
i don't think you should go into such technical depth regarding SMART, because firstly if your hard drive is working well, you don't have to worry about anything at the present. and, secondly,  SMART is basically informational and can't really predict a hard drive failure in most of the cases.

read here for the various attributes:

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

and most importantly, take regular backups, and don't worry too much about the drive. Most drives have 3-5 yrs warranty, so nothing to worry.

---

### Post by Xhip on 2009-02-12
Well, my drive is already 4 and a half years old, that's why I'm still making these tests. I don't think you can ignore SMART in that way, if it exists and show some information, then I rather stick to that than doing nothing and be surprised with a disk failure from nowhere. If I have something that can monitor my disk, I will still use it...

---

### Post by Xhip on 2009-02-17
Is there anyone that has had a problem with 'Load_Cycle_Count' parameter or knows more about it?

---

### Post by Xhip on 2009-02-19
Can anyone help on this please? My 'Load_Cycle_Count' is decreasing fast, and is now at a value of 41, so in 1 week it decreasead 1 point, too fast, I'm getting scared about my hard drive, on Windows it needed 1 month or so to decrease 1 point... Please, anyone?

---

### Post by IcarusR on 2009-02-20
If you are that 'scared' buy a new drive & either load Ubuntu & restore your latest backup. You do have backups don't you ???!!! 
Or image the old drive on to the new one & chuck the old one away. Problem solved !!!

And keep doing regular backups. I can not stress this enough. 
I've seen grown, professional men cry cos their company laptop HDD went *&^£ up & they had no backup & lost years worth of financial records !!!
Being asked if there is 'some magic spell' to make a dead HDD work again is also not funny coming from a financial advisor.

---

### Post by kpatz on 2009-02-20
Load_Cycle_Count is a parameter that measures the number of times the heads are parked and/or unparked.  Laptop drives in particular will park their heads and spin down to save power.  Drives are rated for certain number of load cycles over the lifespan of the drive (usually 200,000-500,000).  If you see this value changing more rapidly it's because the drive is parking (due to inactivity) and then unparking (due to activity) fairly often.

There are parameters you can tweak with hdparm to minimize this.  Google on "linux load_cycle_count" and there are many posts about this.

Windows tends to access the drive more regularly, so the heads don't park as often as they do under Linux.

---

