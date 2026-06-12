---
title: "Is there an inherent problem with ati radeon?"
date: 2012-05-24
forum: Hardware
---

### Post by samwillc on 2012-05-24
Hi everyone,

My setup: 64-bit, AMD Phenom XII, 3.71GHz, 8GB DDR3, Ati Radeon 5450 (<---the weak link so it seems...)

I tried linux mint 13 cinnamon DE which resulted in numerous restart errors after enabling 'additional drivers' for ati radeon HD4xxx.

Is there a problem with ati radeon graphics cards on linux? I read a few other posts where people were also having problems. This is slightly worrying as surely an OS should support any hardware, never had a problem in windows.

Maybe this is just a linux mint problem? Does this card work in ubuntu 12.04 or xubuntu 12.04 with the additional drivers installed?

I don't understand why a certain graphics card wouldn't work in certain desktop environments using linux. Is this not a crippling disadvantage to many users if this is the case?

Any thoughts are most appreciated.

Thanks.

Sam.

**edit** is it best just to use the standard drivers for this card? Will enabling additional drivers add anything other than problems? I do no 3D graphics or video editing, most demanding thing I do is watching an (1080p) HD movie.

---

### Post by eleftg on 2012-05-24
Why don't you first try to install ubuntu x64 on your machine and see if it works? Then if anything similar happens you can post for help. I have never used Linux Mint so I can't help you.

Anyway, truth is AMD drivers don't always work flawlessly on all Linux distributions and hardware. For example I have a dual GPU setup on my laptop with a discrete AMD RADEON and an integrated Intel GPU and I only use the integrated one. The reason is fan overspeed problems with RADEON and unity reverting back to unity2d without me choosing it. So I completely disable it from vgaswitcher.

It feels strange to say this in 2012 but until AMD publishes better (closed-source unfortunately) Linux drivers there is little that can be done from the Linux community

---

### Post by coffeecat on 2012-05-24
> **samwillc said:**
> Ati Radeon 5450 (<---the weak link so it seems...)

Not at all. I have a card with that GPU. For me, it "just works" - with the default open source driver, that is.

> **samwillc said:**
> **edit** is it best just to use the standard drivers for this card? Will enabling additional drivers add anything other than problems? I do no 3D graphics or video editing, most demanding thing I do is watching an (1080p) HD movie.

Basically, yes. With the HD5450, the default open source driver will give you perfectly adequate performance for all that you list, including watching 1080 HD movies. I've used four different ATI GPUs with different releases of Ubuntu - Mobility HD4200, HD4350, HD5450 and HD6450 - and performance for each with the open source driver has fulfillled my needs. My limited experience of the proprietary driver has convinced me that I am better off with the open source one.

---

### Post by samwillc on 2012-05-24
Ok, thanks people.

@eleft - I have installed linux mint 12, linux mint 13 (mate and cinnamon), xubuntu 12.04, ubuntu 12.04 (tried classic and unity). All 64 bit versions and all clean installs.

@coffeecat I will try with the open source drivers and see whether I get any issues. If it continues, I may just buy an nvidia card, I presume suggestions should be for another thread.

Sam.

---

### Post by Carl H on 2012-05-26
I also have had numerous problems with installing any 64 bit Linux onto my new AMD A6 with integrated Radeon graphics. All boot to a black screen (and then the monitor goes into sleep mode after complaining of no video input), unless the kernel parameters are changed from 'quiet' to 'nomodeset'. 

I've eventually got a usuable Ubuntu 12.04 system, apart from the screen resolution cannot be set higher than 1280x960, so it doesn't look great on a widescreen 24" monitor. 

I haven't yet tried the proprietary driver with Ubuntu, although I tried it with Mint and it totally bombed the system completely.

---

### Post by coffeecat on 2012-05-26
> **Carl H said:**
> I also have had numerous problems with installing any 64 bit Linux onto my new AMD A6 with integrated Radeon graphics. All boot to a black screen (and then the monitor goes into sleep mode after complaining of no video input), unless the kernel parameters are changed from 'quiet' to 'nomodeset'.

You don't say which Radeon graphics that is. That is important. The motherboard in the machine I'm posting from has integrated Radeon HD3000 which I quickly concluded was not worth bothering with when I first assembled the computer. This didn't matter because I knew I was going to use a PCIe card, and HD4350, HD5450 and HD6450 PCIe cards each give me good service with the open source drivers with this motherboard.

---

### Post by Carl H on 2012-05-26
> **coffeecat said:**
> You don't say which Radeon graphics that is. That is important. 

It's a 6530D.

---

### Post by samwillc on 2012-05-26
I actually changed my card to an nvidia 440GT.

I want up-to-date drivers to continue using linux into the future and if ati can't provide, then they lose out on my ££££.

Sam.

---

### Post by QIII on 2012-05-26
It's not as though there are no posts from people having problems with NVIDIA cards...

The "Additional Drivers" method of installation works for many and doesn't work for others.  I don't use it for just that reason.

ATI does support Linux, with a special affinity for Ubuntu.
Please see link in my signature.

---

### Post by samwillc on 2012-05-26
Not quite what I wanted to hear after shelling out on a new card... although the ati install looks a pain in the a**e. My current card was very easy.

Anyway, too late now! Thanks for the links. Will bear it in mind for the future if I use an ati card again.

Sam.

---

### Post by Yellow Pasque on 2012-05-26
Please mark the thread SOLVED.

---

### Post by chome4 on 2012-06-07
> **samwillc said:**
> Hi everyone,

My setup: 64-bit, AMD Phenom XII, 3.71GHz, 8GB DDR3, Ati Radeon 5450 (<---the weak link so it seems...)

I tried linux mint 13 cinnamon DE which resulted in numerous restart errors after enabling 'additional drivers' for ati radeon HD4xxx.

Is there a problem with ati radeon graphics cards on linux? I read a few other posts where people were also having problems. This is slightly worrying as surely an OS should support any hardware, never had a problem in windows.

Maybe this is just a linux mint problem? Does this card work in ubuntu 12.04 or xubuntu 12.04 with the additional drivers installed?

I don't understand why a certain graphics card wouldn't work in certain desktop environments using linux. Is this not a crippling disadvantage to many users if this is the case?

Any thoughts are most appreciated.

Thanks.

Sam.

**edit** is it best just to use the standard drivers for this card? Will enabling additional drivers add anything other than problems? I do no 3D graphics or video editing, most demanding thing I do is watching an (1080p) HD movie.

Not a problem with the card, just not been tested during the creation of this distribution of Linux!

---

