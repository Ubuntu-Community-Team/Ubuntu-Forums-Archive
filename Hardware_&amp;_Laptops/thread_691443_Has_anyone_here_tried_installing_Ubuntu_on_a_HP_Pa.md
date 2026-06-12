---
title: "Has anyone here tried installing Ubuntu on a HP Pavillion DV6707US?"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by tomsa on 2008-02-08
I am considering buying a HP DV6707US laptop at a major retailer.  My plan is to shrink the existing Vista Partition, and install Gutsy as the OS of choice.  I have googled my brains out, scoured the laptop testing team wiki, and searched these forums pretty extensively over the past few days, and I haven't found a whole lot of info.  I like that it has a Turion 64 processor, for when 64 bit is more readily available, that it has 2 GB of RAM installed, and I also like that it has an Nvidia graphics card.  Have any of you tried installing Gutsy on the laptop?  Is the fact that I'm not finding a lot about it a good sign because no one has any complaints?  Should I just save my money?  Please let me know what you might know about this computer!

[Link to the major retailer  ]("http://www.circuitcity.com/ccd/productDetail.do?oid=199872&WT.mc_n=4&WT.mc_t=U&cm_ven=COMPARISON%20SHOPPING&cm_cat=GOOGLE&cm_pla=DATAFEED-%3EPRODUCTS&cm_ite=1%20PRODUCT&cm_keycode=4#prodspecs")

---

### Post by A. J. Rimmer on 2008-02-08
Hi -- I just stopped by the forums for a quick look and saw your post.

Can't put my finger on it at the moment, but seems there was a long thread regarding problems that people were having with 7.10 on the HP dv6000 and dv9000 series laptops.  I'm sure it still on the forums somewhere, just don't know where at the moment.  You will want to find that and read through it.

I have an HP dv5000 series that doesn't seem (based on what I have read) to have a problem with 7.10, but I'm sticking with 7.04 for now, just to be safe.  Feisty works great on the HP, and I have Gutsy running on an older Ultra-brand laptop with no problems at all.

If I stumble across the thread I will post again.

Update: tomsa -- search the forums for "dv6000" and you will find a lot of info that should be of use to you.

---

### Post by tomsa on 2008-02-09
I've seen that thread, and I haven't seen anything about the dv6707 on them.  It's been mainly the dv6704 or lower model numbers.  I'm going to take a live CD to the aforementioned retailer to see if 7.10 plays nice with the hardware.  I'll post the results as well.  I figure if it doesn't find a wireless card or something, that would be bad!

---

### Post by Ayuthia on 2008-02-09
If you have not used an AMD/Nvidia HP laptop before, there are some models that will not start up without using some kind of noapic kernel parameter to start.  There is a chance that it will have a Broadcom wireless card so it should detect it, but you will not be able to connect with it until you have installed the firmware or NDISwrapper.

I have an HP dv6338se that works with noapic noirqdebug and have no problems when using gutsy.  However, I know someone that has a dv9000 series with AMD/Nvidia/Broadcom combination and was not able to get Gutsy to work.  However, he is able to get 32-bit Hardy to work without any kernel parameters

I am not trying to have you not purchase it, but make you aware that there might be some work involved to get Ubuntu to work.  It does seem that Hardy might be better, but it is in alpha still.

---

### Post by tomsa on 2008-02-13
Well.....I appreciate the input from everybody.....and I have made my purchase.  I got a Gateway T-1625 this past weekend.  I did like I said I would and took a live CD with me to the store- I would have to say that was a great decision, and I would recommend it to anyone.  I wasn't able to get ANY of the HP laptops to boot at all.  The Gateways and Dells did fine, but the price was right on the Gateways.  A funny side note to all of this is, apparently I managed to unblock the wi-fi connection on all the computers I tried at best buy.  The management wasn't happy about it either- since neither they nor the geek squad could figure out how to remedy the situation.  

Unfortunately,  my computer still has Vista on it, and I hate it.  I was going to wait until my wife was out of town next week to do it, but I jst can't stand it any more.  Neither can she (I have a convert on my hands! Yay!)  I may very well start partitioning right after I finish this post!  Cheers!

---

### Post by Wollombi on 2008-05-21
Ok, I know the original poster bought a different model, but I thought I'd post for informational purposes anyway.  

I am using this laptop with Kubuntu Hardy (8.04) 64-bit and had very few problems.  

Since it uses an Aetheros wireless card, you need to use NDISWrapper and the XP driver, and I have a script I found on the net somewhere (don't remember where now, sorry, but I can post if anyone needs it - just remember I didn't author it) to make the wireless work. 

One small problem I have is if I use the hardware button on the touchpad to disable it, then push it to re-enable it, kded crashes and I can no longer use the mute/volume controls on the touch strip above the keyboard.  Minor gripe, but it will bug me until I find a fix.  Yes, I'm neurotic. :)

Other than that, no real problems.  The restricted drivers work for the NVidia card, so I didn't have to download from NVidia and compile.

I have NOT tried prior versions (7.10, 7.04) on this laptop, so YMMV with those.  Hardy is a LTS release though, so why not use it?

Any questions feel free to ask.  I'll answer them if I can.

---

### Post by nosklo on 2008-06-01
> **Wollombi said:**
> 
Since it uses an Aetheros wireless card, you need to use NDISWrapper and the XP driver, and I have a script I found on the net somewhere (don't remember where now, sorry, but I can post if anyone needs it - just remember I didn't author it) to make the wireless work. 


I am installing ubuntu on this laptop (Pavilion dv6707us) for a friend. Everything works but wifi. Latest Madwifi doesn't work. So I am turning to NDISWrapper. If you can post this script for me it would be very helpful. I also have trouble finding Windows XP drivers since NDISwrapper refuse to work with the Vista drivers that are already in the laptop (in C:\Windows\System32\Inf\netathr.inf and C:\Windows\System32\Drivers\ath.sys)
If you can post the windows XP drivers that worked for you, I will greatly appreciate. My personal email address is nosklo [AT] gmail (dot) com. Thanks in advance.

---

