---
title: "Inspiron E1505/6400 thermal paste removal  Heat issues"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by tgm4883 on 2007-07-19
Please move if this should go elsewhere.

I have changed my processor from a Core Duo to a Core 2 Duo, and in doing so, have removed the crappy thermal paste dell uses and added some Artic Silver 5.  Both processors are 1.66Ghz, but now my system hangs around +50C where it used to idle around 38C.  Of course this lead me to wonder about my AS5 job, so I did it again with no benefit.  

has anyone had this problem or tried replacing their thermal paste on this system?  I'm starting to worry about the clearance between the CPU and Heatsink.

---

### Post by w4ett on 2007-07-19
The only thing I can recommend is that the layer of Arctic Silver ( I use it myself)  needs to be extremely thin.  Did you use denatured alcohol to clean the HSF and processor prior to reassembly?  (just asking the obvious troubleshooting questions)....HSF running at full RPM?

---

### Post by tgm4883 on 2007-07-19
> **w4ett said:**
> The only thing I can recommend is that the layer of Arctic Silver ( I use it myself)  needs to be extremely thin.  Did you use denatured alcohol to clean the HSF and processor prior to reassembly?  (just asking the obvious troubleshooting questions)....HSF running at full RPM?

Yea its extremely thin.  Denatured alcohol?  Hadn't heard of that, I just use some walgreens 91%.  The fan is running as it normally does, but not full speed (although it didn't have to run at full speed before)

Is there anywhere that sells thermal pads?  I am thinking the gap is too large between the cpu and heatsink.

---

### Post by w4ett on 2007-07-19
> **tgm4883 said:**
> Yea its extremely thin.  Denatured alcohol?  Hadn't heard of that, I just use some walgreens 91%.  The fan is running as it normally does, but not full speed (although it didn't have to run at full speed before)

Is there anywhere that sells thermal pads?  I am thinking the gap is too large between the cpu and heatsink.

Yea....been an OEM for for a long time...D. Alcohol is what I use......Also hint #1...the Dell supplied HSF has a bigger gap to facilitate the use of the thermal pad that is supplied with that unit.  I've run into this before, come to think of it.  Run down to radio shack and get some of the regular Heatsink Compound...the thick white stuff, and try it....OR invest in a good quality eg: Thermatake HSF,....BUT try the compound first.

---

### Post by tgm4883 on 2007-07-19
> **w4ett said:**
> Yea....been an OEM for for a long time...D. Alcohol is what I use......Also hint #1...the Dell supplied HSF has a bigger gap to facilitate the use of the thermal pad that is supplied with that unit.  I've run into this before, come to think of it.  Run down to radio shack and get some of the regular Heatsink Compound...the thick white stuff, and try it....OR invest in a good quality eg: Thermatake HSF,....BUT try the compound first.

I'll try the compound.  I don't know how well a thermaltake HSF would work.  Do they make them for laptops?

---

### Post by w4ett on 2007-07-19
> **tgm4883 said:**
> I'll try the compound.  I don't know how well a thermaltake HSF would work.  Do they make them for laptops?

Shows how much I am paying attention...lol

No you are stuck with the stock HSF.....plus if that compound works ok....leave well enough alone...it works as well as that "thermal pad" that was installed at the factory.

If you find that you are still having thermal issues,  the arctic silver folks make some "ceramic" paste that has good properties too,......Just a lot more expensive than Radio Shack   :)

---

### Post by tgm4883 on 2007-07-20
> **w4ett said:**
> Shows how much I am paying attention...lol

No you are stuck with the stock HSF.....plus if that compound works ok....leave well enough alone...it works as well as that "thermal pad" that was installed at the factory.

If you find that you are still having thermal issues,  the arctic silver folks make some "ceramic" paste that has good properties too,......Just a lot more expensive than Radio Shack   :)

[http://www.radioshack.com/product/index.jsp?productId=2526910&cp=&sr=1&origkw=thermal+paste&kw=thermal+paste&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2526910&cp=&sr=1&origkw=thermal+paste&kw=thermal+paste&parentPage=search)
is this what your talking about?  I want to be sure because the word bonds to me means that it is some sort of adhesive.  If this for some reason doesn't work, I want to be able to remove it

---

### Post by w4ett on 2007-07-20
That's the stuff

---

### Post by tgm4883 on 2007-07-20
> **w4ett said:**
> That's the stuff

it it an adhesive or just a paste?

---

### Post by w4ett on 2007-07-20
It's a non-conductive thermal paste, not a true adhesive, dissolves with alcohol,  It will stay pliable even under high heat conditions.

---

### Post by tgm4883 on 2007-07-20
Just called down there, it's web only :(

But I do remember seeing some while thermal paste at a local electronic store, I may go have a look at that.

---

### Post by tgm4883 on 2007-07-20
Just updating.

I went to my local electonic store (Norvac) and got a sheet of thermal pad and some thermal paste.  I then did some testing using cpuburn (burnP6).  All tests had 2 instances of CPU burn running.  Temps measured in conky.

1 thermal pad - I don't think full contact was made between the heatsink and the cpu.  Running 2 instances of cpuburn both my cores at 100% my temp instantly shot up and held around 98C.  During this time my cpu would throttle back (in order to keep the temp down) - Test lasted < 5 minutes

2 layers of thermal pad - Full contact was made, but close to the same result.  Temp instantly shot up, held around 99C.  CPU throttled back to keep temp down. - Test lasted < 5 minutes

Think layer of Silicon Heat Transfer Compound - I didn't have much hope for this.  For a small packet it was $0.90 and it was about as think as the Artic Silver 5 (although I put on a thinker layer of it).  Doing the same test as before, I was surprised by the results.  My temp slowly climbed up to 70C and hovers between there and 68C.  My fan is barely on.  This test has been running the last 26 minutes.

I am wondering if I should be trying the AS 5 again with a little thicker layer.  I will check my idle speeds and see if its any better.  If im as cool as I was before, then :guitar: on


w4eet, some :popcorn: for you for recommending that silicon compound

:EDIT:

I forgot to add the info on the compound.  This is what the packaging says on the compound
Silicone Heat
Transfer Compound
Cat. No. 860-4g
M. G. Chemicals

---

### Post by w4ett on 2007-07-20
Yes...you can try  a thicker application of the arctic silver, but be careful....it is not completely non-conductive........(electrically speaking), but great at xfer of heat to the HSF.

Glad the "old school' method gave you better results though!

Good Luck.

---

### Post by tgm4883 on 2007-07-21
Ok, redid the AS5 job (much like the silicon job).  Interestingly enough, the AS5 job running cpuburn also sits between 68 - 70C.  Idling seems the same.  I figure this is about as good as I am going to get, so I will be happy with it.  

If I had to choose between the AS5 and the silicon compound, I would choose the silicon compound.  Seems that I get about the same results with both, but the AS5 costs 10 times as much.

---

### Post by w4ett on 2007-07-21
Yep....sometimes the old school method works best.   Arctic Silver is VERY good with desktop OC'd machines when the HSF and the cpu has close tolerances (clearance).  In fact I use it on most of the systems that I build, BUT.....in your circumstances....Mass produced Laptop using a thermal pad as the original thermal transfer substance, the silicone paste is a better replacement.

Glad I could help...If you have other questions, I'm normally around.

---

