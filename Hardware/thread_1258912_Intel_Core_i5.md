---
title: "Intel Core i5?"
date: 2009-09-05
forum: Hardware
---

### Post by n0rth3rnlight on 2009-09-05
Is anybody having any luck running ubuntu on a stock i5? Is the P55 chipset working out OK?

---

### Post by mark_m on 2009-09-06
> **n0rth3rnlight said:**
> Is anybody having any luck running ubuntu on a stock i5? Is the P55 chipset working out OK?

what is an i5? Are you having trouble with one?

---

### Post by calc on 2009-09-16
> **n0rth3rnlight said:**
> Is anybody having any luck running ubuntu on a stock i5? Is the P55 chipset working out OK?

I just bought one and will get it sometime next week so hopefully I can manage to make it work. I doubt it will work on anything other than karmic if it does work at all.

Here is an article I just found:

[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=1)

---

### Post by Geetar_Jake on 2009-09-28
I picked up the i5 750 over the weekend, with an EVGA p55 LE board. I'll be assembling it today, so once it's all up I'll post in here anything interesting...

I found this doing some searching also, which has some promising information! :guitar:

[http://www.phoronix.com/scan.php?page=article&item=intel_lynnfield_add&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_lynnfield_add&num=1)

---

### Post by Tulsapoke on 2009-10-07
I have been running an MSI P55 motherboard with an i5 for a couple of weeks now.  I am running it on Karmic and everything seems to work fine.  Suspend, Ethernet you name it.  I have enabled, Green Power, EIST, Turbo, and C-state without issue.  

The turbo boost does not seem to be working though.  The CPU frequency scaling monitor seems to show that all the cores idle at 1.2GHz and spool up to 2.67GHz under full load.  The turbo should push them up to 3.2GHz (if fully loaded by a single thread).  Hopefully this is enabled soon in a kernel update or someone posts some way to activate it.

This machine is still 7x the speed of my old box so I am not sweating this too much, however it will be cool to see the full capacity of the i5.

---

### Post by AppleBonker on 2009-10-07
I'm not running an i5, but I am running the i7 860 (which is a Lynnfield processor similar to the i5) without any issues (on Jaunty for a few weeks).  This is mated with an Asus P7P55D Deluxe mobo.  As far as I can tell, you shouldn't have any issues with a P55 motherboard.

---

### Post by n0rth3rnlight on 2009-10-08
Ok thx for the input. Will place an order then 8)

---

### Post by AppleBonker on 2009-10-08
I don't think you will be disappointed.  The only issue I had with mine was ram related and had nothing to do with Ubuntu (I've seen numerous reports of ram issues using multiple motherboard manufacturers, so research the ram/mobo combo before buying).  Once I got the ram figured out (as well as my softraid), my PC has been screaming fast.  Now I'm just prepping to wipe clean again and install Karmic once it is out of beta.

---

### Post by Vorsplummi on 2009-10-17
Anybody who owns one of those lynnfield, please give us some benchmark results.
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

It would nice to compare your results to phoronix's

---

### Post by ProNux on 2010-03-18
Anyone tested on this hardware?

Core i5 750
Gigabyte P55-UD3P
Radeon HD4850

---

### Post by calc on 2010-04-17
I have:

Core i7 860 @3.55GHz
Gigabyte P55-UD5
8GB DDR3 RAM
Radeon 4350

It's quite fast, I don't have time to run any tests on it, but it does compile openoffice.org in just under an hour, or ~ 30min with ccache and few other hacks.

---

### Post by ProNux on 2010-04-26
> **calc said:**
> I have:

Core i7 860 @3.55GHz
Gigabyte P55-UD5
8GB DDR3 RAM
Radeon 4350

It's quite fast, I don't have time to run any tests on it, but it does compile openoffice.org in just under an hour, or ~ 30min with ccache and few other hacks.
Thanks for the info.  I managed to get it running smooth, am using Karmic-64 bit.  Minor issue on flash plugin at Firefox, though.

---

### Post by calc on 2010-04-27
> **ProNux said:**
> Thanks for the info.  I managed to get it running smooth, am using Karmic-64 bit.  Minor issue on flash plugin at Firefox, though.

You can get the 64bit Flash plugin package at [https://launchpad.net/~kees/+archive/ppa](https://launchpad.net/~kees/+archive/ppa) which will probably help if you are still running the one in the archive which is 32bit.

---

### Post by EpiLePTiC FaiRY on 2011-02-26
I'm trying to run an i5 with the H67 express chipset and 10.04 Server installs but then does nothing after reboot. Also, memtest version supplied with the disk (2.11 I believe) won't run. Very confusing. I can only imagine it is the chipset or BIOS setting incompatibility because it would be a very odd hardware fault.

I'm going to try memtest 4 as they have added further chipset support but if anyone knows why Ubuntu 10.04 won't run then please give me a clue!

It's an Asus P8H67-M with 8GB Corsair XMS3 and an i5 2500.

---

### Post by EpiLePTiC FaiRY on 2011-03-02
Nope, I'm out of ideas. The latest memtest runs without issue. Did 2 full cycles and found no errors. Now the install disk is b0rking out sometimes. Think I'm going to try SME Server and see how that does. I can turn FakeRAID back on that way.

---

### Post by mlissner on 2011-03-25
One comment here is that I think you're using a different generation of the i5 processor. I think when this thread was started, it was the first generation, and since that time, Intel has rolled out a new generation of chips, and (uncreatively), didn't give it a new set of model names, and stuck with the old ones + higher model numbers. 

Not positive, but I wouldn't expect a lot of good info on this thread about your processor...

---

