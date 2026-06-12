---
title: "What hardware (or vendor) for SOHO Server?"
date: 2014-06-06
forum: Hardware
---

### Post by alanq2 on 2014-06-06
I need a SOHO server.
It seems a simple ask.
But every search I try turns up nothing matching my spec.
One problem is that if you search 'ECC' you get every result containing "non-ECC", "ECC No", and every other possible variation, which doesn't help.

I'm happy to build it myself, but pre-built has the advantage of a guarantee -- when it fails, someone else can trouble-shoot it :)

Hardware Spec:

[LIST=1]
[*]Small -- the S in SOHO 
[*]Quiet -- for the H in SOHO -- ideally passive cooling. 
[*]Room in the box for two hard discs (I plan RAID 1 -- short down-time if one fails, disc space is cheap) 
[*]ECC memory -- it will run 24/7. I can cope with a system crash, it's data integrity that's important. 
[*]AMD chipset/CPU (or VIA or ARM ?) -- for their better attitude towards GNU/Linux (even if this is past-tense, it beats WIntel). 
[*]One gigabit port will do, ideally two. 
[*]One or two USB -- ideally v3 but v2 will do. 
[/LIST]
 
Software Spec:
Ubuntu 14.04 server

Use:

[LIST=1]
[*]File server 
[*]Email server 
[*]Print server 
[/LIST]
 for two users.

I'm in the UK.

Any ideas much appreciated.
Thank you.
Alan

---

### Post by papibe on 2014-06-06
Hi alanq2. Welcome to the forum ):P

Have you considered a Ubuntu preinstalled server?

For instance a [System76 Eland Pedestal]("https://system76.com/servers/model/elav4") (they ship to the UK).

Hope it helps. Come here often and have fun.
Regards.

---

### Post by alanq2 on 2014-06-07
Thank you, Papibe

Yes, I did find System76.
Very nice looking machines.

Unfortunately:
[LIST]
[*]Over specced for what I need 
[*]Expensive -- especially with delivery over the pond on top 
[*]Long shipping means turn-around for any repairs will be longer 
[/LIST]

Apart from that it's great :)

I'm imagining a small, fanless machine -- maybe mini-itx -- but with ECC memory.
System on SSD, plus two cold-swap 1TB HD.
Software RAID 1.

---

