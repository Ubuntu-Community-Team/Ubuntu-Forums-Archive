---
title: "Will a 10.000 RPM hardrive improve startup-time?"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by oldb0y on 2008-01-16
I was thinking of buying a 10.000 RPM harddrive (WD Raptor X). But will my startup-time improve any? If I install my Ubuntu-system on it.

---

### Post by jerrykenny on 2008-01-16
Surely you're just showing off now oldboy !   10,000 rpm indeed.

Harrumph, it'll be twin turbos next.

I reckon a hand compiled kernel is the biggest single improvement you can make to your bootup.

(assuming its compiled ok that is)

---

### Post by oldb0y on 2008-01-16
No showoff here[-X
I'm really not that skilled, so hand-compiled kernel sounds like rocket-science to me...

---

### Post by jerrykenny on 2008-01-16
Lol,  well it'd be interesting to see what difference it does make, aught to make a difference to the runnng of the thing anyhow.

More Ram might be a cheaper option, but i reckon thaat only improves bootup if yer presently short on ram and becoming the bottleneck 

     Good luck

---

### Post by Yellow Pasque on 2008-01-16
Of course it speeds startup, but there are better/cheaper things to try first
[http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)

---

### Post by OmegaBLK on 2008-01-16
> **oldb0y said:**
> No showoff here[-X
I'm really not that skilled, so hand-compiled kernel sounds like rocket-science to me...

I think the main problem with many people's boot times are most likely due to the amount of services that startup on their particular installation.  The less services you have running at bootup, the faster your boot time.  Also checkout [AutoFsck](https://wiki.ubuntu.com/AutoFsck?highlight=%28AutoFsck%29).  If you insist on purchasing the WD Raptor you probably would notice some boot up improvement, but I have no numbers/benchmarks to draw on nor personal experience as I have never owned a WD Raptor so I can only guess.  Unless your system is just dog slow, I would attempt to try out cheaper solutions first as the price premium on the Raptors (150GB versions) is not really worth the purchase IMHO anymore.  Especially right now since many of the new large +750GB drives with the 32MB cache are giving the Raptors a run for their money in some benchmarks.  Now if the 150GB Raptor was $70-50 cheaper, I would definitely recommend one.

---

### Post by Whiffle on 2008-01-16
> **OmegaBLK said:**
> I think the main problem with many people's boot times are most likely due to the amount of services that startup on their particular installation.  The less services you have running at bootup, the faster your boot time.  Also checkout [AutoFsck](https://wiki.ubuntu.com/AutoFsck?highlight=%28AutoFsck%29).  If you insist on purchasing the WD Raptor you probably would notice some boot up improvement, but I have no numbers/benchmarks to draw on nor personal experience as I have never owned a WD Raptor so I can only guess.

I wholly agree here... removing unused services would be a good place to start.  A 10k rpm hard drive might help, not sure though, I've never had one.  

Oh, and kernel compilation really isn't all that hard, you just have to pay attention to what you're doing.

---

### Post by tgalati4 on 2008-01-16
I'm thinking of getting a Raptor myself.  If you get one, please post some results so we know how much time you save on boot.

Regards

---

### Post by oldb0y on 2008-01-17
Well I'm not 100% sure about buying one. If I do so, I will come back in this thread with some comparison. Thanks for the replies!

---

### Post by Whiffle on 2008-01-17
If you have a dual core processor, you can also set it up so it uses both cores on boot to start services in parallel.

---

### Post by cubeist on 2008-01-17
Actually, from my experience, faster HDD's don't really make a noticeable difference on boot up speed.  I recently replaced my 4200 rpm to a 7200 rpm notebook drive with cache  and ncq and the main speed difference is in the overall system speed.  For example, opening my pictures folder with several thousand pics used to take about 15 seconds, now it takes about 3 seconds...

Using bootchart on the old drive took I think 34 or 35 seconds, the new drive is 31... with about the same services.

My advice, don't buy a super expensive drive to help bootup.  Buy it for overall system speed or space.  And remember, faster drives run much hotter!

---

