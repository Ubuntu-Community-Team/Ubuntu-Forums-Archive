---
title: "MP-BIOS bug: 8254 timer not connected to IO-APIC"
date: 2008-06-15
forum: Hardware
---

### Post by Mgiacchetti on 2008-06-15
fresh install hardy 8.04
on boot i receive MP-BIOS bug: 8254 timer not connected to IO-APIC

I cannot successfully hibernate, haven't tried suspend.

in windows i needed some driver for my amd??  was to enable the ability for the processor to cool itself when its hibernating (don't quite understand that but ok microsoft)

There doesn't seem to be any problems besides the hibernate thing currently in ubuntu, but i would like this error gone..

I do not wish to use the noapic in grub, because that would not be fixing the problem, that would be hiding the problem.

I am wondering if anyone has found a viable solution besides the noapic, and besides going into bios and messing with apic.  as another post said "i disabled apic, i dont know might cause problems"

Again both of the above would be "hiding" the problem instead of fixing it.

mobo:  ASUS Naos-GL6 (compaq bios) [Link]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00757470&dlc=en&lc=en&cc=us")
proc:   AMD athlon 64

---

### Post by Mgiacchetti on 2008-06-15
^bump^

---

### Post by Mgiacchetti on 2008-06-16
^another bump^

---

### Post by Mgiacchetti on 2008-06-22
wonders if there is a fix besides "noapic"

---

### Post by Jgrant05 on 2008-06-30
^^yet another bump^^ toshiba Satellite A215-S4817 8.04 64/32bit D/B

---

### Post by mbarvian on 2008-06-30
Another bump, Toshiba Satellite A215-s7422

---

### Post by zasq on 2008-07-10
Hi! Have you found a solution. Have the same problem with a new installation of hardy on Dell Inspiron 1501, AMD 64bit. I agree with Mgiacchetti that the problem should be solved, not hidden...

---

### Post by kam1 on 2008-07-14
i have the same problem with  AMD64 desktop,What should I do??:guitar:

---

### Post by jgoetges on 2008-07-15
Nooby here too with same problem as kam1.Dunno about this forum.4 weeks and no answer.What am I missing?

---

### Post by polecat409 on 2008-08-16
I have the same problem with my Toshiba Satellite A215-S6804 running Ubuntu 8.04 32-bit.

I'm sure someone, somewhere has found a fix for this!?!?!

---

### Post by lisati on 2008-08-16
It's quite a common message - I get it on my Toshiba A100 Satellite laptop, and also on my desktop (Compaq/HP). I think most of the time it's safe to ignore it.

---

### Post by markp1989 on 2008-08-25
i get it on my Fujitsu amilo pro v2030 

tried noapic boot option, and system couldnt boot

---

### Post by GOVATENT on 2008-08-27
I also have the same problem on my toshiba A215-S4757. AMD X2 cpu. I just ignore it. Have had it for ever. I started using ubuntu at version 7. The machine just won't hibernate. Also I can't use the FN keys. Like to dim my screen. My solution is that if I plan to use the machine at night, I go into the bios setup where for some reason the FN keys work. I just dim the screen to a good brightness settings then reboot into ubuntu. Works out. At least ubuntu boots, other distos like slack i have to turn off acpi at grub or it won't start.

---

### Post by cosmoshell on 2008-10-12
im having the same problem

---

### Post by faktorqm on 2008-10-14
^bump^

---

### Post by cosmoshell on 2008-10-17
<burp>^*^

---

### Post by zasq on 2008-12-13
Same problem. And I suspect that some problems I have with usb-devices are connected to it. Any solution yet?

---

### Post by karlmp on 2008-12-24
bump

---

### Post by push23 on 2008-12-25
I had the same problem, but adding "nohz=off hpet=disable noapic" to kernel options helps me.

---

### Post by icanoe2 on 2009-01-15
<<bump>>

Having the same problem and cannot boot any Linux flavours
New install 
ASUS AMD motherboard
AMD Sempron processor
1 Gig ram

---

### Post by michaelalonzo on 2009-01-19
Ive been researching and the noapic-- don`t work for everybody.  
Anyone else got a solution to this? Anyone with a good step by step how-to? I almost got lost just trying to figure out where to type noapic just to find out it does not work.

---

### Post by ph0t0n on 2009-01-30
For the first time EVER, I finally got my laptop to load without me holding down a damn key!

Kernel options were:  ***nohz=off hpet=disable noapic***

---

### Post by freeztar on 2009-03-06
I'm guessing there's still no fix for this other than turning it off?

---

### Post by sadicote on 2009-04-15
Yeah, i think so too, i have just upgraded to Jaunty--once again after i crashed my system trying to migrate to ext4 without an inkling of the basics--and i agree, the 'noapic' workaround is not a fix, even to a total linux dunce like me.

And i don't even have a laptop, just a straightforward desktop with Nvidia 185 Beta installed and working smoothly. This problem did stop surfacing in my first install at some stage, (don't ask when or how, i have no idea), and now after all the upgrades and updates, by the book in a fresh install, this recurrence is something that is unexpected; it's been more than 6 months since! If this is still an existing bug how do i report it?

---

### Post by Geenimetsuri on 2009-05-24
Yup, same here with an ACER Travelmate 230 laptop.

The three "fixes" (read: workarounds) that I've noticed to work:
-noapic
or
-clocksource=jiffies
or
keep tapping keyboard keys(!) and eventually you might get the desktop running. Problem with this approach seems to be occassional wonky system clock afterwards - ie. **decades** off the actual time. :mrgreen:

---

