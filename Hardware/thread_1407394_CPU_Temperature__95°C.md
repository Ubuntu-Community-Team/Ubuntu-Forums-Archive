---
title: "CPU Temperature : 95°C"
date: 2010-02-15
forum: Hardware
---

### Post by Gzorg on 2010-02-15
Hi there,

My sensors are displaying 95°C when working fully. It's an Intel Core Duo T2310. I guess there's nothing wrong with it, since it looks like it has a thermal rating of 100°C. Actually, I only managed to find the info for [a similar one]("http://processorfinder.intel.com/details.aspx?sSpec=SL8VR") .

Any way, I still finds that rather hot, and I'd like to lower the temperature to somewhere around 85°C. **Is there a tool that exists to achieve this ?** I always read about monitoring, but I didn't find any info about applying limits.

By the way, when not doing anything, the temperature is around 65°C.

---

### Post by josepaul on 2010-02-15
> **Gzorg said:**
> Hi there,

My sensors are displaying 95°C when working fully. It's an Intel Core Duo T2310. I guess there's nothing wrong with it, since it looks like it has a thermal rating of 100°C. Actually, I only managed to find the info for [a similar one]("http://processorfinder.intel.com/details.aspx?sSpec=SL8VR") .

Any way, I still finds that rather hot, and I'd like to lower the temperature to somewhere around 85°C. **Is there a tool that exists to achieve this ?** I always read about monitoring, but I didn't find any info about applying limits.

By the way, when not doing anything, the temperature is around 65°C.

an idle temperature of 65°C?, this is too hot, are you using a laptop? if not, I suggest you get a new cooler and also clean and reapply the TIM.

---

### Post by akashiraffee on 2010-02-15
How old is the laptop?  You did not say whether the fan was on.  I'm presuming it is, and it probably stays on, right?

If so, most likely the heat sink is clogged and has to be cleaned.

I know this problem applies to some manufacturers more than others (eg, Toshiba), but if you have never taken a laptop apart, here is what happens to them after a few years.

About 1/3 to 1/2 of the interior volume is actually a large metal heat sink.  It extends from the exhaust grill you can see at the back.  That grill is very deep -- perhaps 5-7" -- and extends all the way to where the CPU is, directly over one of the fan intakes on the bottom.  The copper heat sink which the grill is part of becomes a solid surface flush with the metal base of the fan, resting directly on the top of the CPU.

Because the air circulates thru from the bottom and out the back, the dust that you can see from the outside (eg, at the back) is only a tiny fraction of what is collecting around the CPU, 5-7" back from the opening, where the air enters via the fan.  

My laptop got to the point where it would shut down after 20 minutes of use, even when I used an extra external laptop fan and *would pack ice under the chassis* and sometimes on top at the back (which was very warm).  When I took it apart, at the very start of the grill, deep inside directly around the CPU, the entire grill was completely blocked by a 1/2" layer of compressed dust.  Like, when peeled off it remained solid.  It looked like a strip of grey commercial carpeting.  So rather than being surrounded by vents, the CPU was *packed in insulation.*

_There is absolutely no way that using compressed air, a shop vac, ardent prayer, etc, will help you with this._  The only way to deal with it is to take the heat sink right out and clean it.  Probably that means removing the screen, the keyboard, detaching the drives, and pulling the motherboard out the top (ie, everything in the chassis must be removed).  Lots and lots and lots of very tiny screws.  I fortunately found step by step instructions for my make and model online.  Takes hours.  DO NOT attempt to do it if you cannot!!

Also (I learned this the hard way): get some **thermal paste **first because the paste (this is the same white lithium like stuff that goes between the CPU and the fan in a desktop) will be dried up dust.  DO NOT put it back together without fresh paste.

You could also get a repair shop to do this.  If you do, before you ask about that, tell them you want to buy some thermal paste.  If they don't have any, just leave.  The reason I say that is because after taking mine apart and realizing I needed the paste, I went around trying to get some.  Here is what happened in the first three stores:

"We don't have any thermal paste."
"Don't you assemble computers?"
"Yeah, CPU fans all come prepasted now so we don't have to stock any separately."
Kind of shocked by that stupid and pathetic policy.
"Do you clean laptops?"
"Yes."
"Okay, so I just cleaned mine and the paste is totally dry.  What would you do in that case, just put it back together with no paste?"
"No, if the fan is broken we replace the fan, and the new fans come with paste on them, like I said."
"The fan is not broken.  So maybe you would put a new fan in and charge me for that, or you would not bother to put paste in, right?"

