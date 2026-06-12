---
title: "Stuck to Feisty with Mobility Radeon 9600"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by lviggiani on 2009-02-06
Hi guys,
I have an old laptop PackardBell EasyNote R7720 ([http://support.packardbell.com/it/item/index.php?pn=PB05500706&g=1400](http://support.packardbell.com/it/item/index.php?pn=PB05500706&g=1400)) equipped with an ATI mobility Radeon 9600.
I run Festy without any problem but I'm stuck there...
If I dist upgrade to 7.10, after reboot, even using the open driver "radeon", "ati" or "vesa" the system suddenly freezes and the mouse stop moving. I think this is a bug with Xorg... however, I cannot do the next dist upgrade to 8.04 as it freezes while downloading the updates...
On the other hand, my dvd drive is gone and it reads nothing other than Feisty live CD (isn't it funny!?) so I cannot install directly Intrepid.
I cannot boot from USB flash too... :(
BTW, I friend of mine, in Nov '08 had installed Intrepid on a Thinkpad equipped with the same video card, and the bug was still there.
It seems that with latest updates of Intrepid, the bug is fixed.
So I would like to ask:
1) Can someone confirm that Radeon 9600 works fine in Intrepid with lates updates and open "radeon" driver?
2) Is there a way to update to 8.10 via net (Internet?) without passing through 7.10, 8.04?
Many thanks in advance.

---

### Post by zvacet on 2009-02-07
I can not answer your first question but for second is** NO**.You can not skip versions to upgrade your system.I used vesa driver in Gutsy with no problem,so I don´think it is bug.Maybe somebody more expirienced then I´m will give you better guide to this.

---

### Post by Kevbert on 2009-02-07
Regarding your first question. I'm surprised that you're having problems with the ATI Mobility Radeon 9600 as I'm using a ATI Mobility Radeon 9000 which works fine with both Gutsy and Hardy using the built in ATI drivers.
No to the second question. If you want to upgrade, the best way would be to either a complete clean install of Intrepid, or even better, why not dual boot Intrepid with Feisty ?

---

### Post by abenusa on 2009-02-07
I have an IBM R50 laptop with the ATI Mobility Radeon 9000 graphics card with a 1400 X 1050 resolution display. The generic drivers installed with Ubuntu 8.10 work, however the generic driver is sluggish.

Tried the fglrx driver, and wound up with an unsupported graphics card running in low resolution mode. So uninstalled fglrx driver and am back to the sluggish generic driver.

It would really be nice to have an ATI driver that is responsive.

---

### Post by Kevbert on 2009-02-08
> **abenusa said:**
> I have an IBM R50 laptop with the ATI Mobility Radeon 9000 graphics card with a 1400 X 1050 resolution display. The generic drivers installed with Ubuntu 8.10 work, however the generic driver is sluggish.

Tried the fglrx driver, and wound up with an unsupported graphics card running in low resolution mode. So uninstalled fglrx driver and am back to the sluggish generic driver.

It would really be nice to have an ATI driver that is responsive.

Have you boosted the RAM as much as possible (or do you have the default 512Mb) ? You'll find that helps. The fglrx driver doesn't seem to like the 9000 IMHO.

---

### Post by ugm6hr on 2009-02-08
This sounds very odd.  CD drive will read a Feisty but not a newer CD, vesa driver won't work etc...

However, if you are certain you know what you are doing, you should be able to do this from Recovery Terminal (i.e not load X at all).

From Feisty - ensure you have correct old repos: [http://ubuntuforums.org/showpost.php?p=6319924&postcount=4](http://ubuntuforums.org/showpost.php?p=6319924&postcount=4)

Reboot into Recovery Terminal (from Grub).

```
apt-get update
apt-get install ubuntu-desktop
apt-get upgrade

```

Upgrade from Terminal:
[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended)](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended))

Repeat process as above for Gutsy (i.e. from Recovery Terminal) to Hardy etc.

---

### Post by lviggiani on 2009-03-03
Hi guys, thank you all!!
I'll try upgrading from terminal and see what happens... :)

---

### Post by lviggiani on 2009-05-06
Hi Guys,
In the end I could install Intrepid by means of a 1Gb thumb drive and then dist-upgrade to Jaunty.
Both Intepid and Jaunty run well using open driver "radeon" and I have my desktop effects running smoothly.
So for anyone having the same video card and any doubts to upgrade to latest ubuntu I would say that everything is working fine with the opensource driver and I would strongly recommend ***not to use*** the proprietary driver fglrx.

---

### Post by rannday on 2009-05-06
try Jaunty?

I, recently until Jaunty and the failure of my motherboard, have been unable to boot up 8.10 and below to what I believe to be a graphics card issue. Using an Nvidia 8600 GT on my box.

Once Jaunty came out, I immediately created a Live CD and was able to boot up on my pc under Jaunty, HURRAY!

---

