---
title: "rdiff and High Temp"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2007-02-24
Ok, I have a Satellite Toshiba laptop.  I have been learning to use rdiff-backup instead of the rsync.  I have the little icon on my panel that tells me what the temp of the internal hdd.  I have not been able to get any other controls like that working, just the hdd.  Anyway I have noticed that the temp always hangs around about 100F or so, usually not higher than 104F.  I have a Celeron M processor.  Every time I run rdiff-backup command the temperature soars up to around 111F or 113F.  The little thermometer turns red instead of the nice yellow it usually is.  Also the fan doesn't kick on like it should.  Usually the fan kicks on around 108F or so.  However when rdiff-backup is running it doesn't seem like it cares about the temp.  I have two theories.

1.  rdiff-backup somehow messes up the temperature reading, to make it not read correctly, or rdiff-backup somehow messes with the fan control

2.  The temperature is not really the hdd temp, but rather the processor temp, even though it claims to be the hdd temp.

Should I be concerned about this? 

Is the temp too high?

Thank you for the help.

Shane

---

### Post by Richard Kut on 2007-02-27
Hello shane2peru! I don't think that theory one would apply,

> 
1. rdiff-backup somehow messes up the temperature reading, to make it not read correctly, or rdiff-backup somehow messes with the fan control

simply because that is not one of the goals of the project - see here for more info:

[http://www.nongnu.org/rdiff-backup/features.html]("http://www.nongnu.org/rdiff-backup/features.html")

I believe that theory two is much more likely:

> 
2. The temperature is not really the hdd temp, but rather the processor temp, even though it claims to be the hdd temp.

I would only be concerned if the temperature exceeds 70 degrees Celsius for more than a few minutes.

I coincidentally addressed a similar issue earlier today, so maybe this thread will be useful to you too:

[http://ubuntuforums.org/showthread.php?t=369579](http://ubuntuforums.org/showthread.php?t=369579)

I hope that this helps.

---

### Post by shane2peru on 2007-02-28
Hey, thanks for the info.  I will look into those additional links on the other thread a little later.  I noticed this last time I ran rdiff-backup, that it didn't seem to spike the temperature.  It may have just been a fluke.  I will keep an eye on it though.  Thanks again!

Shane

---

