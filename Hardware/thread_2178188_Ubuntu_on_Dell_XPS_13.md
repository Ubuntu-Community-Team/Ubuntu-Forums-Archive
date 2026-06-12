---
title: "Ubuntu on Dell XPS 13"
date: 2013-10-02
forum: Hardware
---

### Post by Cyb3 on 2013-10-02
Hello everybody,

I don't know if this thread is on the right forum but if it isn't, please move it. Anyway. I've been thinking about getting a new laptop. What i have read on the internet and watched on YouTube it seems like a good idea to get the Dell XPS 13 Developer Edition. But just wanted to ask you guys about this laptop, if anyone have it or tried it out. What's your opinion of it? Are there other laptops that will be awesome with Ubuntu on it?

Thanks in advance!

---

### Post by TheFu on 2013-10-02
I like my Dell 1558.  I wish the screen had higher resolution - 1080p is extremely limiting.  I miss my D600 with 1440p resolution. The HDD is fast, plenty of RAM, eSATA ports, 1000base-tx ethernet .... wish I'd spent the extra $10 for a better wifi card for the 2 hrs a week I use wifi.  Besides that, I'm still in love with this 3 yr old laptop. It is the best I've ever owned (for my needs).

However, I never take it on airplanes. I use a netbook or tablet for that. a laptop is too heavy for travel and I travel internationally about 8 weeks a yr.  My netbook lets me have a full OS (Ubuntu), encrypted partitions since any portable device **must** be encrypted, and a good remote access client back to my servers at home that have nearly unlimited processing, RAM, disk and networking. [Remote desktops rock]("http://blog.jdpfu.com/2012/10/23/remote-desktops-rock").

What do you plan to do with this laptop? How I use a laptop means nothing unless you use it the same way.

In most cases, getting a cheap netbook ($250) and a cheap desktop ($450) will provide more computing power than any laptop can provide. If you edit code all day, using a remote desktop back into your $450 Core i7 box will be much better than any laptop can match.  I read about a guy that pays $10/month for a VPS and uses his ipad for his remote desktop.  I've been doing something similar for about 2 yrs now.

OTOH, if you need to do video editing all day, then a netbook/remote desktop is not a viable option, but for almost every other normal development task, it is the best, most cost-effective, answer.

---

### Post by Cyb3 on 2013-10-02
> **TheFu said:**
> I like my Dell 1558.  I wish the screen had higher resolution - 1080p is extremely limiting.  I miss my D600 with 1440p resolution. The HDD is fast, plenty of RAM, eSATA ports, 1000base-tx ethernet .... wish I'd spent the extra $10 for a better wifi card for the 2 hrs a week I use wifi.  Besides that, I'm still in love with this 3 yr old laptop. It is the best I've ever owned (for my needs).

However, I never take it on airplanes. I use a netbook or tablet for that. a laptop is too heavy for travel and I travel internationally about 8 weeks a yr.  My netbook lets me have a full OS (Ubuntu), encrypted partitions since any portable device **must** be encrypted, and a good remote access client back to my servers at home that have nearly unlimited processing, RAM, disk and networking. [Remote desktops rock]("http://blog.jdpfu.com/2012/10/23/remote-desktops-rock").

What do you plan to do with this laptop? How I use a laptop means nothing unless you use it the same way.

In most cases, getting a cheap netbook ($250) and a cheap desktop ($450) will provide more computing power than any laptop can provide. If you edit code all day, using a remote desktop back into your $450 Core i7 box will be much better than any laptop can match.  I read about a guy that pays $10/month for a VPS and uses his ipad for his remote desktop.  I've been doing something similar for about 2 yrs now.

OTOH, if you need to do video editing all day, then a netbook/remote desktop is not a viable option, but for almost every other normal development task, it is the best, most cost-effective, answer.

I understand that, that laptops have different uses. But what about the built quality, interaction with the hardware, batterylife, screen etc. I think this is great because of Dell works closely with Ubuntu. I want to have a very slick and fast computer though intend to have the  computer for some years without feeling i need to switch to a faster  laptop later in the future. Because i take my computer with me a lot i don't want to  have such a "heavy/big" laptop. 

I will mostly use the laptop for programming and maybe some Photoshop/Lightroom use on it.

---

### Post by oldfred on 2013-10-02
Some more info here:

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by TheFu on 2013-10-02
> **bnrW66w said:**
> I understand that, that laptops have different uses. But what about the built quality, interaction with the hardware, batterylife, screen etc. I think this is great because of Dell works closely with Ubuntu. I want to have a very slick and fast computer though intend to have the  computer for some years without feeling i need to switch to a faster  laptop later in the future. Because i take my computer with me a lot i don't want to  have such a "heavy/big" laptop. 

I will mostly use the laptop for programming and maybe some Photoshop/Lightroom use on it.

To me, any "laptop" is too heavy to carry more than between buildings, so we have extremely different use requirements.
I did write a few "laptop selection articles" a few yrs ago when I was in the market that might get you thinking about things you haven't considered yet.  [http://blog.jdpfu.com/2010/04/23/buying-a-laptop-stuff-to-know](http://blog.jdpfu.com/2010/04/23/buying-a-laptop-stuff-to-know) has a link inside to the older article. Both are 

I haven't used a laptop (currently a Core i5) on battery more than 15 minutes in years. OTOH, I use my netbook for 5+ hrs every weekend in a programming class and once a month giving presentations - while remote connected to my "desktop" in a private cloud.

I find the build of Dell non-business computers to be fine, but not nearly as good as the business line ... which usually adds $500 to the price.

