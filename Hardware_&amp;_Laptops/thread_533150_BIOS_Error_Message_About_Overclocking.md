---
title: "BIOS Error Message About Overclocking"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Geekkit on 2007-08-23
So I booted up my computer this morning (Ubuntu 7.10) and the BIOS complained about overclocking had failed and allowed me to press F1 to go into setup or F2 to use defaults. Of course I chose F2 and Ubuntu booted just fine.

I'm puzzled though because I didn't make any BIOS changes or even configuration changes last night in Ubuntu. Could this possibly be my BIOS battery giving up the ghost?

---

### Post by w4ett on 2007-08-23
That's what it sounds like....the CMOS tests it's checksum every boot... a weak battery can give you this error.

---

### Post by RJARRRPCGP on 2007-08-23
> **w4ett said:**
> That's what it sounds like....the CMOS tests it's checksum every boot... a weak battery can give you this error.

But, I do find that strange. If the BIOS battery was weak, then it should just say "CMOS checksum error" or similar. Also, I would check the clock for signs of a dying CMOS battery. 

Did the clock suddenly go to a rediculously long time ago, like "December 1, 1999"? 
It may, even when the motherboard is far newer!

---

### Post by w4ett on 2007-08-23
> **RJARRRPCGP said:**
> But, I do find that strange. If the BIOS battery was weak, then it should just say "CMOS checksum error" or similar. Also, I would check the clock for signs of a dying CMOS battery. 

Did the clock suddenly go to a rediculously long time ago, like "December 1, 1999"? 
It may, even when the motherboard is far newer!

All things considered, the Battery can be at that infamous "borderline" state....it can cause some (non-technical term) freaky errors, some of which are oftentimes not able to be reproduced on multiple boots.  Besides, a $2.00 fix is extremely cheap.

---

### Post by ricardisimo on 2007-11-12
I got the same message, only it was preceded by several days' worth of failed bootups, first by Gutsy, and then Feisty, after I decided I'd had enough. Drive light blaring away, but nothing ever comes of it. Only thing I can do is hit the power reset over and over until one of the boots finally sticks. Clock looks fine, by the way. Anything else I should check?

I'm curious about something I noticed during bootup: one of my /grub/menu.lst settings from two installs ago (the timeout) was still in effect. What gives there? I thought a new install was a new install, tabula rasa. If that stuck around, maybe something else did also, something causing this problem. No?

---

### Post by ricardisimo on 2007-11-12
<Bump>

---

### Post by ricardisimo on 2007-11-20
Still having the same problems. I have to boot and reboot several times before it "takes". Then I get the "Overclocking failed" warning, with the option to enter BIOS setup or use defaults.

I've tried real basic mechanical stuff, like letting the PC run for a while so as to see if one or another component is overheating noticeably. The RAM chips seem nice and cool all of the time, but I do notice what might be a bit of excess heat coming off of the ATI graphics card. Could this be causing the problem?

Also, is there a way to upgrade BIOS, and would this even be wise? Thanks in advance.

---

### Post by ricardisimo on 2007-11-21
<bump>

---

### Post by ricardisimo on 2007-11-24
<bump>

---

### Post by RJARRRPCGP on 2007-11-24
Similar problems have been reported with some motherboards before, seems to be a motherboard flaw.

But please inspect your PC for bad caps.

---

### Post by ricardisimo on 2007-11-27
What exactly is "charm" and where would one find it? Thanks.

---

