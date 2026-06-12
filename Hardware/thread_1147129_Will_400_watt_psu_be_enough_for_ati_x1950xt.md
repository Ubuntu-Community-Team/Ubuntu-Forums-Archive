---
title: "Will 400 watt psu be enough for ati x1950xt?"
date: 2009-05-03
forum: Hardware
---

### Post by barisurum on 2009-05-03
Hi there this one is not directly about ubuntu. I consider upgrading my video card to x1950xt and I have a cooler master 400 watt psu. Will this be enough to power the monster? Thanks.

---

### Post by mikedep333 on 2009-05-03
Short Answer: Probably

It depends on what you have in the rest of your system. If you have 8 hard drives, no.

Use a [power supply calculator]("http://www.google.com/search?q=power+supply+calculator&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") like [this one]("http://extreme.outervision.com/psucalculatorlite.jsp"). Make sure it says you will need no more than than like 375W.

---

### Post by Dngrsone on 2009-05-03
It does not appear to require an external power cable, and there are no power requirements listed that I can find.  I'd say it's a good chance your 400W PSU will work fine with it.

---

### Post by barisurum on 2009-05-03
> It depends on what you have in the rest of your system.

Thanks for the posts. Here is what I have as the rest:

amd k8 5600+ dual core 2.8 ghz
two cd/dvd drives
one harddrive sata2
external harddrive usb 2.0
usb sound card 1.1
usb mouse
4gb of 800 mhz ram
no extra pci cards

---

### Post by barisurum on 2009-05-03
Additional info:

I opened the case and saw that my psu has 19A on 12V rail. Is this enough?

---

### Post by mikedep333 on 2009-05-03
I think you will be ok.

A quick estimate of your system on the high side (to be safe.) Your CPU uses like upto 89 Watts, and the graphics card does too. Your drives use about 75 watts. There's roughly 75 watts for the remaining stuff.

That means you're using about 328 watts total. The 12V rail can do upto 228 watts. I bet at least 100W of the 328 watt load is on the 5V rail, so you should be fine.

---

### Post by barisurum on 2009-05-03
> That means you're using about 328 watts total. The 12V rail can do upto 228 watts. I bet at least 100W of the 328 watt load is on the 5V rail, so you should be fine.

Thanks mikedep for your excellent explanation, so I don't have to buy a new 500 watt PSU as the tech forum guys suggest!? They say x1950xt needs at least 30A on 12V rail, and I thought I had to buy a new psu.. They also provide links to their fellow psu sellers.. :D But I realized that 30A is about the whole system load not the gfx card... Thanks again for enlightening me! Cheers :)

---

### Post by barisurum on 2009-05-06
Just installed the new x1950xt, so far no problems. I didn't test it with full load though because the open source ati driver doesn't allow this lol :D If it fails in the future I will go buy a new psu, but both tremulous and assaultcube with full effects didn't produce any problems. Thanks again.

---

