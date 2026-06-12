---
title: "Repeated shutdown"
date: 2015-02-22
forum: Hardware
---

### Post by newholm1 on 2015-02-22
Hi there. I have been using my homebuilt system based on the Gigabyte HA55M-USB3 for five years now. Yesterday I took it apart as I sometimes do to remove dust and clean the inside. I took precautions such as using an antistatic mat, and as far as I could tell, no harm came to any of the components. However, when I put it back together again, it refused to boot properly and has done since. What happens is the computer starts as normal, but after a few seconds the power cuts. The amount of time before this happens varies, but nothing ever appears on the screen. The fans are functional, but cut along with the rest of the power. My external hard drive comes on when I switch the rocker switch at the back, and continues when the rest of the power cuts, so I know it isn't the power supply. The light on the front power switch comes on when pressed, but switches off when the power cuts. The Hard Drive indicator light for the internal hard drive does not light. Is this problem familiar to anyone? Short of replacing components, it is hard to know where to start.

---

### Post by weatherman2 on 2015-02-22
One obvious place to start that bears repeating: re-check all of your connections from the power supply.  Unplug and re-plug everything in.

I'd also unplug EVERYTHING not required to get the computer running: all add-in cards, external drives, internal drives, everything.  Just enough so the board should power on and POST.

It COULD be the power supply (unlikely but possible).  Power supplies can fail in strange ways.  Don't assume the power supply will be either all or nothing.  It could have enough power to power up some things but the computer might shut down immediately if there isn't enough power to keep everything going.

Motherboards can and do fail, too.  Just because you were careful doesn't mean the motherboard wasn't on the verge of failing prior to your cleaning, and whatever you did kind of disturbed it enough to push it over the edge.

---

### Post by newholm1 on 2015-02-22
What's the minimum I should need for POST? I have tried a few combos (right down to starting up without even the processor) and the power still cuts - in fact it seems to cut out after the most time when everything is connected. At no point does it go to the POST screen. I figured it would only go there if everything was functioning correctly.

---

### Post by weatherman2 on 2015-02-22
You should be able to POST with RAM and CPU and video (assume motherboard has integrated video).

Silly question: you plugged in both the 24 pin main power and the 4-pin (or 8 pin) CPU power, right?

It's a shame you don't have a spare power supply to try.

Are there any blown capacitors on the motherboard?  (unless they are "solid capacitors").

---

### Post by newholm1 on 2015-02-23
Both the 24 and 8 pin power cables are plugged in, yes. Not sure about blown capacitors - how would I tell? Everything looks normal to me. Definitely can't POST. Had another look, I think it must be the power supply as the time before power cuts is erratic, very suggestive of a dodgy power connection. My power pack is the Antec Earthwatts EA500D, which seems to be discontinued. If I need a new one, are they mainly interchangeable? Is the wattage the only consideration I need to take into account?

---

### Post by tgalati4 on 2015-02-23
Yes, just match the wattage and you should be OK.  It's strange that cleaning a machine would cause a power supply to act up.  Perhaps there is too much dirt inside the power supply.  Unplug it.  Open it up.  Take a screwdriver and carefully short the pins under the large capacitors.  You might see a large spark.  That is OK.  Now blow some compressed air and describe how dirty it is.  Reassemble and test.

---

### Post by weatherman2 on 2015-02-23
I would be careful digging around in a power supply with a screwdriver.  Even if unpulgged, those caps can still have a bit of charge and give you quite a shock.

Generic PC power supplies are somewhat interchangeable, as long as it was in a standard case.  I would get an efficient 80+ power supply now for sure - sometimes they cost a little more, sometimes you can find good deals on them on sale.  The old inefficient power supplies could leak 10 watts or more vs. the newer efficient models.  Even if turned off those old ones could draw 4-5 watts.  Over five years, that adds up in extra power.

Yes, match the wattage to the old one.  A little higher wattage is fine but of no real benefit if the old one was adequate.  A lower wattage may also work fine depending on your hardware.  More than 500 watts is probably way too much unless you have a separate video card or a lot of hard drives or something.

---

### Post by newholm1 on 2015-02-25
I have had a good go dedusting the power supply, to no avail. I then tried a new power supply (600 watts rather than 500, as recommended in the shop) but still no luck. The power continued to fail, but it seemed to take a little longer to fail. This may be coincidence. Any idea what I should try next?

---

### Post by tgalati4 on 2015-02-25
Put your finger on the exposed chips on the motherboard while booting.  Do any get really, really hot?  If so, then you have a chip failure, which will draw extra power until the power supply shuts down as a protection.  So it's possible that your old power supply is working correctly.  The new power supply would take longer to shut down because it can handle more power before tripping.

Are there any bulging or leaking capacitors on the motherboard?  The other issue is the heat sink may need new heat paste on the CPU and or GPU.  5 years is about the time that the paste dries out and causes the CPU to get hot and cause a thermal shutdown.

---

### Post by weatherman2 on 2015-02-25
I'd guess bad motherboard.  It happens, even when you don't try to clean your motherboard.  

You could remove the motherboard entirely from the case and blow out any remaining dust.  Sometimes a screw or something could short out something on the motherboard.

CPU thermal paste is something you try if the CPU is getting a little too hot over time, but it isn't required (at all) for the heat sink to do its basic job.  It helps make a good seal or connection between the heat sink to the CPU, but even with burned or inadequate thermal paste the CPU won't overheat that quickly as long as the heat sink is firmly, correctly attached.  

But if the heat sink isn't correctly or firmly attached, you could get overheating in a few seconds and a quick shutdown.  You can try removing the CPU heat sink and re-seating it, and if you have thermal paste now it wouldn't hurt to clean the surfaces and re-apply new paste, but I wouldn't go out and buy thermal paste just to try to fix this problem - unlikely to help it.

---