Nb, a new laptop fan can be like $75. Well, you won't get much of an answer after that.  One person actually turned away which I took as an honest admission of guilt.

Anyway, charging $50 just for the cleaning would be completely reasonable, even if you are good at it this could easily take 1-2 hours.  Just make sure they actually have some thermal paste in the shop, because they will not bother to look for it afterwards if they didn't bother to have some to start with.  

Nb, you can order paste online for about $5.

Found a pic.  This heat sink is much smaller than mine was, the grill looks only a few inches deep, but as you can see it is the same situation.  This crap needs to be scraped off from the inside.

BTW, after I cleaned it out, the thing ran like new.  Totally cool, never shuts off, the fan rarely even comes on.

[IMG]http://www.insidemylaptop.com/images/clogged-laptop-heatsink.jpg[/IMG]

---

### Post by Cabs21 on 2010-02-15
to [akashiraffee]("http://ubuntuforums.org/member.php?u=968776")

Just as a warning that placing ice or below room temperature air near the fans to cool the computer is a very VERY bad idea.  By lowering the air temperature that low you were basically sucking water directly into the heat sink and CPU.  This could also have been the reason why your dust layers were so tightly packed and held together, because you made a mud type mixture with water and dust while a fan blowing hot air dried the dust quickly so the next layer could be added.

---

### Post by akashiraffee on 2010-02-15
No, the ice was sealed in frozen water bottles and my air is dry, so there is little condensation ;)  I also know other people who turned out to have the same problem, who never resorted to ice.

I did not blow water vapour thru the unit, and in any case this was after the thing was already completely clogged.

Go google. It is a very common (possibly **inevitable**) problem that many people never bother to deal with because you cannot see it at all from outside -- after 3 or 4 years they just figure the thing is old and don't work right.

---

### Post by Cabs21 on 2010-02-15
> **akashiraffee said:**
> No, the ice was sealed in frozen water bottles and my air is dry, so there is little condensation ;)  I also know other people who turned out to have the same problem, who never resorted to ice.

I did not blow water vapour thru the unit, and in any case this was after the thing was already completely clogged.

Go google. It is a very common (possibly **inevitable**) problem that many people never bother to deal with because you cannot see it at all from outside -- after 3 or 4 years they just figure the thing is old and don't work right.


Sorry but if the water bottles had any condensation on them then you were sucking damp air into your computer.  Just cause the ice does not touch the computer or is sealed off does not mean you are not sucking in water.  If the air was cold enough or your computer was close enough to the contained ice that the air did not have time to warm up then you were sucking in damp air.  It might not have been a lot of moisture but it is still there.  At higher temp its no problem but at lower temps the moisture would rather stick to a solid surface instead of a liquid surface like air.  Even if you started the cooling method after the clog happened the moisture would have helped to compress and harden the clog with the mixture of pressure, moisture, and dust to make it worse then before.

---

### Post by akashiraffee on 2010-02-15
> **Cabs21 said:**
> Sorry but if the water bottles [...a lot of irrelevant thoughts...]

That's very interesting, but even if it did contribute slightly to the problem this does not change the fact that:

- the thing was already shutting down due to overheating because it was clogged

[B]- this is INDISPUTABLY a normal, common, acknowledged, widely documented problem with laptop cooling systems.  Just look around on line for the number of "how-tos" dealing with dozens of different common laptops.  
These usually have detailed pictures by [COLOR=Red]professional technicians[/COLOR] such as the one in my first post.[/B]  *

- the ONLY way to solve the problem is to take the computer apart.

Not all of these tens or hundreds of thousands or most likely *millions *of other laptop users tried ice -- which I am not recommending anyway, my point was the thing got really hot.

* notice, a half inch or more of solid, caked dust.  It looks like what you might find in your car's air filter.

---

### Post by Cabs21 on 2010-02-15
Oh i know its a huge problem.  I try to keep my desk as dust free as possible to lower the dust intake into my laptop to help stem off this very issue.  I dont want to have to tear it apart any time soon.

---

### Post by akashiraffee on 2010-02-15
I've taped window screen over the intake vents since then -- it's much finer grain than the plastic grate built into the chassis over the fan.

That will collect a very noticeable amount of dust pretty quickly, can be removed and cleaned easily, and allows plenty of air flow when it is clean.  Did it to my desktop too, there's all kinds of huge holes in desktop cases, including right on the bottom.

---

### Post by Cabs21 on 2010-02-15
you just have to be careful and monitor your CPU temps to make sure that you are getting enough air flow now that you put a filter over it.  You might even want to add a second fan or increase the strength of your current fan to compensate for the loss of flow through the screen.

---

