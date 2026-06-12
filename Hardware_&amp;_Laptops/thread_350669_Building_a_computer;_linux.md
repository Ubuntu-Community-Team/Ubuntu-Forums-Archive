---
title: "Building a computer; linux"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by billybag on 2007-01-31
I have built computers in the past, but with the intention of using windows.

i would like to build a computer specially for using ubuntu linux. i know hardware is much better than others when it comes to linux.

i was wondering if people can provide insite/tips on what to get for harware.

---

### Post by aysiu on 2007-01-31
I've moved this to a more appropriate forum.

---

### Post by tommcd on 2007-02-01
Chech Phoronix for linux hardware support.
[http://phoronix.com/](http://phoronix.com/)
From what I gather the nvidia 550, 570, and 590 chipsets are pretty well supported now for AM2. The core 2 duo intel chipsets seem to be pretty well supported with the 2.6.18 kernel, which will be in Feisty, I think. 
Read the articles on Phoronix for specifics.

---

### Post by RandomJoe on 2007-02-01
I generally spend a bit of time on Google - specifically [http://www.google.com/linux](http://www.google.com/linux) so I hopefully get searches more pertinent to Linux - searching for info on the various parts I'm interested in.  Go deeper than the first page, sometimes the problems won't always show up in the most popular results!  And since you have a particular distro in mind, of course spend time searching through distro-specific forums like this one.

It helps if you can figure out which chipsets are being used on a given item, then search on that chipset.  As an example, some Core 2 Duo systems - while largely very nicely working - have an issue in some cases with the PATA interfaces.  Intel dropped PATA support for their chipset, so any boards using an Intel chipset have to use another chip to handle them.  Jmicron seems to be common, and there have been many postings here about the troubles people have had with them.  But that's only the Intel-chipset boards, I have an nForce board that's fine.  Of course, there are many models of nForce, some more supported than others so - again - pay attention to the details!

But be careful to note the dates on anything you find - I've read some real rants about pieces of hardware, which would have turned me off until I noted the date was 2 years old and subsequent digging turned up evidence that the same device is now well supported.

When I built my most recent system, it started by reading a very positive review about a particular motherboard and the Core 2 Duo, then snowballed from there.  Annoyingly I can't find the mobo review anymore but I did visit the site tommcd mentioned, as well as [http://www.linuxhardware.org/](http://www.linuxhardware.org/) for more info on various parts.  Usually led there by a Google search link.

Perhaps not the most exciting way to build, but I also try not to go "bleeding edge" with the latest-and-greatest hardware.  I'll pick up items that have been out for a year or so, which means at least a few people have had a chance to play with it and work out bugs or at least catalog what's doable with it.  Let someone else be the guinea pig! ;)

---

### Post by tommcd on 2007-02-02
That linuxhardware.org site is new to me. I will have to check it out. As RandomJoe stated, the newer bleeding edge stuff will be more likely to have hardware support problems. If you like to be an early adopter of new hardware be aware of that. The Phoronix site is a good place to ask about that. Their forum admin Michael is very knowledgeable about new hardware and linux, and he answers many posts.
Older hardware (e.g., AMD socket 754 and 939 chipsets from nvidia and via; and the intel P4 chipsets) is almost all well supported at this time.
A quick google search for <motherboard-name linux> or <chipset-name linux> will usually find any support problems from lots of forums. Be careful of the dates though, as RandomJoe said.

---

### Post by billybag on 2007-02-03
thanks guys! your info has been very helpful

---

