---
title: "hardware upgrade worth it?"
date: 2009-09-30
forum: Hardware
---

### Post by clutch| on 2009-09-30
So I have this Gateway M305CRV Rev 1 dual-booting Jaunty and Backtrack 4, and I'm wondering if it's worth upgrading.  Its not my only computer (I also have an 07-ish mbp that is at least 9000 times faster), but its the only one that runs linux full-time due to a lack of HDD space on my other laptop.  

Anyway, this thing is old.  Pentium 4 @ 2.20Ghz, which isn't too bad actually, but it has 216mb RAM, which is horrible.  Did some poking around and found that I can upgrade it to 1gig for around $40.  Would it be a major performance increase?  I would just clear off some space on my good notebook and dual boot it but I don't think the wireless card is any good with Backtrack 4, so I would just end up spending money on a USB wifi card anyway I guess.  So,

Would a RAM upgrade from 216 to 1gig make a huge difference in a machine this old?

Also, thoughts on throwing a small-ish SSD in here in place of the dying 40gig that's installed right now?  I mainly use this system for playing around with pentesting, so tons of storage space isn't necessary.  Wondering if the performance increase would be worth the $$$

/edit [http://support.gateway.com/s/Mobile/Gateway/M305CRV/3501715sp58.shtml](http://support.gateway.com/s/Mobile/Gateway/M305CRV/3501715sp58.shtml) <--here's all the technical specs

---

### Post by clutch| on 2009-09-30
I get what you're saying, but since the macbook pro's wireless card can't do injection, I would probably spend the same $40 on a separate USB wifi adapter anyway.  I'm just wondering if the RAM upgrade would noticeably improve performance.  I would assume that going from 216 megs to 1 gig would vastly improve things, but I'm not sure if there are any other bottlenecks in this particular system to worry about.

/edit dude deleted his post.  idk.  plz help.

---

### Post by clutch| on 2009-10-01
bump?

---

### Post by gordintoronto on 2009-10-01
Run system monitor, click "resources," and see how much swap you are using.  If it's significant (100 MB?), a RAM upgrade would make a difference.

I'm no fan of SSD drives.  If your hard drive is dying, pick up a cheap replacement, just make sure you're getting a 2.5 inch IDE drive, such as this one:
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16822148128](http://www.newegg.ca/Product/Product.aspx?Item=N82E16822148128)

---

### Post by clutch| on 2009-10-01
Yeah, its using roughly 100MiB for the swap space, give or take 5.  This thing almost crapped itself just trying to open the system monitor.  lol

---

### Post by markbuntu on 2009-10-01
A ram upgrade will make a big difference since you will no longer be using the very slow swap for system operations. 216mb ram is very marginal. It is a wonder it works at all.

SSD is slow expensive and has a limited life compared to a hdd. You would kill it fairly quickly if you are using it for swap. The only reason for SSD is survivability, Hdds are also very cheap these days.

So, ram for $40 a new hdd for another $40 -50. A used machine like that sells for about $100....

---

### Post by clutch| on 2009-10-02
Ok thanks for your help. Gonna throw the new RAM in there next week, not so worried about the HDD since it still seems to be working ok. I know it's probably stupid to dump 40$ into a machine that's only worth 100$, but I just need a second laptop until I build my new desktop later this winter. My fiancé uses my mbp a lot, and I hate not having a reliable spare to use while she's on it.

---

### Post by louieb on 2009-10-02
> **clutch| said:**
>   Pentium 4 @ 2.20Ghz, which isn't too bad actually, but it has 216mb RAM, which is horrible. ... can upgrade it to 1gig for around $40.  Would it be a major performance increase? 

Got the same processor in my T30 ThinkPad.  IMO best 40 bucks you'll spend.  Went from 512MB to 1.5GB in mine - now - I can even run XP inside VirtualBox without a noticeable slow down.  

My drive wasn't dieing but it was only 40GB. Got a 160GB Seagate for around 50 -60 bucks. Nice to have the extra space.

---

### Post by clutch| on 2009-10-02
Yeah, I figured that would be the case.  I don't know for a fact that the hard drive is dying, I'm just kind of assuming that its days are numbered considering its age.  Then again, I don't keep anything on it anyway because I am just learning and have a habit of screwing things up so badly that I just decide to wipe the drive and reinstall.

Is there a good tool in Linux to check on the health of a disk?  I remember reading about something like that for Mac a while back, but I never tried it.

---

