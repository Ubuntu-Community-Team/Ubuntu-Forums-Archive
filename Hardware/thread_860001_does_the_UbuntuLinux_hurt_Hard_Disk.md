---
title: "does the Ubuntu/Linux hurt Hard Disk?"
date: 2008-07-15
forum: Hardware
---

### Post by harry.s.ko on 2008-07-15
Dear all Heros,
1st Iet me introduce myself to you ,I'm from CN--P.R.China,and I like the OS<Linux,Macintosh,windows,and the professional Unix>/IT/softwares etc..
but,now i have a important question needed an answer is wheather the UBUNTU 8.04 LTS nwill hurt the laptops' Hard Disk?just because in the forum china of ubuntu/BBS,there's someone said that the linux will hurt the Hard Disk of laptops,<because the HDD will be read all the time when in use or not,> and,the CPU always run in a high frequency,<added 2 pics of it > ,so , I really want to know the result of it ,because I will buy myself a Thinkpad T6x(P) in 1st Oct~7th,and I want to install a ubuntu 8.04 lts ,
so i want to get a correct answer to confirm my decision!
so,pls let me know it clearly ASAP

ps>,does the ubuntu support the thinkpad t6x very well?? like "Power Management"?
thanks
-- 
Smiles & Health
BestRegards&Thanks

Harry Ko
[email]Harry.S.Ko@gmail.com[/email]
Huntsman Advanced Materials(Guangdong) Co.,Ltd
Flying Geese Mountain Industrial Park
Shilou Town,Panyu,
+86 135 8043 3186
Guangzhou,511447,P.R.China


above is a letter what i want to send all the fans of ubuntu,so ,
 I really need help now ,
pls help me a little guy in linux:)
tks

---

### Post by kahlil88 on 2008-07-15
> **harry.s.ko said:**
> someone said that the linux will hurt the Hard Disk of laptops,<because the HDD will be read all the time when in use or not,> and,the CPU always run in a high frequency

Whoever said this probably just hates GNU/Linux and is spreading FUD to make you stay with Windoze. I don't think there is any operating system that is known to hurt hard drives and jack up the CPU (except maybe VISTA!). I can't guarantee that Ubuntu will work on any specific computer, but it will probably run very nicely on your Thinkpad. Power management is excellent, and Ubuntu will even tell you if your battery is bad, and if it's a recalled battery that you can get a free replacement for! I haven't seen any other operating system do this. :)

---

### Post by blampars on 2008-07-15
> **kahlil88 said:**
> ...Ubuntu will even tell you if your battery is bad, and if it's a recalled battery that you can get a free replacement for! I haven't seen any other operating system do this. :)

really? the battery in my Dell Inspiron 9100 has been bad, and there was a recall for it, but ubuntu hasnt told me anything except that its "charging" hehe

---

### Post by kahlil88 on 2008-07-15
> **blampars said:**
> the battery in my Dell Inspiron 9100 has been bad, and there was a recall for it, but ubuntu hasnt told me anything except that its "charging" hehe

Weird...maybe it's not in their battery database or something? My friend installed Gutsy on his laptop and this notification popped up informing him that his battery was bad and gave him a link to the recall site.

---

### Post by Odrodzona-Sarmacja on 2008-07-15
There is always Gaim program constantly looking for changes on hard drives for file browsers and other programs. It is run as service, but it is not in the list of services in Ubuntu. One can easily rename gaim binary, as uninstalling the gaim totally is not allowed on Ubuntu. Then you just use F5 if you need to refresh your file browser.

Also something with powering down hard drives lately doesn't work on Ubuntu 8.04, as some strange noises come from hard drives (yea strange I know and it wasn't in earlier versions) and there is no option for power management to disable power saving on hard drives or something alike.

However I don't believe hard drives will be destroyed just by Ubuntu directly.

---

