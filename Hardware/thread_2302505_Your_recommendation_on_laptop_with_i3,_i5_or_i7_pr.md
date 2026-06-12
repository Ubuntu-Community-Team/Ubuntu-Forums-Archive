---
title: "Your recommendation on laptop with i3, i5 or i7 processor"
date: 2015-11-10
forum: Hardware
---

### Post by DVD-R on 2015-11-10
Hi all,
I'm looking for a refurbished laptop that I can setup with a dual-boot.
Win-7-pro and Ubuntu.

I would like to pickup a unit with an i3, i5, or i7 processor.
There are some units out there that have various challenges to deal with, such as graphics issues etc.
Does anyone have experience with a laptop with i3,i5 or i7 in which you had an easy no-challenge installation of Ubuntu?
I would appreciate your experiences with such a unit.
Sincere thanks  :-]

---

### Post by sudodus on 2015-11-11
A refurbished or 'second-hand' professional class computer is a good alternative to a new consumer class computer for the same price.

In my family we have 3-5 year old HPs and a Toshiba with Intel i5 processors, that work well with Windows and Ubuntu. They run well in BIOS mode and it is possible to run in UEFI mode too. The HPs were refurbished with Windows 7 in BIOS mode, and I installed Ubuntu as dual boot. The Toshiba was delivered with both Windows 7 and 8 (optical install disks were supplied), and I can install dual boot systems in BIOS as well as in UEFI mode. I have been using this Toshiba for testing new versions of Ubuntu based operating systems, mainly Lubuntu and ToriOS, and for testing my own linux tools.

We have the following computers with Intel i5 processors,

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02782591](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02782591)
[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879)
[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

but I think most similar computers of the same age will work. It is more difficult to install dual boot system (with Ubuntu alongside Windows) into several of the newer HP and Toshiba computers because of non-standard UEFI systems, that try to lock the computer to Windows.

-o-

You should check that the graphics and wifi chips have linux drivers, either that the built-in linux drivers work, or that there are proprietary drivers.

---

### Post by oldfred on 2015-11-11
I believe all i-series Intel based systems were UEFI. But first gen also were early UEFI/BIOS by vendors and often had issues, but then Ubuntu's early implementation of UEFI was also under major development. I would avoid first gen Intel i-series. Or only consider BIOS install.

But now they are releasing 6th gen - Skylake and those also have some issues as so new that driver development has not caught up yet. 

Just about every other brand system can be installed with UEFI or BIOS. The Windows 7 DVD only installs in BIOS mode, so drive must be MBR(msdos). But DVD can be copied to flash drive and slightly reconfigured for UEFI boot. 

Dell was one of the few to offer its own update to its top end developer version (expensive) back with 12.04 called sputnik. But supposedly all the sputnik updates were built into 14.04. But now they are releasing an even newer model. 
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by mastablasta on 2015-11-12
+1 to business class/profesional computer from HP. they are SUSE EL certifies I believe. 
some dells come Ubutnu preloaded.

and then there are Zareason and System76

---

### Post by ilya9 on 2015-11-12
Well, Ii'm using this one for more than 1 year: [www.samsung.com/ca/support/model/NP470R5E-K01CA]("http://ubuntuforums.org/www.samsung.com/ca/support/model/NP470R5E-K01CA"). It's awesome. Intel Core i5, 8 Gb RAM, AMD Radeon HD 8xxx Series. For best experience install some nice OS such as Ubuntu or Win7 x64 Ultimate.

---

### Post by Bucky Ball on 2015-11-12
You make no mention of what you want to do with the machine. If you surf the web, email, listen to music and watch videos and not much more you don't need an i7, or an i5. I do that and more with an i3. :) Defining what you plan to do with the laptop may help to narrow the focus and possibly save you some money.

It is things like graphics and wireless cards you need to be concerned with rather than the processor (once you've decided on the appropriate processor for your needs, of course).

---

### Post by DVD-R on 2015-11-12
Thanks all for your great comments.
I've had to do some homework on what the UEFI bios.
And I think Bucky's point is well taken....I do have a few programs that heat the processor up for a few minutes, but for the most part, I don't need a super machine.
I appreciate greatly your recommendations on specific units.
I'll look into those in particular.
Sincere thanks!!!

---

### Post by pqwoerituytrueiwoq on 2015-11-12
i would suggest 2ed gen intel
personally i use my laptop to light duty work cause it is a mobile device i have a desktop for the heavy lifting
for a laptop i suggest a Pentium cpu (2ed gen or better) with at least 2Ghz
alot of the time the i3/i5/i7s have lower clock speeds to compensate for the extra heat don't neglect clock speed for more cores/threads, 9 times out of 10 it is not worth it to trade clock speed for more cores/threads
Pentium chips are basically i3s without hyper threading, sometimes have a slightly weaker iGPU

i have been very happy with my laptop (link in signature) it will probably be hard too find though

---

### Post by sammiev on 2015-11-12
I'm running a Intel i5 with 8GB memory and a 240 SSD.

I can load most OS in a few seconds.

It's actually overkill as the owner is too slow to keep up.

---

### Post by Linuxisfast on 2015-11-14
Thinkpads are super well made mil spec laptops for refurbished models. I bought two x220 in mint condition from Computer Overhauls NYC and both run 14.04.3 perfectly with full functioning fingerprint scanner and all buttons.

---

### Post by hotsummer55 on 2015-11-15
I would look for a laptop with non-dedicated intel graphics as you won't have any problem with drivers and the performance is fine for all but heavy graphics requirements ,gaming.
If you can create a live boot usb drive and if possible try it on the laptop before you buy.
Try to get one with intel wifi as well as you will have less problem with the wifi as well.

---

### Post by DVD-R on 2015-11-18
Ended up getting a refurbished Thinkpad T520, 15.6" screen, i5, 64bit-windows-7-home.
The installation of ubuntu was just as easy as any other PC I've done installs on.
I did change the bios option to Legacy.
But the house-hold really likes this unit!
On-ward and upward! :-]

---

### Post by Bucky Ball on 2015-11-18
Good news. Please see first link in my signature to help others. Enjoy the new machine. :)

---

