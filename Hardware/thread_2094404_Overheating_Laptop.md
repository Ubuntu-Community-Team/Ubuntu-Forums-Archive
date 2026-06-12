---
title: "Overheating Laptop"
date: 2012-12-13
forum: Hardware
---

### Post by duncan12 on 2012-12-13
I have an Acer laptop (Aspire 5534). I have a big problem with it - overheating. I use the desktop stats viewer conky to check my computer's core temperature and it usually reports something around the 80°C (176°F) mark. This is rather worrying to me.

It is nearly 3 years old, but I still see no reason for it to overheat.

Sometimes it overheats and "clicks" off - no shutdown. I lose all my work :( (so now I save viciously every 2 minutes) and it won't turn on again for 5 to 10 minutes (as it cools down). I observe that this happens at the 90°C mark. This has been happening ALOT more than it ever did recently, I think because I have started using it to listen to Spotify in the background. However Spotify uses the OGG format and never uses _much_ CPU.

EDIT: I've just checked and Spotify tends to use 20 to 30% CPU (of the measly 1.2GHz). This is a bit, but certainly not enough to justify overheating.

I am not gaming or doing anything CPU-intensive. All I am doing (apart from Spotify) is editing text files with Geany (a lightweight programming text editor) and using Chrome.

I am not blaming Ubuntu. The other day I booted into Windows to check if it overheated there as well, and it did. However, being a Linux user, is there anything I can do to reduce / monitor CPU load?

= = = = =
Mörgæs 2013-12-05:
Using a fresh install of Lubuntu 13.10 everything works fine. Does not get more than 60 °C

---

### Post by ahallubuntu on 2012-12-13
Well-designed laptops do not overheat in normal use, but some are poorly designed, unfortunately, and a cooling pad may be your best bet with them.

In addition, any laptop that is more than a few years old should have the fan and heat sink area cleaned out - dust and hair can accumulate in there and reduce the cooling efficiency a lot.  Some laptops are pretty easy to clean, some are a pain (need to remove the keyboard etc.).  Maybe you will be lucky and yours will be easy to clean.

You also want to make sure the CPU fan is actually WORKING.  I assume you can hear it?  If the fan dies, obviously things will get hotter.

Finally - if you can still boot Windows and there's a BIOS update available from the manufacturer, consider installing that.  Sometimes these updates can improve how/when the fan runs.  You have to be REALLY careful about doing a BIOS update, though - there's always a small chance you could brick the laptop if something goes wrong (shuts off in the middle of the update, etc.)  Never do a BIOS update on battery power.  In your case, I'd do an update when the computer is cold so you won't risk an overheat shutting it down in the middle.

Your BIOS may also have a setting for the fan.  Setting to be always on may make it be annoyingly loud all the time but may reduce overheating issues, too.

---

### Post by duncan12 on 2012-12-13
> **ahallubuntu said:**
> Well-designed laptops do not overheat in normal use, but some are poorly designed, unfortunately, and a cooling pad may be your best bet with them.
True... I do often use it propped up on a piece of wood, and that helps. But I don't expect to have to do that all the time.

> In addition, any laptop that is more than a few years old should have the fan and heat sink area cleaned out - dust and hair can accumulate in there and reduce the cooling efficiency a lot.  Some laptops are pretty easy to clean, some are a pain (need to remove the keyboard etc.).  Maybe you will be lucky and yours will be easy to clean.

In fact, just before I read this I shut it down and pointed a vacuum cleaner at the fan area, on a low setting. That, in addition to using it propped up on a piece of wood, has the temperature lurking around 70°C now, which is an improvement from 80°. However I still don't think it's great. So I'll look at doing a better clean soon.

> You also want to make sure the CPU fan is actually WORKING.  I assume you can hear it?  If the fan dies, obviously things will get hotter.

I can hear it, but it is quite soft - I don't think it's going at the setting it should be at for the temperature it's at.

> Finally - if you can still boot Windows and there's a BIOS update available from the manufacturer, consider installing that.  Sometimes these updates can improve how/when the fan runs.

I don't think there is.. but will check

> Your BIOS may also have a setting for the fan.  Setting to be always on may make it be annoyingly loud all the time but may reduce overheating issues, too.

Rebooting and trying that now.


Thanks for the ideas.

---

### Post by duncan12 on 2012-12-13
I booted into Windows and (after waiting 10 minutes for it to open) Windows Update refused to work. I can't be bothered spending the next 5 hours working out why.

However I went back into the BIOS and in the info screen it said "System BIOS Version" was "1.10". Acer's website [http://www.acer.com.au/ac/en/AU/content/drivers](http://www.acer.com.au/ac/en/AU/content/drivers) says there is a v1.18. However no changelogs there relate to the fan - one says "Modifies 'exit discarding changes' string" which I assume refers to the fact that for the exit discarding changes option you have to press no instead of yes for the "are you sure" message. And there's one regarding Bluetooth. So I don't think there's an update regarding fan etc (nor do I think there would be for some reason).

Is there anything I can do Linux-side to control the fan speed? I've heard of people doing that before.

---

### Post by agillator on 2012-12-13
If you have checked and all the vents are clear, etc., then your problem, especially at that age, is probably that the thermal compound between the cpu and the heat is bad (i.e. old and no longer performing up to par). I don't know you and your capabilities, so I will say my first suggestion would be to take it to a technician and let him find and fix the problem. If I am right, he well replace the thermal compound, charge you $75 and you will have a fully operational computer again. Quite frankly, well worth the price.

If you don't like that option and are willing to run the risks involved in opening your computer, say so and I can tell you how to do it. If you don't know what the risks are, then use the option above, please.

---

### Post by ahallubuntu on 2012-12-13
I think it's highly unlikely that new thermal compound would be required on a laptop this new (only about three years old?).  I sure wouldn't pay $75 for that.  This laptop may not be worth much more than that.

If the CPU is easy to get to, though, it wouldn't hurt to buy some Arctic Silver thermal paste and re-apply it to the heat sink/CPU after carefully cleaning off the old stuff.  It might make a slight difference but I doubt it will make a large difference in this case.

---

### Post by ahallubuntu on 2012-12-13
> **duncan12 said:**
> I went back into the BIOS and in the info screen it said "System BIOS Version" was "1.10". Acer's website [http://www.acer.com.au/ac/en/AU/content/drivers](http://www.acer.com.au/ac/en/AU/content/drivers) says there is a v1.18. However no changelogs there relate to the fan - one says "Modifies 'exit discarding changes' string" which I assume refers to the fact that for the exit discarding changes option you have to press no instead of yes for the "are you sure" message. And there's one regarding Bluetooth. So I don't think there's an update regarding fan etc (nor do I think there would be for some reason).

There appear to be 8 versions newer than the installed BIOS version.  First of all, did you read the release notes for EVERY version?  Second, sometimes enhancements are added that aren't recorded in the release notes.  Personally, after being very careful (download the BIOS first, let it cool down overnight, start up back into Windows and install the BIOS update), I'd update the BIOS.

Did you look in BIOS setup for any options regarding the fan?

---

### Post by duncan12 on 2012-12-13
> **ahallubuntu said:**
> There appear to be 8 versions newer than the installed BIOS version.

I assume you're getting that from the difference between 1.10 and 1.18. However there's only 3 versions listed for download on the website if you actually select Aspire 5534.

Actually, looking at it now, there's 8 rows in the table, but there's only 3 with anything in them. Maybe it's a website glitch that it's not displaying the earlier 5.

So yes, maybe I may as well try updating anyway.

> Did you look in BIOS setup for any options regarding the fan?

Yes I did, there were none.

---

### Post by agillator on 2012-12-14
The reason I mentioned the thermal grease is that it fixed a computer of mine that was showing similar symptoms and was about the same age. Not a recommended procedure for someone who doesn't know one end of a screwdriver from the other. A fairly simple procedure, and much less expensive, for someone who does.

---

