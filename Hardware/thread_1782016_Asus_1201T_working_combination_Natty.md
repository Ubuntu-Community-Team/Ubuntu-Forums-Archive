---
title: "Asus 1201T working combination Natty"
date: 2011-06-14
forum: Hardware
---

### Post by maestrobwh1 on 2011-06-14
Wifi is unstable from the latest standard kernel and drops out all the time with me being 10 ft (3 meters) from my router.  This particular chipset seems unstable in linux in general, and was only stable in Meerkat with the first few versions of its kernel.  Not exceptionally stable in puppy linux lucid either.  RTL8912se from Realtek.

I have an odd combo but for anyone who has the combination of this wifi with a Radeon card and wants to use fglrx, this is the only way (after trying fglrx builds for 4 hours) that I could get it installed and have stable wifi: 

Use the kernel 2.6.39-0-generic [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

Use fglrx from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Then I disabled the ppa's because within the latest releases, fglrx breaks easily during its won upgrades or during a kernel upgrade.  Not in the mood.  If I notice any funkyness, I will re-enable them but everything seems rock solid at this point.

The kernel upgrade also fixed the odd issue with the brightness OSD (running KUBUNTU) not showing when I used the Fn key, but did work when I used the slider from the power manager.

The only Fn Key that does not work is the Screen Blank key (Fn+f7)

My battery is lasting significantly longer in Natty compared to previous releases.  Nice.

---

