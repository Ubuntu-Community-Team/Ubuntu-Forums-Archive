---
title: "Xubuntu fails to boot after RAM upgrade."
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by jrollf on 2007-07-19
I've been running Xubuntu for about 3 weeks now.  Overall it has been running well, at least untill I tried to add ram to my system.  The system is intended to be a home file server and ftp server on the internet (and possibly a low end web server in the future).
 
I've made a few upgrades in the last couple of weeks, so I'll give a brief history before I address my current issue.
 
Here is my system as it was when I first installed Xubuntu:
 
Gigabyte GA-71x motherboard
600 mhz Athlon Slot A
256 mb RAM (2 x 128 mb SDRAM, one PC100 one PC133)
Generic NVIDA card
30 GB Western Digital IDE
 
I ran this conifg for a couple of weeks, it ran well so I decided to upgrade the system.  My first upgrade was to change the CPU to an 1Ghz (1,000 mhz) Athlong Slot A (Orion core).  All went well.
 
Finally I got a hold of some 256mb, low density, PC100, CL2 ECC (non-registered) RAM (which Gigabyte says my motherboard will run).  I actually have 5 sticks of the RAM (all same make and type), my motherboard can only take three, so I have 2 extras.
 
I have found that I can use 2 sticks in any of the three slots (for a total of 512mb) and Xubuntu runs great (with ECC enabled or disabled, both work).  But for some reason as soon as I put 3 cards in the system Xubuntu either fails with a "core panic" or just hangs on the Xubuntu boot logo screen.  I'm suspecting this is a motherboard issue, but I'm not sure.  I've even tried disabling ECC, setting the timings to slower CL3 settings (including all the related timings), but nothing seems to work.  I've tried all 5 RAM cards, any of them work great as long as only two are in the sytem. 
 
So here is what I'm left with:
 
[COLOR=blue]This systems works:[/COLOR]
Gigabyte GA-71x
1ghz Athlon slot A
[COLOR=blue]512 mb PC100 CL2 ECC RAM (2 x 256mb low density)[/COLOR]
 
[COLOR=blue]While this system hangs:[/COLOR]
Gigabyte GA-71x
1ghz Athlon slot A
[COLOR=blue]768 mb PC100 CL2 ECC RAM (3 x 256mb low density)[/COLOR]
 
The end result is I might just end up staying with 512mb, but I have the RAM and would really like to run 768mb (especially if I do use it as a web server).  The sysetm works great with 512mb, with or without ECC enabled.  The manual for the motherboard says I should be able to run 3 x 256mb cards.  Any suggestions?
 
Thanks,
John

---

### Post by Kowalski_GT-R on 2007-07-19
Maybe I can help.

Does your system use a Via chipset? I'm afraid it can be a bit of an Headache at times.

Slot A Via chipset on one of my pcs didn't seem to like different sticks, even if characteristics were the same.

Tried everything possible: inverted sticks. tried slot 2 and 3, 1 and 3, 1 and 2, no joy.

At the end i went for a single stick (i was hoping to install 1 Gb,now performance is better with a single and faster 512 stick: same win xp OS)

A shop attendant confirmed me Via chipsets were prone to this "fuzziness".......

---

### Post by jrollf on 2007-07-19
Yes it has the VIA 751 northbridge (IronGate) with the corresponding VIA southbridge. This system is old enough that 256mb sticks are the largest my motherboard will accept, so 512mb sticks won't help. :(
 
Thanks,
John

---