### Post by Wulfrunner on 2008-07-15
I have been running Ubuntu on a T60p for 18 months and yes, it has damaged the hard drive. I do not know if Hardy Heron still has this problem, but Fiesty and Gutsy caused an abnormal number of spin up/spin down cycles while trying to save power. The drive has a lifespan of about 600000 cycles, and since I have had it, well over 300000 cycles have been recorded. This can be prevented if you play with your configuration files, but you will not benefit from hard drive power saving.

Power Usage: I have also gone through one 9 cell battery in 18 months (i.e. it got down to 60% of design capacity). You will never get the power usage below 20W and still be able to access the full functionality of your machine under Ubuntu. Expect to run your CPU and GPU 5-10 degrees C hotter using Linux. Your fan will run nearly constantly and you will get, realistically, 50% of the battery life under Ubuntu compared to Vista.

With that said, Ubuntu works out of the box and supports all hardware (with tweaking for things like fingerprint reader). You can spend days configuring and tweaking and playing around and you can marginally improve the mobility (i.e. power saving, noise, performance), but these machines are designed to function under Vista and do not take well to Linux (I have tried Gentoo, Debian, and BSD). If you want a laptop, you want mobility and Ubuntu does not support that adequately on the T6x series simply because they're too powerful.

---

### Post by sdennie on 2008-07-15
> **Wulfrunner said:**
> I have been running Ubuntu on a T60p for 18 months and yes, it has damaged the hard drive. I do not know if Hardy Heron still has this problem, but Fiesty and Gutsy caused an abnormal number of spin up/spin down cycles while trying to save power. The drive has a lifespan of about 600000 cycles, and since I have had it, well over 300000 cycles have been recorded. This can be prevented if you play with your configuration files, but you will not benefit from hard drive power saving.


I'm not sure how you consider this to be "damage".  That's 3 years of disk life before Load_Cycle_Count *might* become a point of failure for the disk.  This number is also highly dependent on the number of hours the machine has been up (also can be found with smartctl) so some people might find this number to be much lower after 18 months.

> 
You will never get the power usage below 20W and still be able to access the full functionality of your machine under Ubuntu. Expect to run your CPU and GPU 5-10 degrees C hotter using Linux. Your fan will run nearly constantly and you will get, realistically, 50% of the battery life under Ubuntu compared to Vista.


I agree that by default, the Ubuntu power savings is likely to be like this however, it's not extremely difficult to drastically increase battery life to be the same or better than Vista.  I don't have a T60 laptop but, the XPS m1330 information in my signature should be applicable to a wide range of machines (and also automatically reduces Load_Cycle_Count problems by only enabling it on battery power).

> 
If you want a laptop, you want mobility and Ubuntu does not support that adequately on the T6x series simply because they're too powerful.

My current laptop, while not a T60 and only 13.3", is about as powerful as laptops come (2.5Ghz, 7200rpm disks, nvidia graphics, etc).  It's simply a matter of taking the time to configure the machine to be on par with the way a Vista machine configured directly from the vendor would be.

I don't mean to sound mean but, your post makes it sound like Ubuntu is all gloom and doom on a laptop and I don't think that's the case.  Yes, it's harder to get it configured right but, it's well worth it.

---

### Post by harry.s.ko on 2008-07-17
before ,I just doubt that whether the ubuntu will destroy/hurt/damage the harddrives , because I used the ubuntu in a computer but not a laptop,and I will  try to use a T6x series,it seems that the laptop is not suit for the laptop now?
just need some update later ,we will see a really version like windows suit both computer and laptop ,
so ,who can help me now?? 

thanks all the one who give me helps..

---

### Post by lisati on 2008-07-17
> **kahlil88 said:**
> Weird...maybe it's not in their battery database or something? My friend installed Gutsy on his laptop and this notification popped up informing him that his battery was bad and gave him a link to the recall site.
There was a recall for Toshiba batteries too. I found a Windoze program at the Toshiba website to check if mine was "bad" but couldn't be bothered running it in Wine. Severe squinting at the serial number on the battery & comparison with info at the website suggested I didn't qualify for a replacement: it would've been nice since it's "gone south" and only lasts a few minutes when fully charged......

---

