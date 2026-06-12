---
title: "How to test hardware for heat damage on a laptop?"
date: 2016-04-08
forum: Hardware
---

### Post by MibunoOokami on 2016-04-08
Hi all,
 

 Long story short, I bought a used laptop today that was described only as needing a new inverter.
 As it turns out, the laptop won't even turn on because a heat source has been applied to the base causing some slight melting of the plastic base. I've looked inside and can't see or smell any evidence of a short, and it doesn't look like anything else is melted. This makes me think the heat was applied externally and that there may be a tiny glimmer of hope that I may be able to repair this myself without spending too much money.
 

 Is there a way I can test any of the components myself to determine what is damaged/needs replacing?

---

### Post by weatherman2 on 2016-04-08
Motherboards fail.  Could be the motherboard failed due to heat damage from the board itself.  The design may have been poor initially, causing it to get too hot.  Sometimes a component like the CPU or graphics card overheats, because the heat sink was dirty or the fan stopped working.  Or it could have been used in a way that blocked the vents.

Some people will tell you you can fix a laptop motherboard, but I have never tried - it seems far too difficult for the average person unless you already know a specific component has failed.  If you have tried the obvious things like re-seating the RAM, I would write it off as a bad investment and find another laptop.  I assume you would get a refund if you could but it sounds like you are beyond that.

---

### Post by RobGoss on 2016-04-09
Hello and welcome to the forum, If it's more them a inverter as you indicated  I would take it back it might not be worth all the headache you might run into along the way, besides the person that sold it to you was not telling the truth about it so that tells me it might be more going on with that Laptop...

---

### Post by QLee on 2016-04-09
> **MibunoOokami said:**
> 
 Is there a way I can test any of the components myself to determine what is damaged/needs replacing?

The simple answer is, Boot up a live CD and see what works and what doesn't. If it works live then boot it up and run memtest for a few hours, give the system a chance to get hot if it is going to while you are watching it.  See if the cooling fan comes on. And leave it on a non flammable surface with an extinguisher close by.

You've been here for five years and through over 300 posts so presumably you have a live CD, DVD or usb version or can obtain one that could work on that laptop. If the laptop doesn't start smoking or melting anything while running memtest overnight then by then you would have noticed all but possibly some intermittent problems. Even if it works OK initially, old components can fail at any time. I'm sure you know how to research the laptop's components in the forum and minimum requirements. It's possible that the original owner just wasn't satisfied with some cosmetic damage to the case or it could be completely trashed and the lack of power brick might have been so they didn't have to show it boot up. You also know that people here will try to answer any questions that come up. 

A real-life test like this might be all you need. I'd expect that this isn't going to be your only system that you use for day-to-day things.

---

### Post by MibunoOokami on 2016-04-09
Yesterday after trying the laptop, I closed the lid thinking I had turned it off and about half an hour later the fan was going, so there is some life in there.
 

 It didn't even occur to me to try a livecd... The good news is CD drive spins up indicating more life, the bad news is I get no picture even on external monitor, so I'm guessing the graphics/video card is stuffed. I'm going to do a search to see if video cards are interchangeable and see what happens if they are.
 

 I can't return it because the seller added an essential clause which everyone does these days and advertised it AIWI. It was a gamble that would have paid off if it were just the inverter. It may still pay off depending on the price of video cards, assuming that is the (only) problem.

---

### Post by weatherman2 on 2016-04-09
Sounds like a bad motherboard.  I have seen a dozen or two computers do exactly what you describe.  Just because the fan comes on doesn't mean the motherboard is good.  Don't assume that "no video" means a bad graphics card.

If you feel like taking it apart so you can see the motherboard, look for "blown caps."  If you don't know what "blown caps" means, google it.  If you have blown caps, the motherboard is probably bad unless you feel like trying to replace capacitors on a modern motherboard, something I've never wanted to try on something so small and delicate like a modern motherboard.

It might be worth taking it completely apart and putting it back together, just to see if some bad connection was causing your issue.

Also: plugging it into an external monitor just to confirm that no video at all is being displayed might be worth a shot if you have a spare monitor sitting there.

---

### Post by MibunoOokami on 2016-04-10
As mentioned above, I've tried an external monitor already.
 

 I've just finished taking the laptop apart and putting it back together. The areas of suspicion are the CPU, GPU and Wi-Fi card where new thermal paste has been put on top of the old. I also found quite a bit of corrosion on the thin piece of metal on the plastic base near where the USB ports are, one screw that goes on the mother board was also slightly corroded, but nothing else appears damaged. No blown caps either.
 The seller clearly has tried doing things himself. There are screws missing and/or bent, and clip on plastic parts of the bezel have been super glued in place.
 

 I'm going to buy some thermal paste and replace the current stuff to see what happens, while I'm at it I'll try removing more of the corrosion. The odds of this being successful are probably minuscule since corrosion suggests liquid has come in contact with it, and excess thermal paste may have had an adverse effect on heat dispersal but it may be worth a try.

 

 Will post at a later date with results.

---

### Post by weatherman2 on 2016-04-10
I'm sure you are disappointed that this laptop may turn out to be bad, but know that replacing the thermal paste on those chips won't make it work again.  Replacing the thermal past might help if it was working but the chips were getting too hot.  I don't see how it will help in the laptop's current state.  It wouldn't be worth wasting more money on in my opinion.

---

### Post by MibunoOokami on 2016-04-18
I figured it's time to replace the thermal grease on my laptop anyway, so changing it on this computer won't cost anything more than a little bit of time. I did just that and as you said, it made no difference, so I guess the MB is poked.  It's a little disappointing but it is what it is. Caveat emptor.

 Returning to my original question with a slight difference. Is there a way I can test any of the hardware to see if anything can be salvaged?

---

