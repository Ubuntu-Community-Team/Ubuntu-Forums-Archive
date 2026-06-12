---
title: "xircom pcmcia card support"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by towner on 2005-01-19
a bit of advice needed, 

i've been lucky enough to be offered three pcmcia ethernet cards. Ive done a limited amount of research and dismissed the chances of getting one of them to work (xircom cardbus ethernet cbe-10/100btx), that leaves me with two xircom creditcards,  ce3b-100btx and ce3-10/100. 

has anyone managed to get either of these cards working with ubuntu/

any tips gratefully received.

---

### Post by Soulman on 2005-01-21
Have you tried "sudo modprobe xirc2ps_cs" on the command line as root.  This module works with my xircom XE2000.  Hopefully this will work with yours also.

---

### Post by towner on 2005-01-21
thanx Soulman,
I'm at work at the moment but will give it a go later
 8-)

---

### Post by dbutcher on 2005-03-03
I am a brand new ubuntu user.  
I also have Xircom XE-2000 card, but it is not recognised in device manager when I insert it.  It there a way to force install recognition of the card?  (I also have a 3com card that works flawlessly.

---

### Post by dbutcher on 2005-03-03
I should have said that I tried the modprobe xirc2ps_cs command, but without effect.  (ie: it's not the driver that's missing, but the card itself.)  It does not matter whether I install the card in my laptop, or in the docking station, it is simply not recognised in Device Manager.
Thanks for any advice.

---

### Post by Bart Rombaut on 2005-04-13
But it works for me, thanks!!!

Any idea how I can make it automatically when starting up?

[edit]

ow it is already  O:) 

[\edit]

---

### Post by dotsi on 2007-11-08
Dudes,

First of all, sorry for the possibly unconventional "bump" for this thread. I did it because I'm having the exact same problem with my IBM ThinkPad 600E, Xircom XE2000 and Xubuntu.

The card shows up OK, modules are loaded, the link is up, addresses are as they should be, but ping still doesn't get through even to my router, let alone anywhere else. I have tried at least a couple of different cables, but neither of them didn't seem to be faulty in any way.

Do I need a miracle or what?

**EDIT:** solved by getting a 3com NIC that works :)

---

