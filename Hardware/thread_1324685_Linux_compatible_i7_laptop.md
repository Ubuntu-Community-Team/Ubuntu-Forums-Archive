---
title: "Linux compatible i7 laptop?"
date: 2009-11-12
forum: Hardware
---

### Post by josephellengar on 2009-11-12
Anybody know of a linux compatible laptop with the core i7 processor?  I had an order up for an hp envy 15 until I heard about all of the bugs in the bios.  I know of the studio xps 16, but I kind of hate Dell, so I'd like to avoid that if possible.  I am willing to pay a premium for something that looks nice as long as it has good specs (specifically core i7, and 6 or 8 gb of ddr3 1333 mhz ram).  Any suggestions?  (I hate Apple).

---

### Post by auslander on 2009-12-24
> **rossholley said:**
> Anybody know of a linux compatible laptop with the core i7 processor?  I had an order up for an hp envy 15 until I heard about all of the bugs in the bios.  I know of the studio xps 16, but I kind of hate Dell, so I'd like to avoid that if possible.  I am willing to pay a premium for something that looks nice as long as it has good specs (specifically core i7, and 6 or 8 gb of ddr3 1333 mhz ram).  Any suggestions?  (I hate Apple).

I have the exact same question.  The Envy 15 has some interesting BIOS, though it looks like there's a patch coming that fixes most (all?) of that?  [http://lkml.org/lkml/2009/12/20/146](http://lkml.org/lkml/2009/12/20/146)

It sounds like the Dell has problems of its own.  See this thread:  [http://en.community.dell.com/forums/p/19306277/19605802.aspx?PageIndex=1](http://en.community.dell.com/forums/p/19306277/19605802.aspx?PageIndex=1)
I guess the factory BIOS underclocks to try and prevent using more than 90 watts (the size of the power supply), so some people have received 130 watt supplies from Dell which helps but there are other issues and Dell claims a BIOS update is coming in early Jan.  Apparently running on battery doesn't have this problem, only when on AC power.  The HP comes with a 120 watt PSU, it's hard to imagine that setup using less than 90.

It seems like the Envy is better as far as heat dissipation, the lack of an optical drive is not a problem for me at all -- and you can put 16GB (!!) of memory in it.  Dell appears to have a better keyboard and LCD, HP has a more powerful video card (ATI 4670 on Dell, ATI 4830 in the HP).

The BIOS issue in the HP appears to be a Linux bug in ACPI setup.  The Dell BIOS issue appears to be a deliberate attempt to reduce power on the machine to meet the external PSU output, which seems worse somehow.

If I knew that one of these two machines ran Linux reliably (and at relatively low temp) I'd buy one today.

---

### Post by christian.convey on 2009-12-24
I just ordered at Dell M6500 mobile workstation, which I suspect (hope) has good Linux compatibility.  If you ask me in a month I should have a more definite answer.

BTW, it's expensive, but take the posted price with a grain of salt.  After some negotiating I was able to get an M6500 configured at $4100 for a final price of $2800.

---

### Post by josephellengar on 2009-12-24
I bought the dv7t quad.  That is supposed to have at least pretty good compatibility, and fortunately, HP has a 21 day return policy no questions asked, so I'll return it (free shipping!) if it's not compatible.  Also, it's a lot cheaper than the envy and doesn't have the mouse problems.

---

### Post by auslander on 2009-12-24
Yeah, but only 1600x900 screen on the dv7t, and it's big.  Envy is pretty light, played with one at Best Buy today.

Wish someone could verify that "turbo boost" and other features work with Linux after that patch.

---

### Post by josephellengar on 2009-12-24
> **auslander said:**
> Yeah, but only 1600x900 screen on the dv7t, and it's big.  Envy is pretty light, played with one at Best Buy today.

Wish someone could verify that "turbo boost" and other features work with Linux after that patch.

Yeah, I know.  I was disappointed with the screen, but the fact that the mouse doesn't work at all (even in windows sometimes) was the killer for me.  I can indeed confirm that turbo boost does work though, based on another thread with an authority on the topic.  What other questions did you have?  If they were in the other thread I can find the link and post it here.

---

### Post by auslander on 2009-12-24
> **rossholley said:**
> Yeah, I know.  I was disappointed with the screen, but the fact that the mouse doesn't work at all (even in windows sometimes) was the killer for me.  I can indeed confirm that turbo boost does work though, based on another thread with an authority on the topic.  What other questions did you have?  If they were in the other thread I can find the link and post it here.

What other thread?

Yeah basically just wanted to know if the patch fixes *all* the ACPI issues or just some of them.  So, correct fan usage, thermal zones, etc, etc.

---

### Post by josephellengar on 2009-12-24
> **auslander said:**
> What other thread?

Yeah basically just wanted to know if the patch fixes *all* the ACPI issues or just some of them.  So, correct fan usage, thermal zones, etc, etc.

This thread: towards the end the guy who proposed those acpi patches discusses compatibility etc.

```

http://h30434.www3.hp.com/t5/Operating-systems-and-software/BIOS-broken-on-HP-Envy-15-and-DV6T-Quad/m-p/151225

```

---

### Post by auslander on 2009-12-24
[http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15/](http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15/)

Looks like everything is working except video when doing resume from suspend.  Awesome.

Too bad BestBuy isn't open on Christmas day.

---

### Post by jdos2 on 2009-12-25
(blush) I'm supposed to be working with the X folks on the video but have restored the laptop that I can install BIOS updates- when I installed Ubuntu I wiped the laptop, meaning that I made myself a LOT of work.

I'll have Ubuntu installed later in the week and'll be able to report back to 'em what they wanted.

---

### Post by josephellengar on 2010-01-08
Got my dv7t a few days ago.  I can verify that everything works except for the video gets corrupt after suspend or dropping to a command line.  This is fixed by restart.  Otherwise, it's a beautiful machine.

---

