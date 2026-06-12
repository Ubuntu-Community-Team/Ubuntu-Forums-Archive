---
title: "overheating"
date: 2014-08-05
forum: Hardware
---

### Post by mastablasta on 2014-08-05
So we tried to play Enemy Territory. Computer is Dual core Celeron 3300 with old ATi Radeon 9600 (opensource drivers). Game played fine but then suddenly got stuck and crashed completely. i had to do a hard reset (couldn't get into console and REISUB didn't work). Upon reboot the desktop set resolution as it was set in game. this is totally wrong! but lets skip this part for now. It crashed a couple more times until it reboot and turned itself off before or after getting to desktop. I thought GPU is overheating so i cleaned the PC inside a bit..

i wanted to check the logs but i couldn't boot. so i went into BIOS and checked some settings and sure enough i saw a CPU temp rising until the computer shut itself down. would applying new thermal paste solve this or do i need a new cooler/fan as well? the CPU has a classic cooler and fan for these intel CPU.

---

### Post by mörgæs on 2014-08-05
Exactly which parts did you clean? Is the radiator within the cooling unit completely free from dust and does the fan rotate as expected?

---

### Post by Mike_Walsh on 2014-08-05
Hi, mastablasta.

You're doing exactly what I had to do when I took posession of my current system, 8 months ago.

It had nine years worth of dust-bunnies and assorted crap inside it.....and the CPU cooler was absolutely clogged solid.

Hardly surprising, since my brother-in-law is constantly rebuilding their house, and there was brick dust and ALL sorts in there.

I used an old, very soft 1/2 inch paintbrush to remove the worst of the dust from the cooler (after removing the fan), and then finished by using short bursts from a can of compressed air (but ONLY short bursts; longer bursts can lead to a slight build-up of condensation...not a good mixture with electronics). This usually removes any more stubborn stuff from the bottom of the cooler, closest to the thermal contact with the CPU. I'm guessing you obviously know NOT to use a vacuum cleaner; too much danger of static build-up...

I find AMDs seem to run a fair bit cooler than Intels anyway, but mine rarely gets above 35-38C even during the summer.....and I repeat this regularly every couple of months. (We live in a house with hot-air heating, which is the most perfect way of blowing dust right round the house..!)

If it was me, I would replace the standard Intel cooler with something a little bit more substantial; the Intel coolers are marginal in their effectiveness at the best of times. And if you do that, you'll need to replace the thermal paste anyway. Go for Arctic Silver; it's a bit more pricy, but it's worth the extra outlay.

Regards,

Mike.

BTW; what Intel are you running? If I know that, I can look you out some recommendations. This is one area I DO know something about, having changed quite a few fan/cooler combinations over the years.

---

### Post by mastablasta on 2014-08-05
Yay I found a good Akasa paste for 3 EUR at local computer shop. seems to have good reviews on amazon and local webshop.

> **mörgæs said:**
> Exactly which parts did you clean? Is the radiator within the cooling unit completely free from dust and does the fan rotate as expected?

I took it off. it seemed like it wasn't even attached well. one or two of the holding pins was moving suspiciously. hmm...

> **Mike_Walsh said:**
> 
I used an old, very soft 1/2 inch paintbrush to remove the worst of the dust from the cooler (after removing the fan), and then finished by using short bursts from a can of compressed air (but ONLY short bursts; longer bursts can lead to a slight build-up of condensation...not a good mixture with electronics). This usually removes any more stubborn stuff from the bottom of the cooler, closest to the thermal contact with the CPU. I'm guessing you obviously know NOT to use a vacuum cleaner; too much danger of static build-up....

I used vacuum cleaner :P but in short bursts. I know about the static buildup but that would happen if you held there for a certain period of time. and I took off the whole cooler, so no electronics there and did a full vacuum of it...
> 
I find AMDs seem to run a fair bit cooler than Intels anyway, but mine rarely gets above 35-38C even during the summer.....and I repeat this regularly every couple of months. (We live in a house with hot-air heating, which is the most perfect way of blowing dust right round the house..!)

If it was me, I would replace the standard Intel cooler with something a little bit more substantial; the Intel coolers are marginal in their effectiveness at the best of times. And if you do that, you'll need to replace the thermal paste anyway. Go for Arctic Silver; it's a bit more pricy, but it's worth the extra outlay.

