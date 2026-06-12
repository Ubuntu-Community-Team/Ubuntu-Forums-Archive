---
title: "Suggest a 1 TB Hard disk"
date: 2010-05-07
forum: Hardware
---

### Post by sarin_cv on 2010-05-07
I am planning to buy a 1 TB hard disk which requires no external power  supply...please suggest one....

---

### Post by Rasa1111 on 2010-05-07
damn, all the ones Ive seen personally , require external power. 
the 1TB and higher drives anyway. 

good luck

---

### Post by sarin_cv on 2010-05-07
I've heard that the new seagate free agent requires no pwer supply.... but don't know the model name.. :(

---

### Post by Rasa1111 on 2010-05-07
> **sarin_cv said:**
> I've heard that the new seagate free agent requires no pwer supply.... but don't know the model name.. :(

 Seagate is what I use also. 
My 1TB does need external power though. 

Ill see if I can help you find it the one you mention...

---

### Post by Rasa1111 on 2010-05-07
well,,..

here is this one that runs on 'firewire'.. or "BUS powered"
[http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_xtreme/#tTabContentOverview](http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_xtreme/#tTabContentOverview)

which, [I may be wrong], but I believe that means it doesn't need external power?

---

### Post by cascade9 on 2010-05-07
> **sarin_cv said:**
> I am planning to buy a 1 TB hard disk which requires no external power  supply...please suggest one....

1st off, all external hard drives are just 'normal' internal hard drives in a case with a firewire/USB/eSATA interface. 

3.5'' Hard drives need external power. 2.5'' hdds dont. 

So your looking for a external that has a 2.5'' drive inside. 

I'm pretty sure that these drives do what ou want- 

Western Digital- My Passport Essential SE
Western Digital- Elements SE
Toshiba- Canvio Plus

---

### Post by sarin_cv on 2010-05-07
okay... there is Seagate freeagent Go also in the list I think... i'll go with any one of these... which do u think is better among seagate, WD and Toshiba?

---

### Post by srs5694 on 2010-05-07
One issue, which is not really something to decide which to buy, but which you should keep in mind when you get the drive: Some recent Western Digital drives use so-called "Advanced Format" technology, which means that they use 4096-byte sectors on the disk itself, but present the illusion of 512-byte sectors to the computer. This creates a need to create partitions on 4096-byte (8-sector) boundaries or risk severe performance degradation, as detailed [here.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) Every time I turn around it seems like WD has introduced another couple of drives using this technology, so you should research the matter for any WD drive you buy. Other manufacturers are reportedly preparing drives that use the same technology, but to date I don't know of any that are actually on the market.

Also, I've heard of some external drives that present 1024-byte or larger sectors to the OS. For the most part this is fine, but some versions of GParted flake out with such disks. Unfortunately, I don't know of specific models. If you wind up with one, you can still use fdisk or gdisk to do your disk partitioning, then use mkfs to create filesystems on the partitions. (Or you can use whatever partitions and filesystems the disk comes with, especially if you want to use it in both Linux and Windows.)

---

### Post by Rasa1111 on 2010-05-30
sarin cv~

did you get a drive yet?
If not, and are still looking, 

I just picked up a new 1TB external last night~
This is the one~ [http://www.nextag.com/Western-Digital-WDBABM0010-1TB-680347237/prices-html?nxtg=3b040a240519-A58E975AAD5117D1](http://www.nextag.com/Western-Digital-WDBABM0010-1TB-680347237/prices-html?nxtg=3b040a240519-A58E975AAD5117D1)

 It is very compact and sturdy, and there is no power supply.
Straight USB. It is quite niice. :)

---

### Post by Patsoe on 2010-05-30
> **Rasa1111 said:**
> 
I just picked up a new 1TB external last night~
This is the one~ [http://www.nextag.com/Western-Digital-WDBABM0010-1TB-680347237/prices-html?nxtg=3b040a240519-A58E975AAD5117D1](http://www.nextag.com/Western-Digital-WDBABM0010-1TB-680347237/prices-html?nxtg=3b040a240519-A58E975AAD5117D1)

 It is very compact and sturdy, and there is no power supply.
Straight USB. It is quite niice. :)

I read that a lot of Mac-users were annoyed with the "Smartware" software cd-image on this drive. Do you see any issues with this on Linux?

I'm a long-time WD fan, but I guess as a precaution I'd opt for the cheaper Elements series (also available with 1TB), which doesn't have the fancy software on-board. See [http://www.wdc.com/en/products/index.asp?cat=9](http://www.wdc.com/en/products/index.asp?cat=9)

---

### Post by Rasa1111 on 2010-05-30
> **Patsoe said:**
> I read that a lot of Mac-users were annoyed with the "Smartware" software cd-image on this drive. Do you see any issues with this on Linux?

I'm a long-time WD fan, but I guess as a precaution I'd opt for the cheaper Elements series (also available with 1TB), which doesn't have the fancy software on-board. See [http://www.wdc.com/en/products/index.asp?cat=9](http://www.wdc.com/en/products/index.asp?cat=9)

Hey, 

 Yeah, it does have the "smartware" stuff on it, 

 I was also pretty annoyed with it, for about 20 minutes until i figured out how to stop it from running every time i plugged the drive in. 

  I really didnt want to permanently delete it just yet,
but thought i might have to just to get it to stop running on every plug in. 

but.. (can't believe im saying this).. 
luckily i have an old IBM thinkpad 600e that sits in a drawer
with windows XP on it. lol

 and that allowed me to easily stop the WDsmartware from running. 

Now I plug into my computer and it just opens the drive itself, 
nothing extra pops up. 

in xp,  I just went to my computer, 
opened the "WDsmartware" to "explore the folder"..
and there was a smartware virtualCD 'setting'[i think'] icon, and i clicked it, followed a couple more clicks, and it was  "deactivated". 

Im sure I will completely remove it before too long, 
but i figured what's the rush, 
there is plenty of space to leave it where it is for now. 

and it doesnt get in the way at all now,
I dont even know [except in the back of my mind] that it's there on my Ubuntu box. lol

 I almost got the "elements" series, 
but it is allot bigger, and also needs external power...
(I really cannot spare much extra space on my desk, or in my power outlets) so it worked out. 

40 bucks poorer than I would have been, 
but it was 'free money'.. so what the heck.
normally I wouldnt have that to spare either. :lol:

 I also love the fact that I can easily carry 1TB of space on me in something that fits easily into any pocket.
 I got one of those little "case logic" "hardshell" cases that it fits perfectly in, just so i can take it places without much fear of bumps. lol

---

### Post by Patsoe on 2010-05-30
Hi, thanks for elaborating on that!

> **Rasa1111 said:**
> 
but.. (can't believe im saying this).. 
luckily i have an old IBM thinkpad 600e that sits in a drawer
with windows XP on it. lol


Hehe, well I'd say you shouldn't be ashamed of a healthy dose of pragmatism. Luckily, there's usually also a >90% chance that one of your neighbours has a Windows box, for cases such as this one :)

> I almost got the "elements" series, 
but it is allot bigger, and also needs external power...


There's the Elements Portable series now, that doesn't need external power. I think the 1TB version was a very recent addition.

---

