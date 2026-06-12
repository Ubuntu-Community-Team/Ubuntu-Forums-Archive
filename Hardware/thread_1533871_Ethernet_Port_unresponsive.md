---
title: "Ethernet Port unresponsive"
date: 2010-07-18
forum: Hardware
---

### Post by Rowen91 on 2010-07-18
I'm having an issue with my Ethernet port, when I plug in a working cable to it no lights flash on nor even blink. I look at my Wired Networks list and it says Disabled, using a USB Wireless thumb drive to connect. Now, if that was all I would realize that soemthing might have happened to the port, but when I have the wire connected to a router and to the port on starting up my computer, it will flash both the orange and green lights for a moment. It's an onboard Nividia Ethernet port if that helps some.

---

### Post by IcarusR on 2010-07-18
So with a cable plugged into the ethernet port & nothing the other end no lights. 
But when plugged into router & ethernet port lights work.
Is that not normal ??

Is wired network working ?

---

### Post by Rowen91 on 2010-07-19
No, in the initial stages of boot up wither there is a cable plugged in or not, a light flashes for a moment. Then even if a cable is pluged in after that, the lights do not come on and it says my mired networks are disabled. I never touched the enable or disable wired networks, I think, and so thats why I'm asking.

---

### Post by pricetech on 2010-07-19
If the lights aren't even flashing, that sounds like a hardware problem.

Known good cable ??  Straight Through and not Crossover ??

Tried another port on the router ??

---

### Post by Iowan on 2010-07-19
Hmmm... I've seen a similar thread (over in Networking & Wireless forum). Does the wired interface show up in (from a terminal) **ifconfig -a**?
What does **sudo lshw -C network** reveal?

---

### Post by Rowen91 on 2010-07-21
Ok, so I got some new info about what happend. Aperntly there was a storm wile I was away, and a lighting bolt struck not even 50 feet from ware my computer is located, this is just a guess, so I think that strike shorted out the port on it rendering it useless. 

Any body know of any good cheap network cards?

---

