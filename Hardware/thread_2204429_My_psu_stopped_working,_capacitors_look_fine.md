---
title: "My psu stopped working, capacitors look fine"
date: 2014-02-08
forum: Hardware
---

### Post by J_Me on 2014-02-08
Please, for anyone reading this take note that power supplies carry a very large charge WHICH CAN KILL even if it's not plugged in to the mains. Anyway my psu just packed up, I've tested the green cable and it puts out 5 volts but jumping the purple cable wont power up the 12v or 5v they remain dead and so is the fan. The capacitors look fine no bulging. Is there anything else I could try. Thanks

---

### Post by tgalati4 on 2014-02-09
There are some troubleshooting guides on the web, but you will have to search for them.  If the label says "Bestec" then you can confidently throw it in the trash.

The problem with power supplies is when they fail, they tend to take out several components at once.  If a MOSFET blew, you would smell it.  Sometimes the varistors blow--they are the pancake-shaped resistors that short when too much voltage tries to pass--what is commonly called surge protection.  Sometimes the turn-on circuitry fails.  That gives you 5VDC trickle power, but won't turn the PSU on.  I've repaired a few of these by simply changing the switching transistor.  This might be the case for your problem.

Capacitors can short and leak without bulging.  The only way to tell is to pull out the large ones and test them as individual components.  You would need to measure basic capacitance and ESR.  Of course measuring the voltage at various test points around the power supply can help isolate the problem.

---

### Post by Bucky Ball on 2014-02-09
> **tgalati4 said:**
>  If the label says "Bestec" then you can confidently throw it in the trash.

The problem with power supplies is when they fail, they tend to take out several components at once.

If it is a no-name generic silver box you should have thrown it in the trash and replaced when you bought the PC! Those things can kill as well without even taking them apart, components and humans when they blow and set the curtains alight which then burns down the house. Not to mention the fact they are less than 70% efficient generally. Shouldn't be legal, IMHO.

Always stick to name brands with plenty of safety switches, and 80+ efficiency should be a starting point. There are lots of units with those specs about nowadays. ;)

---

### Post by QIII on 2014-02-09
Even the good ones are widow-makers if you open the case.  Those capacitors can hold a charge for a very long time.

If you are not an electrician, have no training in repairing or refurbishing that sort of thing or have any desire to see your grand-children get married, don't bother with anything more than a trip to the trash can with it.

Saving a few tens of dollars is not worth the potential expense to your family for having you planted.

---

### Post by J_Me on 2014-02-09
@tgalati4 Thanks a lot I think it maybe a MOSFET. The psu had a acrid smell and there's scorching directly underneath the MOSFET on the circuit board.............@Bucky Ball, @QIII Good advice!..............The psu was a cheap piece of CIT(that's the brand name, seems fitting). Thanks again

---

### Post by zajc3w on 2014-02-09
only problem with cheap PSU is using cheap 85 C caps and sometimes no thermal paste under semis. I'm running CIT psu at full load for 8 years. But after a month of use  i changed all caps and i put decent thermal pate on semi's. Next cap change soon 10 years is cap's max lifetime in such conditions.

---

### Post by tgalati4 on 2014-02-09
That's pronounced *Chheeet*.  The C is soft.  Yes, you can change the MOSFET ($3 to $5 for good ones), but again when a MOSFET (metal oxide semiconductor* flame emitting transistor*) blows it tends to take out a few other things like caps, diodes, resistors and voltage regulators.  I have rebuilt a few PSU's in a manner *zajc3w* has suggested, but the time and expense involved, I would just get a decent retail PSU that fits your chassis and has a decent Power Factor (80 to 98% efficiency).

Let us know how this saga turns out.

---

### Post by J_Me on 2014-02-10
@zajc3w thanks for the information.
@tgalati4> That's pronounced Chheeet:p:p:p
I had a closer look at how to go about repairing this and it's not easy, also as you say other parts have probably blown as well I think I'll just buy a new one. But will keep the CIT as a repair job for sometime in the future.
Thanks for all the help anyway

---

### Post by Bucky Ball on 2014-02-10
All good. Please mark thread as solved. ;)

---

### Post by tgalati4 on 2014-02-10
Many times a weak solder joint and the high heat that MOSFETs put out will cause a copper trace to burn up and the power supply to fail.  You can sometimes repair this by simply soldering wire farther back on the trace to the MOSFET leg.  Be sure to short the big caps with a long screwdriver and wear a rubber glove on your right hand as a precaution.  Also, place your left hand behind your back while you are doing this so that you don't create a path across your heart.  That would be bad.  You can whistle while doing this, because it does look silly.

A typical, cheap power supply is rated to 275 watts, so your caps will hold about 100VDC for 120VAC and 210VDC for 240VAC.  But you are only looking at 2.75 or 0.76 amps for a spark.  That is enough to disrupt a heart rhythm, so precautions must be taken.

---

