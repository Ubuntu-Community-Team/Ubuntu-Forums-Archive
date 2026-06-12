---
title: "need new motherboard"
date: 2018-02-27
forum: Hardware
---

### Post by jgw on 2018-02-27
I currently have a gigabyte motherboard f2a68hm-h.  It is a mini atx board and has a 2x amd a4-7300 apu   and 8gb of memory.  I want to replace that motherboard with a mini-atx board with a better layout.  I have been checking out a number of these goards.  Gigabyte seems to have one that might work  (GIGABYTE GA-F2A78M-HD2 REV.3.0, Gigabyte GA-F2A75M-D3H REV 1.1. etc ), and which I could transfer my cpu and memory to, but its got a strange graphics situation.  First they tell me that they have a AMD Radeon HD 8000/7000 installed on board.  I checked that out and, evidently, can be dealt with by ubuntu.  Then I started reading further and I think they also want me to install a radeon display card as well.  This confuses me.  Is the onboard radeon really onboard or what or do I need an additional card.  If I install an additional card will ubuntu be able to deal with that.  On the other hand perhaps I should just find another card?

Before I bite that bullet I thought I would put this out there and get some advise.  

Thank you......................

---

### Post by kerry_s on 2018-02-27
i heard gigabyte is not very linux friendly. they recommend more for windows.

---

### Post by QIII on 2018-02-27
I have had a number of Gigabyte boards that have worked just fine for me running Linux.  There was a problem for some time with iommu, but I believe that has been ironed out.

---

### Post by him610 on 2018-03-02
Is this your current board, GIGABYTE GA-F2A68HM-H FM2+ AMD A68H SATA 6Gb/s USB 3.0 HDMI Micro ATX AMD Motherboard? Recommend you compare the specifications of each alternative replacement board with the specifications of your original board especially CPU socket, memory specs, and physical size.  A full size ATX board will not fit in a MicroATX case; however, a mini-ITX board will fit in a MicroATX case, but you will probably only have one expansion slot.
By the way, I have never experienced any issues with Linux installed on Gigabyte boards - I have two machines with Gigabyte boards.
Good luck,

---

### Post by jgw on 2018-03-05
thanks for the reply!

I have nothing at all against gigabyte boards.  I now plan to update my existing board more to update and any problems as I fixed my problem with connecting with a 4k tv.  So, I will take my time, and get a better display card (built to handle 4k and also update the motherboard whilst I am at it.  The radeon built in graphics, plus an card seems a bit too complex for me although I suspect its dandy for a game player who have always, for many years, demanded the very best graphics available.  Since my current setup is close to 10 years old I think its probably time for a real upgrade.

---

### Post by jgw on 2018-03-21
I now have the new motherboard (GA-F2A78M-HD2)   I am going to use a AMD A8-7650k Black Edition A-series APU With Radeon R7 Graphics AD765KXBJASBX and, apparently, this should work according to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).  This, in theory will also work on a 4k motherboard.  My thought is to simply replace the motherboard on my installed 16.04.3 and, again in theory, it should just boot up and automatically swap out my nvidia driver for something that will run the radeon.  Before I embark on that one, however, I thought I would post this in the hope that somebody will tell me if what I am planning will work or not before I wreck anything.

Thoughts?

---

### Post by Yellow Pasque on 2018-03-21
>  it should just boot up and automatically swap out my nvidia driver

Uninstall the nvidia driver before removing the old motherboard. It will make life easier.

---

### Post by jgw on 2018-03-22
Thanks for the reply - I was wondering about that one but wasn't sure.

---

### Post by jgw on 2018-03-29
Ok, I thought I had gotten rid of all my nvidia stuff.  I found a number of suggestions to remove the nvidia stuff and it failed.  Anyway, after I thought I had done that I installed the new motherboard.  I could never get anything  on the screen so I gave up, reinstalled the old motherboard and checked to see what was going on.  Seems none of the nvidia stuff was gone and I was using exactly the same driver (nvidia 340) that I thought I had gotten rid of.   I also suspect this is why there was nothing on the monitor (I am going to check this to make sure).  If anybody knows what I should have done to get rid of the nvidia stuff I would be grateful.  Here is what I tried:
$ sudo apt-get -s purge 'nvidia-*'
sudo apt-get remove --purge nvidia-*

---

### Post by jgw on 2018-03-30
I think I have been fighting this battle the wrong way.  My old motherboard (AMD A4-7300 APU Dual Core Radeon CPU Processor HD8470D Graphics) has built in radeon hd8470D graphics which, in theory will work in ubuntu 16.04 ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)) I should be able to simply remove the nvidia display card and ubuntu will magically see the built in graphics?  If this is true then I can just setup this motherboard and if it works then, when I swap the motherboards out I should be in fat city.

I also notice that I am getting no responses to these last two and should probably start all over in a new topic? (which I will do if nobody responds as this is getting kinda old)

---

### Post by rbmorse on 2018-03-30
When you boot after removing the nVidia graphics card, check the BIOS setup for settings that pertain to the video subsystem...there might be one you need to change to enable the onboard graphics.

---

### Post by jgw on 2018-03-30
GREAT idea!  Seriously, I know about that but would have foregotten.  Thank you!

---

