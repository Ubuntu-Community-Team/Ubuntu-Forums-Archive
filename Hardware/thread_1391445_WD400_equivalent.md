---
title: "WD400 equivalent"
date: 2010-01-26
forum: Hardware
---

### Post by kmsalex on 2010-01-26
i resantly got a semi new custom built computer from my school,(they were going to trow it out) 2.4 ghz p4 512 mb pc 400 ram in one slot with 3 open, and a 40 gb WD400 drive. it seams the problem was the drive whent bad. so i tolk the hard drive out of my old desktop 
(thinking that all 3.5 ide drives were compatible) pluged it into the new computer and powered it up, it did't detect it, and when i put it back in the old computer it was't detected there either. so i awesomed its fried. now i know that not all 3.5 ide's are the same. so i was wondering wat would be a good replacemet for the WD400 for under $40? as the WD400 is't avaleble form western digital site and is $70 on amazon. an sugestions are apreshated.

EDIT: i did't mean to put the winky face in the title but can't remove it now.

---

### Post by louieb on 2010-01-26
AFAIK -  3.5 IDE drives made in the lat 10 -15 years pretty much should work in any computer with a IDE interface. Double check you connectors and jumper settings.

---

### Post by kmsalex on 2010-01-26
> **louieb said:**
> AFAIK -  3.5 IDE drives made in the lat 10 -15 years pretty much should work in any computer with a IDE interface. Double check you connectors and jumper settings.

they both used 4 pin power conectores, but what are jumpers? i've hered the term before but never bothered to learn what they are. its worth noting i'm relatively new to hard ware replace ment beside swaping out some ram.

---

### Post by t4thfavor on 2010-01-26
+1 to jumpers, make sure it's master or slave  or cable select. I would buy a much larger, much less expensive drive off newegg or something as the 40GB has to be pretty old.

---

### Post by t4thfavor on 2010-01-26
Most of the time Jumpers are in the center of the drive. you will see a bank of 2 rows of 4-5 pins, they make up the jumper setting.

you need a little plastic connector that shorts out certain pins to tell the drive what mode to act in.

---

### Post by louieb on 2010-01-27
Usually the jumpers are located between the flat ribbon connector and the power connector.  Believe your drive has a setting diagram on the top of the drive - if not just google **wd400 jumper settings. **

Also some flat ribbon connectors can be plugged in backwards. Make sure the colored wire is closest to the power connector. 

> I would buy a much larger, much less expensive drive 

+1 IDE drives are also called - PATA or ATA-6 or ATA-100 or ATA-133.

---

### Post by cascade9 on 2010-01-27
> **kmsalex said:**
> so i tolk the hard drive out of my old desktop 
(thinking that all 3.5 ide drives were compatible) pluged it into the new computer and powered it up, it did't detect it, and when i put it back in the old computer it was't detected there either. so i awesomed its fried. now i know that not all 3.5 ide's are the same. 

Umm.....I doubt that its because 'not all 3.5'' IDEs are the same'. Like louieb said, pretty much any PATA drive from the past 10-15 years should work. 

I think you've got a more serious problem than you think...either your molex (power) connector is miswired (5volt where 12 volt should be, and the this is the deadly bit, 12volt where 5volt should be) or some otehr hardware electronic problem. 

If you have a multitester, check your voltages. 

BTW, forget getting an exact replacement drive. Get a nice, cheap 80Gb or 160GB, they go for about $40 on newegg.

---

### Post by kmsalex on 2010-01-27
i tried using the hdd from my original computer and this time it tyred to boot into windows but failed. but when i started up the live cd ubuntu detected it, i don't  want to format it and use it becuse i might try to recover my old computer just for fun one day, pluse its from 2001 and acrocreding to ubuntu has been powered on for 2.1 years. so i was looking at this one on newegg
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136457&cm_re=80_gb_ide-_-22-136-457-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136457&cm_re=80_gb_ide-_-22-136-457-_-Product)

i think it should be good, also do you guys know on avarage how many power on years drives normaly last?

---

### Post by t4thfavor on 2010-01-27
Lots of decent drives have a million hour mean time before failure. Meaning on average the drives last 1 million hours before failing from wear.

2 years is only around 13k hours, though I wouldn't trust it on a critical server, it should last on a PC if you don't have the $80 for a new one.

---

### Post by louieb on 2010-01-28
> **kmsalex said:**
> ...on avarage how many power on years drives normaly last?

Got my 1st PC in 1985 - in that time have had 1 or 2 hard drives die. 90% of the time I replace a hard drive just because its just gotten to small for all the stuff I want to put on it. On a desktop a hard drive should easily work the useful life of the computer.

---

### Post by cascade9 on 2010-01-28
> **t4thfavor said:**
> Lots of decent drives have a million hour mean time before failure. Meaning on average the drives last 1 million hours before failing from wear.

2 years is only around 13k hours, though I wouldn't trust it on a critical server, it should last on a PC if you don't have the $80 for a new one.

Actually, MTBDF isnt the rated life. Common misconception though. 

[http://en.wikipedia.org/wiki/Mean_time_between_failures](http://en.wikipedia.org/wiki/Mean_time_between_failures)

> What does MTBF have to do with lifetime?  Nothing at all!  It is not at all unusual for things to have MTBF's which significantly exceedtheir lifetime as defined by wearout -- in fact, you know many such things.  A "thirty-something" American (well within his constant failure rate phase) has a failure (death) rate of about 1.1 deaths per1000 person-years and, therefore, has an MTBF of 900 years (of course its really 900 person-years per death).  Even the best ones, however,wear out long before that.

[http://www.faqs.org/faqs/arch-storage/part2/section-151.html](http://www.faqs.org/faqs/arch-storage/part2/section-151.html)

---

### Post by kmsalex on 2010-01-30
ok i got the hdd in the mail and pluged it in and powered up the mashine, nothing. i tryed again but this time i held it in my hand to fele if it would even start to spin up, nothing. so i think i might have goten a doa. so i'm going to try to extyange it on newegg. but also i found out the exact mother board its a asus p4p800-vm. i wondering if it doesn't support a drive of 80 gb but i couldn't find that on the Internet. 

any advice on what to do from here would be greatly appreciated.

---

### Post by cascade9 on 2010-02-05
Let me get this straight....

You got a computer, with a dead hdd. You swapped out the HDD in the new computer, and put in a HDD from your older computer. The old HDD/new computer combo didnt work, so you put it back into the old computer, and it didnt work there. 

You've now ordered a new HDD, put it into the computer, and its not working either. 

I wouldnt be at all suprised if your are having a power issue (like there is no power getting to the drive, or the power that is getting there is too much and its blowing the drive) or you have a controller issue. 

You could try hooking the HDD up to the connectors that the CD/DVD drive is using. 

> **kmsalex said:**
> but also i found out the exact mother board its a asus p4p800-vm. i wondering if it doesn't support a drive of 80 gb but i couldn't find that on the Internet. 

Yep, that supports 80GB drives fine.

---

### Post by kmsalex on 2010-02-06
no now i have managed to get the computer to recognise the hdd from the old computer, it even tries to boot into windows but fails. in ubuntu its recognised and i even maged to save some of my pis/and videos i never backed up. to my flash drive. but now it woun't work when i put it back in the old computer. now when i got the new drive and pluged it in i got nothing. i'm hoping it was just a dud and have sent for a replacemet. i'm hoping that it wil work this time cuse i realy don't want to have to use the old hdd.

---

