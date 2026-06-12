---
title: "Building a new pc"
date: 2008-12-24
forum: Hardware
---

### Post by pjs_flyer on 2008-12-24
Hi all

Having looked at the read-built PCs available, I've decided to take the plunge and build my own instead.  I'm looking to build something as powerful as possible but fully compatible with Ubuntu.  In particular, I want to run 3d effects with side-by-side monitors.  So...if you were to build your ideal pc with these criteria, which components would you choose?

Cheers!

P.

---

### Post by teaker1s on 2008-12-30
look at a bare bones kit and think amd intel and nvidia:popcorn:

---

### Post by kspncr on 2008-12-30
I would definitely say go with AMD for your processor and Nvidia for video. What kind of use is your PC going to see? Gaming? Light use? Regular stuff?

EDIT: Never mind, I see you already said you wanted it to be as powerful as possible. I still go with Nvidia for your video card. A GTX280 if you've got the money, but the GTX260 is probably a better deal overall because it's so much cheaper (btw, both are way overkill if all you want is to run 3d effects). For your processor, I'd go with an AMD X4 @ 2.6Ghz, because that's the fastest clock speed for quad core processors, I believe. For RAM, I've never had any not be recognized by Ubuntu so I'm unaware of any that won't work (and I've tried Crucial, Transcend, GSkill, Super Talent, among others).

---

### Post by rfruth on 2008-12-30
my next box 

