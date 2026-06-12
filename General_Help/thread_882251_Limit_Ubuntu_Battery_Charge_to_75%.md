---
title: "Limit Ubuntu Battery Charge to 75%"
date: 2008-08-06
forum: General Help
---

### Post by tom66 on 2008-08-06
This may sound strange, but I need to limit Ubuntu's battery charge to 75%. After that I would like the laptop to stop charging and use AC.

The reason I ask this is quite complicated. A little over 6 months ago I purchased a cheap Chinese battery. It worked great for my Dell which had a crap battery. The battery at the time was superior, even to a new Dell battery. Fast forward to now, I have a problem. I think one of the cells in the battery has failed, and is not holding charge. Once the laptop gets to about 82% charge the laptop will just fail, go dark, cut out. No warning whatsoever is given, and the laptop seems to do fine right up until the moment of failure (no malfunctions like crashes, graphical glitches, etc.). Purchasing it was a mistake, but at least it hasn't exploded on me. Yet. 

This is strange and annoying. But the mystery deepens. I have tested the laptop and found that it will run on 9% charge. No problem, and it doesn't cut out instantly. Ubuntu warns me of a low battery though. I have a theory that if I limit the charge to the point where the laptop is not using the failed cell, I can get at least 50-70% of the battery life out of my battery. 

Edit: More strangeness. The laptop seems to go from 9% charge to 100% in less than 10 minutes! Could this indicate incorrect information is being provided by the battery?

So, my question is, can I stop the laptop charging at 75%? My laptop is a Dell Inspiron 1300, running Ubuntu 8.04 Hardy Heron. ACPI works well, if that matters.

---

### Post by tamoneya on 2008-08-07
ive got no clue about the limiting but I wouldnt trust any battery that charges that quickly.  In your case I would probably just bite the bullet and get the dell one.  using that thing is asking for trouble.

---

### Post by eximius1 on 2008-08-07
Get rid of the battery. It's either going to destroy the laptop or burn down your house.

Just go for the dell battery.

---

### Post by a_pirard on 2009-11-14
It is not strange at all to want to limit the charge of a battery to even 60%.  If you read  
[http://en.wikipedia.org/wiki/Lithium-ion_battery#Shelf_life](http://en.wikipedia.org/wiki/Lithium-ion_battery#Shelf_life)
carefully, you will learn that a battery kept in between 40%-60% charged will last 5 times longer than keeping it at 100% most of the time.
This is another way of life than bad => discard.

---

### Post by *g!t5^_)*(H on 2009-12-12
I'm also very interested on this topic, I mostly use my laptop plugged and I don't want to keep my battery out of the computer.

On Windows I've a software from Sony to limit battery charge to 60% (Battery Saver Software) in order to maximize battery live.

It would be great to do the same with Ubuntu.

---

### Post by tgalati4 on 2009-12-12
Over time, a shorted cell will cause extra load on the remaining cells.  The reason the computer shuts down so fast is because the short uses up a lot of current.  Once you exceed the current limit (perhaps 5 to 7 amps) the power circuitry does a safety shutdown to prevent fire.

So in theory, you could get a few weeks of use only charging to 65%, but the risk of burning out your power circuitry on the laptop is great.  That would require a motherboard replacement because when the mosfets fail, they tend to burn holes in the board trying to supply the extra current (shorted battery+charging+CPU).

The non-OEM batteries also save cost by not having a sophisticated protection circuit built in.  Dell, Sony, HP, Apple, have all had battery recalls.  The fix is usually a more complicated ciruit in the battery to shut it down before a fire starts.

A half-charged battery will only give you an hour or so of life anyway, so you might as well run it without the battery until you can get a proper OEM.

If the laptop is a beater (i.e. you don't care) you can make the mods suggested.  Let us know how well it works.

---

### Post by geckosenator on 2009-12-13
I too want to limit my battery max charge.  This is because I am usually plugged in, but my power source sometimes is intermittent, and I need the battery to cover me (Can't just remove the battery)  I want to maximize life and keep the battery at 40% Unless I specifically tell it to charge to more than that.

How can I do this?

---

### Post by Some Penguin on 2009-12-13
If any of you have Thinkpads, this is quite doable.

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

---

