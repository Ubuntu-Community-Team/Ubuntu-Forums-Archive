---
title: "Unable to install Ubuntu on Neo B2145N Notebook"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by yoshimira80 on 2009-07-12
[FONT="Arial"]Hello Ubuntu world!
forgive me if I'm posting in the wrong place, I'm a TOTAL noobie here.
Till now I've never contributed to the forum, only used it to browse for solutions to my own problems. But today, I'm not the only one with my problem and none of my peers having the same problem have been able to find a solution either. So here I beg for your assistance.

I have recently purchased a Neo Basic B2145N laptop. (specs to follow) I have tried to install ubuntu from Feisty Fawn, all the way up to Intrepid Ibex, with no luck.

Using the Live-CD is completely useless. Where the Alternate CD shows promise, it is a let-down when upon reboot, all that comes up is a black screen with a cursor (on all versions) I also tried using the "install inside windows" option of Hardy Heron which yielded the same result, shockingly.

I have also tried to install the "g-OS" operating systems with the same, or similar results.

The specs of my machine are:

•Neo Basic B2145N Notebook
•Intel Pentium Dual Core T3400 Processor 
(2.16GHz, 667MHz FSB, 1MB L2 Cache)
•Memory:                2GB DDR2
•HDD:                   250GB SATA
•LCD:                   14.1" WXGA
•ODD:                   DVDRW SuperMulti
•BIOS Version/Date:	OEM 1.14, 1/15/2009	
•SMBIOS Version:        2.5
•Graphics:              SiS Mirage 3 Graphics (128MB RAM)

Does anyone at all have any suggestions of what I might try, to get Ubuntu running on my new laptop?


[/FONT]

---

### Post by yoshimira80 on 2009-07-12
Also, I should point out:

this laptop has no trouble whatsoever in running windows XP, Vista Ultimate or Windows 7.

---

### Post by note32 on 2009-07-12
it might be your graphic card i have had a friend of mine that had the same problem

---

### Post by b@sh_n3rd on 2009-07-12
Hi **yoshimira80,** welcome to the community!...

If all you are getting is just a cursor in a black background after you install Ubuntu, it *could* be a video card issue. I dunno how many times I've said this now :D (don't get me wrong, it's not a limitation of Ubuntu). Well, have you tried Jaunty Jackelope? That is just a month and a half old and might have more compatibility to your PC. Until then, I'll do some digging on your card...The card just* sounds* familiar to me but I'm not quite sure about it...

**EDIT:** Just remembered, I helped a dude with a similar prob on Intrepid with a VIA graphics adapter. Later on I tried Jaunty on a different PC that included a VIA adapter too. In this case, Jaunty had no problem in loading to the desktop. Jaunty *does* however contain a few bugs in relation to Intrepid, but does also include some advantages such as this over the latter. This is why I thought of suggesting Jaunty...Hope this helps...

---

### Post by b@sh_n3rd on 2009-07-12
Hey apparently the SiS cards are supported by an open source driver and proprietary drivers are not to be used. I found a link on the Ubuntu community documentation. Try this for more info on the driver: [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml) If you encounter any probs, ask here :D...Hope this helps...

---

### Post by yoshimira80 on 2009-07-12
wow, thanx you guys for FAST response!! I'll look into those right now! :)

---

### Post by yoshimira80 on 2009-07-16
sadly, this winischhofer.eu bit is usless to me :( I can't understand what it's suggesting that I do...

---

### Post by yoshimira80 on 2010-03-23
so, I finally got Ubuntu on my notebook (10.04) but the display is stretched. I searched for means to update the video card driver but when I downloaded it, I discovered that its already installed and currently running.. however, my display option is limited to 800x600 (4:3) ... I need 1280x800 (16:9) ... 

does anyone know how to do that? I feel like such an imbecile when working with Linux... I love it but i don't think it loves me.

---

### Post by Slim Odds on 2010-03-23
> **yoshimira80 said:**
> so, I finally got Ubuntu on my notebook (10.04) but the display is stretched. I searched for means to update the video card driver but when I downloaded it, I discovered that its already installed and currently running.. however, my display option is limited to 800x600 (4:3) ... I need 1280x800 (16:9) ... 

does anyone know how to do that? I feel like such an imbecile when working with Linux... I love it but i don't think it loves me.

If you have the correct video driver installed, it should let you pick the correct resolution. Sometimes it's hard to get it right.

BTW, 1280x800 is 16:10

---

