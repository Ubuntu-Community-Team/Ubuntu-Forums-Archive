---
title: "IMPORTANT: Corrupted RAM/motherboard?"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by StarsAndBars14 on 2006-10-15
I've had a bunch of errors over the past few weeks which may result in my throwing out a HP computer that I've had for about 4 and a half years.  Seeing as I don't have the money to buy a new one at the moment I'd rather prevent this by swapping out parts.  The problem is as follows:

About that amount of time ago,  I received a bunch of auto reboots at the Windows XP bootsplash logo.  Those reboots made sure I could only get in through safe mode, so I ran a bunch of software scans and checks -- from Chkdsk to HijackThis.  I thought I isolated the problem after it started working again.  Not so.  Reboots progressed to STOP 0x8E errors and in turn to STOP 0x7F errors.  Everything from notices to blue screens with memory dump.  The problem appears to be hardware related.

So I ran hardware diagnostics in the form of PC Doctor.  Nothing returned an error.  Then it progressed to Seagate diagnostics (I use a ST380020A hard drive) which didn't return any errors. . .even on memory scans. :confused:

Out of options, I remembered Memtest86+ and checked it out.  On tests 4, 5 and 6 errors began cropping up like crazy in the first 27.3MB of 512.  12 errors on test 4, 1 on test 5 and over a hundred on step 6.  I decided I'd seen enough after test 6 completed and went to turn the computer off.

Is it possible for my computer to be so screwed up that reputable diagnostic measures are returning unreliable results?  I have a chance to swap out and upgrade RAM today which could correct this problem if I'm right, all the way from Memtest to Windows not starting in normal mode.  I've had issues on 6.06 LTS which are hardware related lately but they center around the Xserver displaying orange and green lines on server restart.

Should I patch my kernel to account for defective RAM areas 

[http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/)

(I'm using a custom 2.6.16.18 with iptables and netfilter mods) 

or do kernels - especially those made for Ubuntu - already have this functionality built in?  Since I'm able to use Linux without it really and truly crapping out my guess would be "Yea" but I just want to make sure.

Whoever can answer these questions would have my eternal gratitude.

---

### Post by bigken on 2006-10-15
sounds more like your graphics card has gone or is about to do have another card you could test with ?

---

### Post by bigken on 2006-10-15
also how many sticks of ram does it have have you tried the ram in diferent slots ect

---

### Post by StarsAndBars14 on 2006-10-15
The monitor turns off some times after a server restart.  I have an integrated S3 which is a piece of garbage but I haven't used it in a long time so I wouldn't know if its functional.  

Besides which, I got the ATI card that I have quite a while after the computer itself so according to logic, if anything would go first. . .

You know. :P

It has one stick of RAM at the moment.

I'm really confused now, I don't know if this is memory related or graphics related.  The bulk of graphics problems have been occuring on Linux.

---

### Post by bigken on 2006-10-15
I would pull the ati and try onboard graphics ;)

---

### Post by StarsAndBars14 on 2006-10-15
I talked to someone on the phone that works with computer hardware.  He seconded that.  So I went ahead and pulled it out, the computer started up normally.  

Now, the issue becomes this:

1.  Dust in the inside of the computer may have broken the video card.
2.  That could also have been the reason for Memtest returning errors and the CPU operating at 160 degrees F.
3.  If the reboots/bluescreens/graphics issues continue, then its the memory.

I clean the computer regularly, both on the inside and back outside where the fans are.  I can't get in there to clean that much on the inside owing to both the type of cleaner I'm using and the cramped case.

I might still try to upgrade the RAM for cheap.  I have another slot that I can use stuck in the motherboard between the fan and the disk cables.

---

### Post by bigken on 2006-10-15
I think the ati card was over heating causing the high temprature readings 
to clean the inside of the pc all I use is soft paint brush

---

### Post by StarsAndBars14 on 2006-10-15
I took it out and its running at 157. . .may not have been enough for that to be the cause.

I'll give it a few hours.

---

### Post by bigken on 2006-10-15
this is what I would do next remove the heatsink and fan clean them thourghly and clean off any thermal paste reapply new paste and reseat the sink and fan  in fact strip  the machine and clean all the inlets and fans  ;)


could be cpu fan is failing ?

---

