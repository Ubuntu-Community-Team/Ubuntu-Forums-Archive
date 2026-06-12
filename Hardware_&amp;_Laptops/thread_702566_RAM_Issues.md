---
title: "RAM Issues"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by Mephy on 2008-02-20
Hello,

I think Ubuntu may have messed up my RAM? :(

I hate to say it but it happened right after I installed Ubuntu.

Anyway, I ran Memtest86+ and my memory failed every test. I'm dual booting Windows and Ubuntu, and now, after installing Ubuntu, I get issues on both of them.

I disabled the reboot thing on My Computer so it would give me the BSOD when I have an error.

And the error changes, the first one was something about POOL_**** (i think the stop code was 0x0000006C). The other one that I got was IRQ_NOT_LESS_OR_EQUAL (stop code 0x0000000A).

I'm sure that it's my RAM after the testing in Memtest, but is there a way to fix this? (Other than replacing the RAM?)

I'm currently using 2 gb Crucial Ballistix ddr2 800

---

### Post by Yellow Pasque on 2008-02-20
Have you OC'd your processor or system in any way? Have you tried raising the RAM voltage (don't exceed 2.2V) and/or relaxing the timing to make the RAM  more stable?

---

### Post by Mephy on 2008-02-20
Nope, I actually haven't even OC'd my CPU yet. (That's pretty much the reason I bought the CPU because it's a good OC'er   [core2duo e6300])

But I haven't OC'd anything at all, let alone changed any settings after I installed Ubuntu

I have it on auto detect so it adds more voltage when it needs more voltage, I put in my other 2 gigs and took out the Ballistix and everything seems to be fine now, but I'd prefer to have the ballistix in

---

### Post by Yellow Pasque on 2008-02-20
> I have it on auto detect so it adds more voltage when it needs more voltage
Heh, that's not how it works. Auto detect reads the EPD of the RAM to determine what to set the voltage to. Your RAM probably only asks for 1.8V so it can POST with almost any system. You have to manually up the voltage if you want to get the rated speed/timings.

---

### Post by Mephy on 2008-02-20
Changed it to the  2.2V that Crucial recommends and still no go :\

I don't think it's anything with the settings I have because it worked fine for months before I installed Ubuntu.

The only thing I did besides install Ubuntu that I haven't done in a while was defragged my HD around the same time. Could this cause the issue?

---

