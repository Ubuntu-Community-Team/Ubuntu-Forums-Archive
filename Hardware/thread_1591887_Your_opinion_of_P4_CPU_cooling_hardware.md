---
title: "Your opinion of P4 CPU cooling hardware?"
date: 2010-10-10
forum: Hardware
---

### Post by mfdc1969 on 2010-10-10
I'm trying to build a 'free' computer for a friends kids using bits n pieces from many other boxes to keep the costs down. This is the first time I have really got under the hood and started monkeying with hardware.

I pulled a Pentium 4 3.0GHz Prescott out of a Dell box and added it to an ASUS LGA775 socket mother board which was previously holding down a Celeron 1.6GHz CPU. The board's manual confirms the CPU is compatible but now I am faced with trying to cool a much hotter running CPU!

I have added fans to front and back of chassis to move the air out but the original heat-sink (see attached photo) and fan from the Dell box which were attached to the P4 are not at all compatible with the ASUS motherboard so I can not use them.

So, my questions are:

1. How much hotter can one expect this P4 run under Ubuntu 10.04 in comparison to a Celeron 1.6GHz? I'm not looking for exact temperatures here but perhaps your opinions might indicate greater or lesser teps without getting into the numbers?

2. Can I expect the original, much smaller, heat-sink and fan to cool this P4 or should I just give my head a shake and go buy a serious cooler/heat-sink to properly fit the ASUS motherboard?

---

### Post by mastablasta on 2010-10-10
would it be better to just buy one of the new cheaper Intel processors? they come with the heat sink and will perform better than P4 i guess. i went with Celeron E3300 (2,5Ghz, dual core i believe) for 52 EUR.

---

### Post by mfdc1969 on 2010-10-10
That's a good point - I have not considered that. Are processors still compatible with LGA775? I guess  I have some homework to do!

Thanks!

---

### Post by Dark_Stang on 2010-10-10
I've used these style heatsinks on a lot of Core2Quad processors. Their factory heatsinks (those stupid plastic push pins) suck and just putting on a heatsink like this (spring loaded) dropped temperatures significantly.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16835150088](http://www.newegg.com/Product/Product.aspx?Item=N82E16835150088)

Just make sure it's the same power connection that your motherboard has.

---

### Post by cascade9 on 2010-10-10
> **mfdc1969 said:**
> 1. How much hotter can one expect this P4 run under Ubuntu 10.04 in comparison to a Celeron 1.6GHz? I'm not looking for exact temperatures here but perhaps your opinions might indicate greater or lesser teps without getting into the numbers?

2. Can I expect the original, much smaller, heat-sink and fan to cool this P4 or should I just give my head a shake and go buy a serious cooler/heat-sink to properly fit the ASUS motherboard?

1- depeding on exactly which P4 3.0GHz 'prescott' (theres several versions, thanks intel) celeron 1.6GHz, it could be over twice as much heat, even close to three times. Its probably a 'conroe -l celeron 430 (35watts TDP) and the P4 is probably a 3.0E (Hyperthreading, 800MHz FSB, 1024kb cache, 89watts TDP)

2- dont even try it. Thanks to thearmal throttling the CPU should survive, but you could very well kill something else in the process. You will probably need to upgrade your case airflow as well, those P4s really heat up insade a case if there isnt enough airflow through it.

> **mastablasta said:**
> would it be better to just buy one of the new cheaper Intel processors? they come with the heat sink and will perform better than P4 i guess. i went with Celeron E3300 (2,5Ghz, dual core i believe) for 52 EUR.

P4s, older ones in particular, are more likely to be limited by the chipset rather than the socket. Lots of LGA775 chipsets only went as far as P4Ds, etc. 

If your thinking about getting a  new CPU, its best to check exactly what CPU series are supported by that board/chipset...then go curse intels naming scheme. :lolflag:

---

### Post by mfdc1969 on 2010-10-11
I checked the [board's approved CPUs]("http://support.asus.com/cpusupport/cpusupport.aspx?SLanguage=en-us&model=P5GC-MX/1333&product=1") and over 15 P4s are listed. I'm not sure which one I have though.

About the heat ... I have added a fan at the front of the case and will add one at the back to push/pull air inside quickly. I was thinking of trying to get a big Zalman-ish heatsink (big chunk of Copper).

I was thinking of installing lm-sensors/applet to have an alarm watching the CPU temperature - is there a value at which I have crossed the "point of no return?" 80, 90 degrees C??

---

### Post by cascade9 on 2010-10-11
> **mfdc1969 said:**
> I checked the [board's approved CPUs]("http://support.asus.com/cpusupport/cpusupport.aspx?SLanguage=en-us&model=P5GC-MX/1333&product=1") and over 15 P4s are listed. I'm not sure which one I have though.

About the heat ... I have added a fan at the front of the case and will add one at the back to push/pull air inside quickly. I was thinking of trying to get a big Zalman-ish heatsink (big chunk of Copper).

I was thinking of installing lm-sensors/applet to have an alarm watching the CPU temperature - is there a value at which I have crossed the "point of no return?" 80, 90 degrees C??

With P4s, they should thermal throttle, not burn out the CPU. There has been cases where thermal throttling has failed, but they are very rare. 

If you case will take them, get 120mm fans. They move air more quietly than 92mm fans or 80mm fans, and move more of it as well. 

Thinking about getting a zalman CNPS9500? Really, dont bother. They are in the order of $50, you could get a newer, cooler, faster CPU for not much more. An E5400 is about $70 at newegg, will run fine with the stock intel cooler (inculded in the price), and there are better CPUs you can get running in your motherboard if you want to spend more money. 

As for the maximum temp of the P4- hard to know really. Aside from the throttling, intel decided that they wouldnt publish the 'core' max temp but instead 'Tcase' max temps, and converting between one and the other is......well.....PITA.

---

