---
title: "[SOLVED] HP Debranded desktop"
date: 2008-08-18
forum: Hardware
---

### Post by Psychicfriend on 2008-08-18
Hi all, Does anyone know about HP Debranded refurbished desktop computers.
Computerg**ks.com has them for real cheap $249 w/ AMD Athlon 64 X2 5000+ processor (2.6 GHz) 1GB RAM 320GB HD but no operating system or documentation. I was wondering if anyone here knows if it would be easy to find all necessary drivers for it's hardware when installing Ubuntu on it. And will the BIOs be an issue? 

Ummm yah. Any help would be appreciated.

---

### Post by tamoneya on 2008-08-18
just to make sure we are on the same page I looked at this computer:[http://www.geeks.com/details.asp?invtid=TS-0006A-AMDX625-R&cat=SYS](http://www.geeks.com/details.asp?invtid=TS-0006A-AMDX625-R&cat=SYS)

There is nothing there that jumps out at me saying it wont work.  It should work pretty well but I dont have the full specs.  For example I would like to know what type of graphics card it has but I cant tell.  Even if it is a worst case scenario (ATI) it would still be possible to get the drivers for ubuntu.

---

### Post by zoken on 2008-08-18
> **tamoneya said:**
>  Even if it is a worst case scenario (**ATI**) it would still be possible to get the drivers for ubuntu.

I think you meant NVidia.
ATI now offers a better Linux support than NVidia.

---

### Post by NoVista on 2008-08-18
What?????????

OMG, I can see all the others now coming out of the ATI JUNGLE to lynch you for saying such an absurd thing.

---

### Post by jimv on 2008-08-18
> **zoken said:**
> I think you meant NVidia.
ATI now offers a better Linux support than NVidia.

It's more accurate to say that ATI is just as good as Nvidia, considering that Nvidia's drivers work perfectly in nearly all cases.  I'm not sure how you get better than that.

---

### Post by tamoneya on 2008-08-18
> **zoken said:**
> I think you meant NVidia.
ATI now offers a better Linux support than NVidia.

ATI is all open while nvidia is proprietary.  The ATI drivers will most likely surpass nvidia within the next couple of months but from what I have seen that hasnt happened yet and therefore I will stick with my statement of ATI.  Like I said though it is still possible to get ubuntu working with ATI.

---

### Post by Psychicfriend on 2008-08-19
Anyway, since the hardware info such as integrated video card isn't listed do you think that the Ubuntu install can automatically find appropriate drivers? Especially for the ethernet?

---

### Post by markbuntu on 2008-08-19
Those are probably 2 year old pavillions. They should work just fine. They used ASUS mobos with ati or nvidia video which will work OK. Anyway, at that price you could get a good high power video card, another 1GB of ram and have a great machine. HP desktops are very generic.

---

### Post by Calmor on 2008-08-19
> **zoken said:**
> I think you meant NVidia.
ATI now offers a better Linux support than NVidia.

While ATI has come a long way, I don't think it's time to pat them on the back just yet.

If they had better Linux support, I wouldn't be looking for a cheap NVidia card right now.  I have a Radeon 2600XT as well as an onboard ATI solution, neither of which will configure correctly to work with Mythbuntu.  I've tried the stock "vesa" driver, the "fglrx" driver, Envy's fglrx driver, and I've built and installed the latest driver right from ATI, all to no avail.

I commend their efforts, but there is still work to be done - and if AMD won't open-source the drivers, it's all on them.

---

### Post by sopsaare on 2008-08-19
FGLRX = no working Hardware Video acceleration for Videos With Compiz.
FGLRX = no working Hardware Accelration for moving Windows without Compiz.
FGLRX = no working Wine (at least for me)

NVIDIA = hmm.... pretty much better.

In the other hand of the things, I like Ati more than nVidia, some fair deals and things like that, but because of these sooo good drivers for Linux, I'll never again get Ati card.

---

### Post by Calmor on 2008-08-19
> **Psychicfriend said:**
> Anyway, since the hardware info such as integrated video card isn't listed do you think that the Ubuntu install can automatically find appropriate drivers? Especially for the ethernet?

Since it seems to be a slightly older machine, I think you'll be ok.  Is there any way to contact them for the full specifications?  My current bias against ATI video cards doesn't hold true for all situations - Ubuntu will run just fine in most cases, and even in my case everything but MythTV seems to function normally... 

I wouldn't be too concerned about the ethernet.  In the off chance that the card isn't supported, you could pick up an old PCI ethernet card.  I think 10/100 cards are probably under $10 by now at a computer show or flea market.

---

### Post by Psychicfriend on 2008-08-19
No chance of getting specs on these machines other than a generic model number of "A6000 series" HP Pavillion and the cpu it uses "AMD Athlon 64 x2 5000+". 
Well I think I'm gonna chance it since they just dropped the price to $219.
Thanks for all the help.

---

### Post by Calmor on 2008-08-20
Good luck.  The AMD Athlon 64 x2 processor will not be an issue - I have three AMDs of various ages/classes here - Athlon XP, Athlon 64 x2, and Turion64 x2 - and all three run just fine with Ubuntu and its various flavors.

---

### Post by pwnprog on 2008-08-20
by the sounds of it, i'd say you'll probably be up and running quite easily. just about everything should work right after the install except maybe graphics. for that you'll need to go into your proprietary drivers menu. it should detect that you have a nvidia card and allow you to install the driver on one click! .... well, maybe 2 clicks? 

no more than 2... i promise

and its always good after a fresh install to have a browse through the add/remove programs menu. you might catch something you think you'll need or that might make your computer run better.

in any case, i say do it. that's a good price

---

### Post by George W. Tush on 2008-08-23
The prices on these debranded computers really are impressive.  My computer use is not at all demanding or sophisticated, so the hardware would serve my needs beautifully... so long as the debranded hardware and the Ubuntu software are compatible.

How is loading Ubuntu on one of these "debranded" machines likely to be different than wiping out Windows XP and replacing it with Ubuntu?  

If anyone has good experiences with the purchase of a "debranded" PC, I hope they will publish their comments.

---

### Post by scharkalvin on 2008-12-14
I'm tempted to get one of these machines myself.  Geeks has a large spread of them now from $180 to about $250 ranging from +3800 to +5400 speed and up to 320gb disk.  I'd avoid the mediacenter versions since you're paying extra for an analog tv tuner that probably won't work with Linux and will be obsolete in a few months time.  If you have to install a binary video driver later to get full features it will still work up to 800x600 with the default driver with ANY video hw (everybody supports the basic VESA features).  I just wonder how many IDE and SATA connectors there are (can I add a second disk for raid?)

---

### Post by scharkalvin on 2008-12-22
I've been looking closely at the photos.  It appears that in some of these systems the DVD-RW drive might be an SATA type.  Many SATA DVD/CD/RW drives do NOT work under Linux (yet).  Hopefully the MB has at least one IDE connector so that an IDE DVD-RW drive could be swapped in.

Anybody got one yet?  How did it work out?

---