[http://www.google.com/notebook/public/05004808999777444482/BDRUqSwoQvr_25ocj]("http://www.google.com/notebook/public/05004808999777444482/BDRUqSwoQvr_25ocj")

---

### Post by logos34 on 2008-12-30
> **kspncr said:**
> I would definitely say go with AMD for your processor and Nvidia for video.

+1

And whatever you do, don't make the mistake of so many people and try to skimp/save a few bucks on the power supply.  Just don't do it or you;ll be sorry.  

You don't have to spend a lot, just enough for a quality unit with enough capacity at load.

The power supply is the most important component you never hear about

---

### Post by dtrot55 on 2008-12-30
I would recommend using Nvidia video card and get an AMD 64.  Also think about what OS you are going to use...are you going to use 32bit or 64bit.  I would look into Asus mobo's or gigabit...def get SATA hard drives...atleast 250gigs minimum...if your going to be doing hard core storage and gaming.  Atleast 4 gigs of ram...pref 1066 but 800 will be fine.  Only thing i can caution you about is gaming...in my experience with a NVIDIA 9800GT gaming still hasn't matched Windows in performance on Ubuntu...it could just be that im still not as good at ubuntu yet..but following forums and using WINE Windows has by far won the battle of FPS.  I would also recomend multiple hard drives incase you want to dual boot windows with ubuntu or something else.

---

### Post by Messyhair42 on 2008-12-30
power comes at a price. i just built an intel machine myself. if you want two monitors nothing less than dual core processor. if you've never built one before don't worry, i hadn't and it was easy to figure out.

---

### Post by Merps on 2009-01-01
An alternative to 1 powerful is 2 not as powerful, one for online use and one for private use eg:

1. Supermicro with Phoenix Bios (defintely not ami bios) board with the Bearlake, Glenwood or Lakeport chipsets see the core 2 section here:

[http://en.wikipedia.org/wiki/Intel_chipsets](http://en.wikipedia.org/wiki/Intel_chipsets)

Cost $100

2.  Cpu 2 core Allendale Celeron 1.6 GHz (released Jan 2008  8) for $59

3.  Ram OCZ or Corsair

That's if you have to buy them as soon as possible, and you might even be able to run 2 monitors of just one of those pcs.

Otherwise if you can wait, wait until the intel Nehalem Westmere 6 core are released later this year, that should do the trick with a phoenix/supermicro mobo.

---

### Post by ruddha on 2009-01-01
Today Intel's cpu's are far superior. I'd go for core 2 duo processor (quadcore is also fine). Some recent AMD  cpu's have problems with Linux compatibility ( [http://www.phoronix.com/scan.php?page=article&item=961&num=7](http://www.phoronix.com/scan.php?page=article&item=961&num=7) ).  Go for an Asus or Gigabyte motherboard (I prefer Asus). Watch out for AMD boards with via chipsets.

Videocards are somewhat more difficult, the ATI 4870 and the 4870 X2 are the best ones on the market and the have the possibility of open source drivers in the near future. Downside is problems in some games with Wine/Cedega/Crossover. On the Nvidia side the 9800 series is a good choice.

Ram wise anything between the 2-4 GB. For casing I always recommend Antec. They are silent and often come with a high quality psu. Don't forget to wear an anti-static bracelet or to take antistatic precautions when building your own pc.

---

### Post by kspncr on 2009-01-01
> **logos34 said:**
> +1

And whatever you do, don't make the mistake of so many people and try to skimp/save a few bucks on the power supply.  Just don't do it or you;ll be sorry.  

You don't have to spend a lot, just enough for a quality unit with enough capacity at load.

The power supply is the most important component you never hear about

I definitely agree with this statement. The power supply probably has the most potential to destroy everything.

---

### Post by teaker1s on 2009-01-01
quiet power supply and cpu cooler are must

---

### Post by starcannon on 2009-01-01
[LIST]
[*]Dual Core AMD or Intel CPU
[*]Nvidia based Mainboard, I like XFX or Abit these days
[*]Twin Nvidia Cards SLI'd together
[*]3~8gb of ram, and a willingness to run a custom kernel or 64bit Ubuntu if you want to go over 3.5gb of ram.
[*]3 large identical sata hard disk drives to set up a sata raid with
[*]And as stated before, a good power supply, don't skimp, 700+ watts, spend around $130+ on this part, its important that its quality.
[/LIST]
GL and have fun, I love building my machines. My current desktop is running twin Nvidia 7950gt's in SLi mode, and it rocks.

---

### Post by pjs_flyer on 2009-01-04
Thanks all, this is very helpful - I'll post back when I've put something together!

In terms of OS, I'm tempted to go with 32-bit.  I've got a laptop running 64-bit, but every now and then I hit something that doesn't play well with 64-bit.  The latest was a Canon MP600 printer, where only rpm (rather than deb) drivers are available anyway, and these only seem to be 32-bit - but that's another thread.

Having said this, if I want plenty of memory it's 64-bit...

P.

---

### Post by pjs_flyer on 2009-01-09
Ok, here's the proposed spec so far:

Intel i7 920 chip
Asus P6T Deluxe motherboard (although I've read that the ethernet setup might not be straightforward - would the Gigabyte GA-EX58-UD5 be any safer?)
NVidia geforce 9800 GTX graphics card (are there any potential problems between different manufacturers' versions of this card?)
6GB of DDR3 ram
Hauppauge WinTV Nova card
Zalman GT1000 Case
Zalman 750W power supply
Zalman CNPS9700 NT cpu fan
Logitech wireless desktop
Several Western Digital Caviar SATA drives set up in a RAID array
Twin 19" LCD monitors (tbc - any reliable/problem makes/models?)
Blu-ray, dvd, cd etc drive (again tbc - any good/bad?)

Any potential issues here?

Thanks!

---

### Post by pjs_flyer on 2009-01-09
(duplicate post, sorry!)

---

### Post by Merps on 2009-01-16
actually I noticed that the core range from intel is loosely based on the greek godess core who goes by the name kora, persephone, proserpine or her roman name libera. Now that's ok if you like cora in your motherboard, however, you might prefer to look at the the xeon wolfdale dual core or dunnington sexa core instead. Those WD hard discs look good too. Xeon is another word derived from the greeks, "xenon greek, neuter of xenos, foreign, strange; see xeno" ,however, it doesn't seem to be specifically tied to the greek pantheon as the core (kora) or the itanium (titans) cpus are, meaning it could in theory be a reference to the christian testament of the bible, otherwise known as the greek or new testament. As far as the celeron cpu goes, it is not greek at all but is instead based on the roman word for swiftness or speed, celer or celeritas.

---

### Post by High_Speed on 2009-01-16
> **Merps said:**
> actually I noticed that the core range from intel is loosely based on the greek godess core who goes by the name kora, persephone, proserpine or her roman name libera. Now that's ok if you like cora in your motherboard, however, you might prefer to look at the the xeon wolfdale dual core or dunnington sexa core instead. Those WD hard discs look good too. Xeon is another word derived from the greeks, "xenon greek, neuter of xenos, foreign, strange; see xeno" ,however, it doesn't seem to be specifically tied to the greek pantheon as the core (kora) or the itanium (titans) cpus are, meaning it could in theory be a reference to the christian testament of the bible, otherwise known as the greek or new testament. As far as the celeron cpu goes, it is not greek at all but is instead based on the roman word for swiftness or speed, celer or celeritas.

wth?   Is any of this relevent to the thread whatsoever?  :-s

---

### Post by Merps on 2009-01-16
> **High_Speed said:**
> wth? Is any of this relevent to the thread whatsoever? :-s The reason is that he has selected a core i7 cpu and I recommended the core i7 Westmere see my previous post; subsequently I realised that core was the name of a greek godess. The problem is exacerbated when one takes into account that that kore is also known as libera, and therefore associated with liberalism and windows rather than linux. So in essence core cpus would match windows rather than linux.

---

### Post by teaker1s on 2009-01-17
ram wont work on 32bit as limit is 3 or 4 gb max from memory, more and it must be 64 bit

---

### Post by emshains on 2009-01-17
Dudes, amd is beaten hands down atm. 

Intel all the way till amd comes up with something that can kick i7's butt.

NVIDIA FTW!

---

### Post by colokevin on 2009-01-21
PJs, I just built a similar computer. I had no issues whatsoever. Stats below:

Mobo: ASUS P6T Deluxe
CPU: Intel Core i7 920
RAM: CORSAIR XMS3 6GB DDR3 1600
Graphics:ASUS ENG9600GT silent/HTDI/512M
HD: WD Caviar 640GB
PSU: Antec EA500
Case: Antec P182
DVD: Lite-On
Card Reader: Nippon Labs
OS: Ubuntu 8.10 64-bit

> **pjs_flyer said:**
> Ok, here's the proposed spec so far:

Intel i7 920 chip
Asus P6T Deluxe motherboard (although I've read that the ethernet setup might not be straightforward - would the Gigabyte GA-EX58-UD5 be any safer?)
NVidia geforce 9800 GTX graphics card (are there any potential problems between different manufacturers' versions of this card?)
6GB of DDR3 ram
Hauppauge WinTV Nova card
Zalman GT1000 Case
Zalman 750W power supply
Zalman CNPS9700 NT cpu fan
Logitech wireless desktop
Several Western Digital Caviar SATA drives set up in a RAID array
Twin 19" LCD monitors (tbc - any reliable/problem makes/models?)
Blu-ray, dvd, cd etc drive (again tbc - any good/bad?)

Any potential issues here?

Thanks!

---

### Post by pjs_flyer on 2009-01-21
Thanks, that's very reassuring!  Just about to order my bits and pieces...!

---

### Post by Merps on 2009-01-22
In case you were still a core buyer, I just thought I'd add that the Xeon cpu (the wolfdale dual core is cheap and will work in $50-$100 mobos while the dunnington sexa core will cost) are the most used cpu in main frame computers (80%+, with intel cpus in 75% of the top 500 in the world).

---

### Post by pjs_flyer on 2009-02-03
FYI all set up using spec as above, except:
- didn't use a RAID array in the end
- just used a single iiyama 24" monitor rather than twin 19"

Started up first time, ubuntu 8.10 (64 bit) loaded flawlessly, just activated the nvidia drivers to get the full wobbly window effect.  I can't believe how painless it was!!  Will post the full spec in the appropriate place in due course...

Thanks for all the advice!

P.

---