Regards,

Mike.

BTW; what Intel are you running? If I know that, I can look you out some recommendations. This is one area I DO know something about, having changed quite a few fan/cooler combinations over the years.

quite possible that they run cooler. I only took this one because I found a motherboard a the time that could use all of the old stuff I inherited from my grandfather (AGP card, DDR ram, IDE hard drive). it was cheap and the CPU was the cheapest I could find and that could fit in it. we were moving, money was even tighter than now and we needed another PC so we can both work at the same time.

this is how the cooler for 775 socket looks like: [https://www.google.com/search?q=intel+775+cooler&rls=com.microsoft:sl:IE-Address&tbm=isch&tbo=u&source=univ&sa=X&ei=-ODgU7emE8m9Oaa3gZgO&ved=0CCIQsAQ&biw=1680&bih=925](https://www.google.com/search?q=intel+775+cooler&rls=com.microsoft:sl:IE-Address&tbm=isch&tbo=u&source=univ&sa=X&ei=-ODgU7emE8m9Oaa3gZgO&ved=0CCIQsAQ&biw=1680&bih=925)

i have Celeron E3300 dual core I think and standard cooler. I was checking out the one from Akasa. so if this one doesn't work with new paste I will change it with this Akasa cooler. if that one doesn't work as well then I will throw (or give) everything away and get something modern.

well to be hones I never checked the temps in this PC I never felt the need. now I saw it rising a 1 degree Celsius per second in BIOS (doing nothing basically...). 

the fans seem to be running well. they increased from 800RPM to 2000RPM (according to BIOS) to try and cool it off but didn't help. there is a BIOS feature "quiet fans" - I will need to check the board manual to see what does this do. maybe it's preventing faster spin...

anyway cleaning and applying pasta is on today's schedule. fingers crossed it will go well. we'll see if this solves it all or not. at least I am hoping I can get to system logs.

---

### Post by Mike_Walsh on 2014-08-05
Hi, mastablasta.

Snap! I know ALL about budgets, trust me; why do you think I'M running such an old system?

And there's also the fact that, like morgaes, I too like to keep older hardware running. Ubuntu allows me to do that; I absolutely refuse to pay you-know-who one single penny more for an O/S that I can't make behave the way that I want it to!

(And it's my personal belief that if they had their way, we'd all be junking hardware every 18 months or so, and constantly buying brand-new. Ya gotta hand it to them; Americans DO worship the dollar! :D:D)

Back to your system. Loose & moving pins are never a good sign. Are the attachment pins/clamps in good condition? I mean, not obviously cracked and/or broken? If so, then there's hope..!

Out of curiosity, does your cooler have the solid copper base, or the composite ally/copper base? The composite ones, strangely enough, actually seem to work better...

Regards, 

Mike.

---

### Post by Mike_Walsh on 2014-08-05
Hi, mastablasta.

Snap! I know ALL about budgets, trust me; why do you think I'M running such an old system?

And there's also the fact that, like morgaes, I too like to keep older hardware running. Ubuntu allows me to do that; I absolutely refuse to pay you-know-who one single penny more for an O/S that I can't make behave the way that I want it to!

(And it's my personal belief that if they had their way, we'd all be junking hardware every 18 months or so, and constantly buying brand-new. Ya gotta hand it to them; Americans DO worship the dollar! :D:D)

Back to your system. Loose & moving pins are never a good sign. Are the attachment pins/clamps in good condition? I mean, not obviously cracked and/or broken? If so, then there's hope..!

Out of curiosity, does your cooler have the solid copper base, or the composite ally/copper base? The composite ones, strangely enough, actually seem to work better...

Regards, 

Mike.

---

### Post by mastablasta on 2014-08-05
cooler doesn't have copper base. i applied paste (the small drop in middle method) and attached the cooler. all seemed fine for a short while then temp started rising to 74C where it stayed. in BIOS!!!! and fan go to 2400 rpm and stay there...

booting to desktop sensors is showing 99C

now what? looks like cooler, huh?

edit: i checked hwo the paste was applied an dit turns out that teh drop didn't really spread much around. so i reapplied the paste and this time i spread it arround a bit and it started at 40 C then slowly climbed to what is now 66 C (150F) on idle in BIOS - cpu fan on 2500 RPM. it's been on 64 for a while and then climbed a bit more.seem like it will stay on 65 C measured on idle in BIOS. box open.

EDIT2: i've boot into desktop  (Kubutnu) and ran sensors-detect and then sensors and it shows 57 C. still a bit high but... lower than on idle?!

---

### Post by Mike_Walsh on 2014-08-05
Hi, mastablasta.

Hmm. Sounds like the base has warped. As I understand it, it's a known problem with the Intel-supplied coolers; it's why so many people replace them when they get overheating problems. They charge you a small fortune for the chip, and then supply the cheapest cooler they can get away with! 66 is fairly high. It will run like that, but it's uncomfortably close to the thermal limit for MY liking!

You're better on the software side side of things than I am, that's quite clear. Sounds like you can do tricks with the system that would never even occur to me!

I've ALWAYS been short on funds, all my life.....that's why my system was such a godsend. My sister had it for close on 9 years, and hardly used it during that period, so it's almost like a new one. The hard drive, although IDE/PATA, has got years of life in it yet; according to the S.M.A.R.T data, it's barely done 2000 hrs, so I think it'll last me a few years yet..! Just got to hope that Ubuntu's kernel upgrades keep on supporting the older hardware...

I have a friend who operates a CNC lathe at work, and he's an amateur engineer in his spare time.....has a good-quality lathe in his hobby-room at home. If I get a cooler with a warped base, I get him to skim it for me...makes an ace job, too.

Not everybody has that option, though!

Sounds like you'd be just as well to try the other cooler you've got, yes. Try a slightly larger blob of thermal paste than you used; some people tend to err on the side of caution, and often don't use enough. Other people use too much; it's quite a balancing act to get it just right, and like many things, it only comes with experience. I used too much the first time I tried it, and the stuff went everywhere..!

Let me know how you get on.

Regards, 

Mike.

BTW: Having said that, try removing the cooler again, clean the paste off the cooler and heat-spreader, and try re-applying a slightly larger blob. See how that goes, and let me know what happens, please.

---

### Post by weatherman2 on 2014-08-05
I have a desktop machine with this same CPU, an Intel Celeron E3300.  It uses the standard cooler.  I have not had any issues with it after a few years of use.  I don't play games, though, and I have not overclocked mine.  It runs fairly cool.  Keep in mind the temperature will be hotter in BIOS Setup (when you are looking at the PC Health Status temperature or whatever) than when you have loaded an operating system, and Intel Speed Step has slowed the CPU down at idle.  Even then, 57C is far too hot.  I think mine idles at about 37C with Ubuntu loaded.

I suppose it's possible that if the CPU got really, really hot - due to poor case ventilation, prolonged high CPU use, fan dirty, etc. - that it could warp the cooler.  But you should see it upon looking at the cooler when removed.

When you snap the heat sink/fan back into the motherboard, you need to be certain it is clipped on securely - all four sides.  Make sure there is no "wiggle" on any of the four corners.  I took off some socket 775 coolers recently and had a difficult time at first putting them back on correctly.  To remove the cooler, you rotate each fastener counter clockwise (following the arrows direction), then pull up.  When the cooler is removed, re-rotate all four clockwise and also pull all four of them all the way up.  Make sure all four are up.  Then snap each back in.

If the cooler is messed up, I say buy another cheap one - this CPU should not really get that hot with proper ventilation and you can probably get a brand new replacement for about $5 USD on eBay.  On an old machine like this, it's not worth spending much more.

---

### Post by mastablasta on 2014-08-06
I will recheck the clips. I suspect it is not pressing enough on the CPU.  

I didn't notice that it would be warped. but the paste should be all over (a thin layer) and it looked like it didn't even squeeze it properly.

as for replacement they have this Akasa for 27 EUR: [http://xtreview.com/images/AK-968%20X4.jpg](http://xtreview.com/images/AK-968%20X4.jpg)  - which might be an overkill
(again similar Zalman model for 25 EUR)

this kind Akasa (copper on bottom) for 14 EUR: [http://www.akasa.com.tw/img/product/common/feature/00/AK-CCE-7106HP_f00.png](http://www.akasa.com.tw/img/product/common/feature/00/AK-CCE-7106HP_f00.png)
or they also have some Zalman (aluminium) for about 8 EUR similar model.

eventhough it would seem like it is working but not good enough. I would also expect idle working temp at 30-40 C, so I really have to recheck the pins. is it possible that the pin is broken and doesn't fit well into the hole? I know one gave me trouble to push it in. but when I tried moving the CPU it seemed like it was fastened well inside on all sides. also it doesn't seem like the cooler can get any closer to the CPU.

I wonder why they make these cooler grabbers so ridiculous (the AMD one is even weirder IMO) ? is it due to the temperature changes? 


I don't have another fan  in this box. I might add it. I didn't think it was necessary.

---

### Post by weatherman2 on 2014-08-06
As I said above, make sure you can't "wiggle" the heat sink at all.  When I was messing with my coolers recently, I found a couple of times that even though I thought I'd pushed all of them in, one pin wasn't completely in and I could pull the cooler up ("wiggle it") slightly.  If I didn't pull it, it would be "as close to the cpu as possible" but still not tight.  It needs to be tight on all four sides.  I would pull it out in the way I described above, rotate all four of them in the opposite direction of the arrows, pull all four pins up as far as they go, and make sure, on the bottom, that the plastic around the pins isn't cracked or something.  Then try again.

The original cooler had a thin layer of thermal paste on it.  It has probably burned off now.  You don't necessarily need a lot of thermal paste - a thin layer is all that is required, don't gob too much on.  I assume you made sure the CPU and the bottom of the heat sink were cleaned before you put new paste on.  If so, that should be adequate.  The amount of paste is not going to make as much difference in temperature as you are seeing because of a little thermal paste - it would matter more if you are running a very hot CPU or overclocking it or something, not the E3300 under normal conditions.

The E3300 is old now and wasn't fast in the first place.  I paid only $30 USD for it, the cooler, and the motherboard(!) for mine, a few years ago, on clearance.  So the prices you quote now for a new cooler seem far too expensive to me for an old, slow CPU - I would invest that money toward a much newer CPU instead.  I see cheaper coolers on eBay in USD, not sure what prices would be in Europe (you mention Euros, I assume that's where you are).

An extra case fan in this case isn't going to reduce your extreme temperatures, but if you have a lot of heat in there from other sources (video card, etc.) you might want one.

---

### Post by mastablasta on 2014-08-06
yeah we have extra expencive tech stuff for some reason. most prices woudl go like this - take the USD - pretend they are EUR and then add 30% to that. :)

anyway checked the pins an dsure enough not one but two were not full in eventhoguh i couldn't move the cooler. so after pressing really hard (hmm could it be that the cooler is really bent) i got the pins in. and the temp is now more normal though to me still a bit high. it is 41-42 C on idle and with a bit of websurgin, file transferign it went up to 48 max, but mostly it is at 42-44 C (using psensor with lm_sensors to monitor the temps now). i htink it might be less if i didn't make so many corrections. possible bubbles that could form in the paste are actualyl warmin git up instead of cooling off.

I am thinking about getting "external" case fan when i have the time to deal with that. i will leave it at this temp for now. if it continues to make issues i will get a new cooler. if that doesn't help i will throw away the mobo and get a new CPU, RAm and motherboard. but that costs at leasdt 150 EUR min. so i would rather avoid that cost if possible.

---

### Post by weatherman2 on 2014-08-06
Sounds much better.  Do consider adding a case fan of some sort - if you don't have one at all now that will help a lot when the CPU isn't idling and is generating a lot of heat!

---

### Post by Mike_Walsh on 2014-08-07
Hi, mastablasta.

Couldn't get on here yesterday. Our broadband provider's Parental Control Filters (which we didn't even HAVE) threw a BIG wobbly yesterday, and blocked everybody on the network from accessing anything at all! Technology, eh? Marvellous WHEN it works, but when it DOESN'T... *Sheesh*

Glad to hear your new temps. They do sound MUCH more reasonable; anything under 50c when working hard is quite acceptable. Glad to hear you're using psensor, too; I've been using it for the last coupla months...ever since I found it, actually!

I used to use HWMonitor in Windows, but you couldn't leave it up all the time, 'cos of the window size. I like psensor, because it runs IN the taskbar...so you have a continuous readout. It's quite an education, watching what the temps do when you're running CPU-intensive stuff, isn't it?

Regards,

Mike.

---

