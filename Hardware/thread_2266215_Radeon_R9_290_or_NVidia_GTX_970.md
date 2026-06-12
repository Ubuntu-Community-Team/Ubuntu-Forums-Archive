---
title: "Radeon R9 290 or NVidia GTX 970?"
date: 2015-02-20
forum: Hardware
---

### Post by garpt01 on 2015-02-20
Hi All,
  Question:  

Radeon R9 290 ? 

or

NVidia GTX 970 ?

  I was always an AMD/ Radeon fan starting around 10 years ago. I believed they had the edge in software/ driver support for Linux. I am reading that the tide is turning and NVidia may have the edge both in support and hardware, certainly raw numbers in most categories between these two GPU's. This is a new build based on Intel i7- 5820 with 16GB Vengeance ram and Asus X99-A motherboard.  I use Ubuntu 80%-20% over Windows; still need Windows unfortunately for some tasks. Want a good quality video editing/ rendering machine, not a big gamer. Suggestions?

Appreciate any input! 

Thanks! GT

---

### Post by mooreted on 2015-02-20
Nvidia has much better support for Linux than AMD. I would go for the Nvidia card.

As for video editing you might check out:

[http://www.lwks.com/](http://www.lwks.com/)
[http://fundraiser.pitivi.org/](http://fundraiser.pitivi.org/)
[http://openshot.org/](http://openshot.org/)
[http://www.thefoundry.co.uk/products/nuke/](http://www.thefoundry.co.uk/products/nuke/)
[http://www.ifxsoftware.com/products/piranha/](http://www.ifxsoftware.com/products/piranha/)
[http://www.autodesk.com/products/smoke/overview](http://www.autodesk.com/products/smoke/overview)

The last three are professional, commercial systems that run on Linux.

---

### Post by garpt01 on 2015-02-20
mooreted, 

 Thanks for the info! 
Actually, I ordered the R9 290 first and changed it to the NVidia, but one always likes confirmation of their choices you know....
 was confident of my decision until I started reading threads about issues with various GTX cards, but I guess that just reinforces the recent popularity of the newer NVidias.

And thanks for the links!

---

### Post by mooreted on 2015-02-21
I don't know why AMD makes good cards and bad drivers. 

Glad I could help.

---

### Post by tokyobadger on 2015-02-21
I think nvidia has had the edge over amd for at least the last 10 years as far as linux/*nix is concerned.

For a recent card such as the GTX970 I'd suggest adding the xorg-edgers ppa (there are others too) and installing the 346.35 nvidia-driver - I think "current" is either at 331 or 337

---

### Post by garpt01 on 2015-02-21
> **tokyobadger said:**
> I think nvidia has had the edge over amd for at least the last 10 years as far as linux/*nix is concerned.

For a recent card such as the GTX970 I'd suggest adding the xorg-edgers ppa (there are others too) and installing the 346.35 nvidia-driver - I think "current" is either at 331 or 337

 I was reading some threads re: different ppa's that are available. But to start will I function OK with just the driver package on Nvidia's site?

Thanks.

---

### Post by mooreted on 2015-02-21
The trouble with installing the driver from the Nvidia site is that you have to build modules into the kernel yourself. When you get a system update that also updates the kernel, you have to do it again. By using a PPA the repository will keep you updated automatically.

---

### Post by tokyobadger on 2015-02-21
to add to what mooreted said, try and work with the package-management system - everything you add outiside of that will ultimately make your life difficult

for install just go with the nouveau default (no choices really) and then on reboot add a ppa with the newer drivers, install

---

### Post by garpt01 on 2015-02-21
> **tokyobadger said:**
> to add to what mooreted said, try and work with the package-management system - everything you add outiside of that will ultimately make your life difficult

for install just go with the nouveau default (no choices really) and then on reboot add a ppa with the newer drivers, install

OK, just to recap (I want to get this right to avoid what I believe are user errors when improperly installing the Nvidia drivers mostly)

* Boot into Ubuntu first time with new card. 
* Download ppa (x-org-edgers ppa)
* install 346.35 driver (or latest)

  Don't download or install anything else (at least for now, I believe the tuning and OC apps are available as well?)

Thanks to both of you.

---

### Post by mooreted on 2015-02-21
It comes with "nvidia-settings" which gives you your basic settings. You can enable overclocking. I haven't done it for awhile so I would have to look it up.

In Linux you only ever download something from the Internet when you have no other choice. This improves security and allows you to keep up-to-date from known sources.

When you first install Ubuntu you can click on Additional Drivers and get the version 313 drivers right off the bat if you just want to get going.

---

### Post by garpt01 on 2015-02-21
Thanks mooreted. 
So I will get full functionality without having to build any packages/ modules. That's quite an improvement from my old AMD card, I never did get anything but basic video. 
Good news.

---

### Post by mooreted on 2015-02-21
Things have really improved since my Red Hat 6.0 days for sure. :)

If you run into any issues please let us know.

---

### Post by garpt01 on 2015-02-21
Thanks for the offer of support, mooreted.
I should be ready to run in a week or so. Should go smoothly. My first "performance" rig in about 6 years.

---

