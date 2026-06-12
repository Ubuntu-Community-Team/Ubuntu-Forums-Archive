---
title: "I think Ubuntu's Decreasing My Battery Life"
date: 2009-09-09
forum: Hardware
---

### Post by rossmc92 on 2009-09-09
I have a Samsung NC10 netbook. At most it's supposed to produce up to 8 and a half to 9 hours of battery life. This was the case with Windows and Fedora. Unfortunately it slips away down to about 3 hours with Ubuntu which is a shame seeing as it's what I consider to be the perfect OS. I don't want to switch to another distro but I also don't want to loose so much battery life. Any help available?

---

### Post by Madonnas BoyToy on 2009-09-10
I have no advice to offer, and hope that you don't get mad because of that fact, but I had actually found that my battery life has been extended since switching from Windows XP.  
I have an HP Mini, and the battery life wasn't much to begin with, only about 1.5 hours, but now I get 2.5 hours.

Anyway, best of luck to you in resolving your issue.

---

### Post by Cklein on 2009-09-16
I have the same battery problem with the Samsung nc10. I've tried a lot of stuff, powertop and so on, and the battery only lasts 4:30h which is ok but not as good as in windows. Even disabling wireless (being connected through ethernet cable) doesn't give more battery. Ummm...

---

### Post by sergiom99 on 2009-09-16
Which flavor of Ubuntu are you guys using? Did you try the Ubuntu Netbook Remix?

---

### Post by Fatalrewind on 2009-09-16
Hello

Im using a dell mini 9 and i have found that since switching to
NBR 9.10 the battery life has become much lower 1-2 hours max ,and theres much more heat, and to top it all off i find that when it gets hot everything slows down to a crawl ,this may well be the dell mini not functioning properly but since using NBR 9.10 i have seen a large performance boost on the system but at the same time low battery and high temps.

Nothing has been changed in the bios and i dont overclock but it
almost feels like 9.10 is overclocking the mini9 ?

It has been filed for report.

Paddy

---

### Post by Whiffle on 2009-09-16
Alot of power saving features are disabled by default on ubuntu.  Here's a thread about getting some of them setup:

[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

I don't know if anybody has written a comprehensive howto yet, but it would be nice.

---

### Post by typiCAL_ on 2009-09-17
> **Whiffle said:**
> Alot of power saving features are disabled by default on ubuntu.  Here's a thread about getting some of them setup:

[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

I don't know if anybody has written a comprehensive howto yet, but it would be nice.

I had also noticed a decrease in battery life on my Satellite A500 using Jaunty.  On a full charge I can go about 1hr 45m compared to my usual 2hr 30m in Vista (eck).

Although a couple of the ideas in that thread seem to be giving a little more juice to battery life, so thanks!! :)

---

### Post by TpyKv on 2009-09-17
have you installed powertop?

sudo apt-get update
then
sudo apt-get install powertop

?

This gave me the option to do something with hard drive access times, by enabling it, my battery life has gone through the roof... but then again this is a 400GB HD in an acer aspire one... 

give it a go!

---

### Post by Cklein on 2009-09-17
I'm running UNR 9.04 and have  already powertop. It only complains about usb autosuspend and CPU governor...

Even activating both the power used and the number of interruptions are high, so it doesn't change a lot.

I haven't tried anything about the hard disk. I'll try and tell the results.

---

### Post by kestal on 2009-09-17
First off, 9.10 isn't even out yet. This is bound to be a resource hog until its fine-tuned, especially with some of the problems that have been up and about.

As much as I hate to say this... Have you fully tried to drain your battery yet in Ubuntu? (rather than looking at the time left?)

I bring it up because I had a problem with my old laptop (on Ibex and Jaunty). What used to happen is that when it shows a certain percentage (and time left), it was often inaccurate.

I remember one time after I got it to 0% battery that I would still be able to use it for over an hour. This could be unrelated, though I figured I'd mention.

I remember that once I drained it completely (waiting an hour past 0%), my battery capacity increased back and I had a long battery life again (I had to do this a few times to correct it). My battery could have just been damaged though, or something.

---

### Post by Cklein on 2009-09-18
Hi,

   I've just tried to fully drain the battery and it gives a few more minutes than what the message said, but not that much, so still with a battery that last less time in UNR than in windows xp.
   BTW, has anyone tried to actually measure the time the battery last on xp and ubuntu with the samsung nc10?

---

### Post by Whiffle on 2009-09-18
My laptop has a pretty accurate gauge of wattage.  Windows pulls 10-11 watts, Ubuntu seems to hang out around 13-14, after some tweaking.  Someday when I have time, I'll try to get that lower...

---

### Post by BlueerSkies on 2009-09-18
Bismillaah.   Peace, all.  What type battery is being used in these scenario's?  The lion type that my pc use's should be allowed to run down pretty much totally, before recharging, especially when they're new, as this will increase battery life, and prolong the charge.  I have noticed an increase in use when running ubuntu on my notebook with battery power.  Normal use with win xp is about two and a half hours. Ubuntu uses much less battery power than win xp. But I've had a little trouble charging on ubuntu as it will not reach 100% charge.

---

### Post by Whiffle on 2009-09-18
> **BlueerSkies said:**
> Bismillaah.   Peace, all.  What type battery is being used in these scenario's?  The lion type that my pc use's should be allowed to run down pretty much totally, before recharging, especially when they're new, as this will increase battery life, and prolong the charge.  


Not correct.

[quote=http://www.batteryuniversity.com/parttwo-34.htm]
Simple Guidelines
Avoid frequent full discharges because this puts additional strain on the battery. Several partial discharges with frequent recharges are better for lithium-ion than one deep one. Recharging a partially charged lithium-ion does not cause harm because there is no memory. (In this respect, lithium-ion differs from nickel-based batteries.) Short battery life in a laptop is mainly cause by heat rather than charge / discharge patterns.

Batteries with fuel gauge (laptops) should be calibrated by applying a deliberate full discharge once every 30 charges. Running the pack down in the equipment does this. If ignored, the fuel gauge will become increasingly less accurate and in some cases cut off the device prematurely. 

Keep the lithium-ion battery cool. Avoid a hot car. For prolonged storage, keep the battery at a 40% charge level. 

Consider removing the battery from a laptop when running on fixed power. (Some laptop manufacturers are concerned about dust and moisture accumulating inside the battery casing.)

Avoid purchasing spare lithium-ion batteries for later use. Observe manufacturing dates. Do not buy old stock, even if sold at clearance prices. 

If you have a spare lithium-ion battery, use one to the fullest and keep the other cool by placing it in the refrigerator. Do not freeze the battery. For best results, store the battery at 40% state-of-charge.
[/quote]

---

### Post by BlueerSkies on 2009-09-19
Bismillaah.   Peace.  I would guess that everyone has had their own experience's with batteries. I've tried refrigerating dry cell batteries of every type. They seem to lose some of the initial charge after a while.  I would not recommend placing a pc's battery in the fridge due to moisture collection.  I have had my present li-on battery since 2003, and as expected it is growing weaker. But I've always allowed it to discharge near totally, each time before recharging.  But always do whats best for* your* battery, I say.  Do what works for you!

---

