---
title: "RAID (will a software solution work)"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by seepage87 on 2007-11-14
My goal is to set up a RAID 5 of about 4 for 5 500GB HDs.  Here is a few requirements:

* I want to be able to boot ubuntu from the array (on its own partition)
* I need (maybe a year from now) to be able to add a 6th (then 7th, then 8th evenually) HD to the array without need to back up and rebuild (just resize, restructure)

I'm currently looking at this (fakeraid) card:
HighPoint ROCKETRAID2220
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115022](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115022)

because it supports online capacity expansion (my expansion need not be hot though) and 8 drives (needed) and I've read a couple places that people have gotten it to work in ubuntu (with some hassle).

I would prefer a software solution (mdadm) because it would save a good deal of money and preform as well, but I need to know:

* Does it fit my above requirements
* If so, what is the best solution to use.  Is mdadm the way to go?
* If not, why not and is there a better card to choose keeping in mind price and my requirements.

FYI, I'm going to put this in a brand new box (haven't bought any parts yet, probably going to by HDs on Black Friday if I can find good price).  Goal of the box is to serve files, web server, and eventually be a mythTV backend (hardware encoding capture cards to keep extra strain off CPU).  Any suggestions down this ally would be appreciated too.

Thanks so much.

---

### Post by seepage87 on 2007-11-14
I did some research and already figured out the answer to some of my questions.  For adding a drive check out this:

[http://scotgate.org/?p=107](http://scotgate.org/?p=107)

Someone said that, for just ubuntu,  "RAID5 array reshaping is disabled in the stock kernels, giving an 'invalid argument' error when trying to grow the array.  So they need to compile a custom kernel and enable the option CONFIG_MD_RAID5_RESHAPE=y in the .config file. Note that kernel 2.6.17 or above is required."

Is there any truth to that?  A few other commenters were using ubuntu and didn't seem to have problems.

Also, I've been thinking it might be better not have my root partition in the array to make expanding the array go smoother, but it would be nice to have the redundancy protecting it so I don't have to start from scratch if my out-of-array drive fails.  Any thoughts?

Thanks again

---

