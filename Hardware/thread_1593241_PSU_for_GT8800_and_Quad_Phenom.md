---
title: "PSU for GT8800 and Quad Phenom"
date: 2010-10-11
forum: Hardware
---

### Post by Pithikos on 2010-10-11
After a lot of sudden restarts when playing games and a lot of searching and posted I just decided to buy a new PSU. At the moment I have a Turbo-X at 370watt.

My system parts are:

[LIST]
[*]Phenom || x4 965 Black Edition
[*]4GB ddr3 Ram lat-7
[*]GT8800 512MB PCIE
[*]ASUS M4A87TD
[*]1 HDD Pata133
[*]1 USB external HDD
[*]1 PCI to USB plugs
[/LIST]

I am very sceptical about what kind of PSU I need. The one I have now states:
3.3V ->14A
5V -> 30A
3.3V + 5V -> 180Watt
--------------------------
12V -> 15A -> 180Watt

From other posts I realised that my 12V rail is low on ampere. The thing I am mostly wondering about is if it's nessesary to buy a PSU with a 12V rail at say 40A or is it just fine to buy one at 20A? The thing is that the videocard has an extra power plugin. In that case isn't it enough to have for example 13A from the motherboard and 13A from the PSU directly to the videocard if the recommended current for the video card is 26a? Thinking that 13A+13A=26A.

Would appreciate some answer as I have been fighting for this a week and my brain has become a mess full of voltages and amperes :S

---

### Post by cascade9 on 2010-10-11
Thats an 'old school' power supply (high 5v, low 12v). 

If your computer is freezing/crashing/restarting when playing games, but not any other time, there is agood chance it is power supply related (and with that 360watt power supply, you were uder nVidias recommended 400watt minimum for that video card). 

You should be able to get away with a 450watt unit, going up to 500-550 wouldnt be a bad idea. BTW, better to get a good power supply by a good brand with a decent amount of watt over a 'yum cha' power supply with a huge rating.  Corsair and seasonic are some of the best power supplies around now, but those arent your only choices. ;)

---

### Post by Pithikos on 2010-10-11
Thanks for your reply.
Well I was thinking about CMPSU-550VX 550W from Corsair which has these main specs:
+3.3V@30A, +5V@20A, +12V@41A

So for the 12V rail it's 12*41=492Watt
For the 3.3V it's 3.3*30=100Watt
And for the 5V it's 5*20=100Watt.

Isn't that a bit overkill? I mean the ratio is quite a big number: 5:2. Shouldn't they be more equal?

P.S. Just by checking those numbers 100+100+492=692Watt. How is it possible that a 550watt PSU gives around 700watt? :P

---

### Post by cascade9 on 2010-10-12
> **Pithikos said:**
> Thanks for your reply.
Well I was thinking about CMPSU-550VX 550W from Corsair which has these main specs:
+3.3V@30A, +5V@20A, +12V@41A

So for the 12V rail it's 12*41=492Watt
For the 3.3V it's 3.3*30=100Watt
And for the 5V it's 5*20=100Watt.

Isn't that a bit overkill? I mean the ratio is quite a big number: 5:2. Shouldn't they be more equal?

P.S. Just by checking those numbers 100+100+492=692Watt. How is it possible that a 550watt PSU gives around 700watt? :P

IIRC with corsair (and a lot of other manufacturers) the 3.3v and 5v rails are conencted, so you cant push max voltage though both of them at once (which is why for the 550, corsair has 3.3v @ 30a, 5v @ 28a but together they are limited to 140watts- 

[http://www.corsair.com/products/vx/default.aspx](http://www.corsair.com/products/vx/default.aspx)

They shouldn't be 'more equal' as newer systems pull almost all the power they need from the 12v rail. Which is part of why running older power supplies can be an issue on newer systems, they might be rated for XXX watts but compared to modern power supply of the same XXX watage, the 3.3v and 5v rails will have more amps, and the 12v rail less amps ;)

---

