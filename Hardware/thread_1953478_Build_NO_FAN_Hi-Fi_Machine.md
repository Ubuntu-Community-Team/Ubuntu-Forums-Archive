---
title: "Build NO FAN Hi-Fi Machine"
date: 2012-04-06
forum: Hardware
---

### Post by jamesisin on 2012-04-06
Hello,

I am working to design and build a custom case to house a fan-less Ubuntu machine to process music for my hi-fi.  I am especially interested in locating the parts best suited to minimizing heat production so that heat sinking will manage all heat dissipation.

CPU
RAM
MB
Power Supply
Video Card (with compositing)
SS HDD

There will be a CD drive and that should be the only component with moving parts.

Under-clocking and over-building seem in order, but again the main goal is to have a reasonably powerful machine which minimizes heat production so as to remove any need for cooling fans.

Thanks for your opinions.

---

### Post by winh8r on 2012-04-06
This product might interest you:

[http://www.quietpc.com/products/cpucoolers/nof-cr-100a]("http://www.quietpc.com/products/cpucoolers/nof-cr-100a")

The rest of the site is good too.

i havent used this particular product but have used the site before to purchase quiet fans.

Worth a look, for inspiration if nothing else!!

Hope this helps you.

---

### Post by Yellow Pasque on 2012-04-06
Personally, I would opt for a really quiet (undervolted) 120mm or 135mm fan on a large CPU heatsink, since that will probably be the toughest component to cool passively. I had a 65W CPU cooled passively for a while, but I did eventually overheat it. :\

SPCR is a favorite site of mine, and you can get a lot of ideas by browsing through the forums there.

CPU: Since it's only a 65W TDP and has a nice IGP, this is a good choice: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116400](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116400)

PSU:
[http://www.silentpcreview.com/fanless-psu-build-guide](http://www.silentpcreview.com/fanless-psu-build-guide)
[http://www.silentpcreview.com/Recommended_PSUs](http://www.silentpcreview.com/Recommended_PSUs)

RAM: Get the 1.35V DDR3 if possible

GPU: Not sure what your needs are. If they're basic, the GPU integrated into the CPU (assuming you get intel sandy bridge) will work nicely. Maybe a fanless nvidia gt430 or gt520 if you need good video playback acceleration.

---

### Post by jamesisin on 2012-04-07
> **winh8r said:**
> This product might interest you:

[http://www.quietpc.com/products/cpucoolers/nof-cr-100a]("http://www.quietpc.com/products/cpucoolers/nof-cr-100a")

That looks pretty sweet.

Would it work with the CPU below?

When it says it's 100W, what's that about (since it can't be about powering something)?

What else might I need to know to create a system using that IcePipe without a fan?

> **Temüjin said:**
> SPCR is a favorite site of mine, and you can get a lot of ideas by browsing through the forums there.

CPU: Since it's only a 65W TDP and has a nice IGP, this is a good choice: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116400](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116400)

PSU:
[http://www.silentpcreview.com/fanless-psu-build-guide](http://www.silentpcreview.com/fanless-psu-build-guide)
[http://www.silentpcreview.com/Recommended_PSUs](http://www.silentpcreview.com/Recommended_PSUs)

RAM: Get the 1.35V DDR3 if possible

So perhaps pair that CPU with this MB?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121527](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121527)

Then get the 1.35V DDR3 (if that's available for this combination)?

I'll take a look through this site as you recommended it (both of the links you provided look promising):

[http://www.silentpcreview.com/](http://www.silentpcreview.com/)

As to the video... this machine will be at my hi-fi (in my living room) where guests will see it and have access to it (a showcase).  Since I (also) advocate for Linux/Ubuntu I want it to be able to manage the basic bells and whistles of compositing for the fancy desktop effects as this would be most impressive given the context.  No movies, no gaming, but minimally capable.

Thanks to you both.  This is proving quite excellent.

---

### Post by Yellow Pasque on 2012-04-07
> I want it to be able to manage the basic bells and whistles of compositing for the fancy desktop effects as this would be most impressive given the context. No movies, no gaming, but minimally capable.
Then the intel IGP will work fine.

---

### Post by jamesisin on 2012-04-07
I was considering an off-board video card for thermal management.

My theory being that if I remove that chore from the CPU and put into a separate video card I would be saving myself heat production in the CPU (which I guess to be the most heat producing item of concern).

Less of an impact if we are not discussing an in-CPU GPU but an on-board GPU; in which case the thermal savings would be lessened (because the CPU and GPU are still mildly thermally connected via the MB).

Either way if the video card is inexpensive enough I could add it later or add it now depending on budget.

I think your recommendation would be to try it using the on-board GPU based on the MB in the link I suggested above?

---

### Post by winh8r on 2012-04-07
The IcePipe cooler specs (on the same page as the link) show it as compatible with the i5.

You might find this site useful too for specs of various CPU's and their operating temp ranges:

[http://pclinks.xtreemhost.com/elec.htm#intel_desktop]("http://pclinks.xtreemhost.com/elec.htm#intel_desktop")

The i5 is about halfway down the page linked above.

I would imagine that one possible limiting factor would be the anount of space you have inside the case.

On the other hand if it is fanless then you could create more vent holes/slots on the sides/rear panels as sound deadening will not be an issue without a fan whirring away in there.

Hope this is of some help to you.

---

### Post by jamesisin on 2012-04-07
I'll be building my own case and using a very open design.  (I want it to look good along side the other hi-fi gear.)  So materials selection and size and shape are all up to what I am able to create.

Great chart.  So the Max Cover Temp is my maximum target at the base of the heat sink.  That's useful.  I have a really nice Fluke temperature probe so I can make pretty accurate readings to gauge how my set up is performing.  I suppose my ideal ought to be something like half of that figure.

I figured in my case design I would be keeping the four components separate to minimize heat-sharing, a sort of four zone design: PS, MB, HDD, CD.  I'll use a flat design so that nothing heat producing is above anything else which might produce heat.

Of course CPU, RAM, and PS are the primary heat generators, and so augmenting those with heat sinks (especially good looking ones) is very much in order.

---

### Post by jamesisin on 2012-04-18
I'm curious if anyone can direct me toward an article on underclocking in Ubuntu?

---

### Post by jamesisin on 2012-05-06
Bought an IcePipe, copper.  Ships from UK.  Waiting...

---

