---
title: "cpu running on max frequency"
date: 2011-04-04
forum: Hardware
---

### Post by buchta on 2011-04-04
hi,
I have asus 1215n with intel d525 processor, which is running on full 1800Mhz no matter the load. Having dual-boot, I checked it both in Win7 & Ubuntu 10.10
it seems like the scaling is locked cos when I tried CPU frequency monitor (for GNOME panel) I got the error in attachment.

could anyone please help?
I found some old threads like [http://ubuntuforums.org/showthread.php?t=394911](http://ubuntuforums.org/showthread.php?t=394911)
and [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
but they are not helping me much...
any ideas? any special tips on how to unlock the scaling so it will adjust?

thanks a lot

---

### Post by davidmohammed on 2011-04-04
I believe from what I've read that processor is fixed at that speed - you cant run any faster or slower.  Intel says it is 'optimized' for low power running at that speed

---

### Post by buchta on 2011-04-05
well the power consumption is not a problem yet -the machine's new and so is the battery, but I believe it would stretch the battery time. And mainly, the fan is driving me crazy when it's cooling intensively and there's just Opera and Pidgin running...
So it seems I will have to get used to it...

thank you, davidmohammed

---

### Post by diazamet on 2011-10-11
How does the machine behaviour when running Win7?  Does the fan run just as much?

---

### Post by diasf on 2011-10-11
According to the intel page:
[http://ark.intel.com/products/49490](http://ark.intel.com/products/49490)

Your processor does not have speedstep, so no change for you.
You might be able to control the fan tho, but from the page i got a doubt, what's the result of the "sensors" command? (to control the fan you need the processor's temperature and your might not have the sensor)

---

### Post by buchta on 2011-10-13
I have fresh install now, but had the sensors installed before, so I was able to check the temperature, but I don't want to mess with fan when the cpu's running on max, I don't want it to melt :)

thank you guys anyway :)

---

