---
title: "Kernel panics, Amd 64 dual core, and Ati"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by jaden-excalibur on 2007-08-14
Hi everyone, I need help from all of you today, or anyone who will listen...

For the past year I have taken fondly to linux, specifically Ubuntu, and have had a fun time learning all the tricks of the trade. Somewhere along the way, I noticed that I had an annoying problem that just wouldn't go away... random kernel panics.

For anyone who's had to live with stuff like that, it really is depressing, but it tends to get fixed after a while -- not so with me. My dual core amd 64 proc has been dying no matter what fix I try, and the only signs I have are these:

1. The irq timer 8254 is being circumvented for some reason, and PCI 3 is not being read correctly in the latest gutsy kernel I imported to Feisty.

2. This is an HP media center PC model m7248n , composed of an 

ATI (!!!) IXP 400 motherboard, pheonix bios (up to date), 

ATI Catalyst X300/X500 graphics card.

Falcon 2 video input card (activated as default, but not recognized by IVTV)

4200+ dual cores, 1gb ram,  the rest is insignificant.


Basicaly, I get some crazy crashes most of the time when the falcon card is linked to the IVTV driver, and ends up causing a kernel panic. The rest of the time, it panics randomly, as far as I can tell.

If you have successfully used this model of HP pc before, please let me know, or if you know how I can deactivate the IVTV driver during boot.. that would be great too. 

All help is appreciated, Thanks.

---

### Post by shad0w_walker on 2007-08-14
The most important and obvious question first. Did this all start when you installed the gutsy kernel? If it did then the advice is simple, go back to the Fiesty kernel and wait for the final release then upgrade. 

There is very little advantage as far as I'm aware to grabbing the new kernel (I believe it has CFS but if its causing kernel panics then its not really worth that gain.)

---

### Post by jaden-excalibur on 2007-08-15
Lol, no no, the .22 kernel is not causing it. Well, it's adding one more problem with my third pci card, but other than that they're all the same. I mean, I've only been on  the linux block for a year or so, but this problem has made me dig into so many papers on the kernel design philosophy and the semantics of the linux OS that, well I would have noticed ;).

But yea, right now my thinking is that there may be MANY different causes for these hangs, as some fixes seem to improve stability, but not completely. Right now my best bet is to try circumventing the IVTV driver module and see how that does it. During boot, it's most likely to die right then, with a mailbox error or some-such. If you have any clue on how to better trouble shoot this, it would be appreciated!

You can grab an example of my standard kernel log at [www.tyronemedia.com/kernlog.txt](www.tyronemedia.com/kernlog.txt) 

I could get you a pci list if you want? Doubt it would help more than what I specified.

---