With dual-GPU laptops, you'll want to figure out the dual-GPU support methods - usually the onboard Intel is used on battery and the ATI is used under power, for example. That switchover can be problematic.

Also, during recent programming classes people with extremely thin laptops didn't bring the dongle necessary to plug into an ehternet port. Because wifi sucked, those people were left taking notes during a hands-on programming class.  Not good.

* battery life (unimportant to me); might need user swappable batteries.
* keyboard "feel" (most important - had a laptop with terrible feel and couldn't touch-type on it)
* resolution (1080p min) - discrete GPU
* ports (USB3/eSATA/GigE)
* SDHC reader (camera photo xfers)
* wifi 300Mbps or greater - I've been burned
* 3r gen core i5 CPU
* 6G+ RAM
* 500G+ HDD ... I prefer spinning disks over SSDs still

Does that model address your concerns?

---

### Post by Cyb3 on 2013-10-02
> **TheFu said:**
> To me, any "laptop" is too heavy to carry more than between buildings, so we have extremely different use requirements.
I did write a few "laptop selection articles" a few yrs ago when I was in the market that might get you thinking about things you haven't considered yet.  [http://blog.jdpfu.com/2010/04/23/buying-a-laptop-stuff-to-know](http://blog.jdpfu.com/2010/04/23/buying-a-laptop-stuff-to-know) has a link inside to the older article. Both are 

I haven't used a laptop (currently a Core i5) on battery more than 15 minutes in years. OTOH, I use my netbook for 5+ hrs every weekend in a programming class and once a month giving presentations - while remote connected to my "desktop" in a private cloud.

I find the build of Dell non-business computers to be fine, but not nearly as good as the business line ... which usually adds $500 to the price.

With dual-GPU laptops, you'll want to figure out the dual-GPU support methods - usually the onboard Intel is used on battery and the ATI is used under power, for example. That switchover can be problematic.

Also, during recent programming classes people with extremely thin laptops didn't bring the dongle necessary to plug into an ehternet port. Because wifi sucked, those people were left taking notes during a hands-on programming class.  Not good.

* battery life (unimportant to me); might need user swappable batteries.
* keyboard "feel" (most important - had a laptop with terrible feel and couldn't touch-type on it)
* resolution (1080p min) - discrete GPU
* ports (USB3/eSATA/GigE)
* SDHC reader (camera photo xfers)
* wifi 300Mbps or greater - I've been burned
* 3r gen core i5 CPU
* 6G+ RAM
* 500G+ HDD ... I prefer spinning disks over SSDs still

Does that model address your concerns?

I'm not interested in a big HDD so i'm going to stick with SSD. What are your suggestions on the business models of Dell? Can you give me some links with options for me to buy? Btw the screensize should not go over 15 inch. Yes i agree with the keyboard feel, it's very important for me too.

---

### Post by TheFu on 2013-10-02
> **bnrW66w said:**
> I'm not interested in a big HDD so i'm going to stick with SSD. What are your suggestions on the business models of Dell? Can you give me some links with options for me to buy? Btw the screensize should not go over 15 inch. Yes i agree with the keyboard feel, it's very important for me too.

I am not in the market for any laptops now and the models change every 6 months. Sorry.

I don't expect to purchase a laptop ever again. 10" or less remote access devices with a real-OS.

---

### Post by Kevin_Arnold on 2013-10-02
It seems you can't purchase the XPS 13 Dev Edition directly off their site anymore. Maybe it'll still work if you call them. There used to be a purchase button but now it just says to call their support.

---

### Post by Cyb3 on 2013-10-02
> **Kevin_Arnold said:**
> It seems you can't purchase the XPS 13 Dev Edition directly off their site anymore. Maybe it'll still work if you call them. There used to be a purchase button but now it just says to call their support.

Wierd, because i can order it in Sweden where i live. Link: [http://www.dell.com/se/foretag/p/xps-13-linux/pd](http://www.dell.com/se/foretag/p/xps-13-linux/pd)

---

### Post by Kevin_Arnold on 2013-10-04
> **Cyb3 said:**
> Wierd, because i can order it in Sweden where i live. Link: [http://www.dell.com/se/foretag/p/xps-13-linux/pd](http://www.dell.com/se/foretag/p/xps-13-linux/pd)

Yeah, I heard it is still available in other regions but for some reason the US site won't sell it directly to you. They offer up Windows versions instead.

---

### Post by TheFu on 2013-10-05
> **Kevin_Arnold said:**
> Yeah, I heard it is still available in other regions but for some reason the US site won't sell it directly to you. They offer up Windows versions instead.

Inside the USA, Linux just isn't as popular with "regular people" - most people have **never** even heard the term, IME.  Having a product line and supporting is gets expensive, so if they've been unable to sell a certain number of units, it just isn't cost effective to keep the offering. Sad, but try.

Or it could be a contract clause between the 2 parties. Probably not anymore.  Plus, selling a Win-based PC lets Dell add-on all the crapware to lower the price more than the OEM Win install costs.

My eyes have been opened recently after an installfest last month. Getting Linux installed on some newer PCs is ... er ... non-trivial.  We failed completely with 2 laptops with 5 experts helping. It was the UEFI issues that we were unable to get passed, plus the lack of knowledge about the computers from the owners. This event was at a local university where not all the students had high power laptops, so virtualization resulted in less than great results.

Or it could be that "I have issues." ;)

---

### Post by Kevin_Arnold on 2013-10-07
Sad thing is, I'd actually like an updated XPS 13 Dev Edition. Keep the price about the same and upgrade to the newest processor and I'd be in... or lower the price on the current hardware.

---

