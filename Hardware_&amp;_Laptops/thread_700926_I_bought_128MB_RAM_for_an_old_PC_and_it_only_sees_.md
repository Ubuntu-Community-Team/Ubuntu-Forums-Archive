---
title: "I bought 128MB RAM for an old PC and it only sees it as 64MB"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by Pogeymanz on 2008-02-18
This isn't a Linux problem in anyway.

My friend's old 450Mhz PIII had 64MB RAM and of course he never used it at all.

Enter me with DamnSmallLinux, and he could then TOLERATE to surf the net with that PC since it's in his bedroom and the main PC is in the office.

Anyway... I found a stick of 128MB on ebay, still in the wrapping. It was 100Mhz, which is the bus-speed of his PC, but when I put it in for him, it only showed 128MB total.

I tried takinig the old stick out and only using the new stick, and it said 64MB. I've been talking to the seller and I don't think he is trying to scam me or anything, but he doesn't know what I should try next, either.

So, can you think of anything to get the PC to see that it's 128MB (thus making the total 192MB)? I know the max RAM for that PC is higher than 128MB.

---

### Post by oldsoundguy on 2008-02-18
you bought double density for a machine that can only see single density.  BTDTGTS!!!

---

### Post by jrusso2 on 2008-02-18
> **oldsoundguy said:**
> you bought double density for a machine that can only see single density.  BTDTGTS!!!

Yes I bet thats the problem

---

### Post by Pogeymanz on 2008-02-18
Oh dang. I didn't realize they even made double-density RAM for computers with 100MHz bus-speed.

---

### Post by kerry_s on 2008-02-18
you know the max is more than 128mb, how about just telling us the make and model # of the computer so we can look it up?

sometimes only a certain amount of ram is supported in the bios and a bios update is needed.

---

### Post by Pogeymanz on 2008-02-19
Well, I'm not sitting in front of the computer or anything. I just emailed him and asked him what kind it is.

The best I can tell you now is that I think it's a Gateway from 1998 or 99 with a Pentium III @ 450MHz.

---

### Post by oldsoundguy on 2008-02-19
Have your friend get the FCC number and go to the FCC site and plug that into their search engine.  He will come up with the info on the Gateway and most likely there will be a link to a PDF of the user's manual.  THAT will tell him and you all about what kind and how much memory the unit supports.

Had there been WinDOZE on the machine, you could use Belarc Advisor and run it.  

In Linux the command is lshw.  It will give you a hardware list of what is is installed. 
IF you need to install the program, here is the info: [http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)
But Gutsy has a non GUI already in it.

---

