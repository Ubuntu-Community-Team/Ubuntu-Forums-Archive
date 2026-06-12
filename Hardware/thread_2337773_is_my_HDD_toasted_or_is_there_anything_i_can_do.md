---
title: "is my HDD toasted or is there anything i can do"
date: 2016-09-21
forum: Hardware
---

### Post by normalcrayon on 2016-09-21
Have been having lots of boot problems and i think i found the cause... is it over? Tons of bad sectors
[http://i.imgur.com/RJ39moZ.png](http://i.imgur.com/RJ39moZ.png)

---

### Post by DuckHook on 2016-09-21
Not good.

While true that new drives are so large that a few thousand bad sectors are not necessarily disqualifying, it's never a good thing to see so many because their presence implies an unreliable drive. Back in the day when HDDs were expensive&#8213;and far smaller&#8213;it was worthwhile and not too laborious to figure out where the bad sectors were. If they were confined to just one well defined area of the disk, then this could be put down to a bad patch on the substrate and one took a chance that the rest of the disk was okay. But these days, it doesn't make much sense to do such deals with the devil. 

My recommendation is to buy a new HDD.

BTW, SMART shows your drive to be OK. To do a deep analysis:

Testdisk Instructions:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mma8x on 2016-09-22
I went through [something similar]("https://ubuntuforums.org/showthread.php?t=2327361") recently. My SMART status also came back OK. Running badblocks just had read error after read error. I ended up getting the data off (but I forgot and left the power on on the drive for like a month). Now the drive isn't recognized at all. So, maybe keep it as a spare, but I wouldn't chance leaving anything valuable on there that I don't have a backup.

---

