---
title: "Laptop Heat Issue"
date: 2008-10-31
forum: Hardware
---

### Post by xrecar on 2008-10-31
I have a question. Since I Installed Intrepid on my Compaq Presario CQ50-115NR I've noticed that my laptop doesn't heat up as it does with vista, It stays cooler for a longer time. So I was wondering if it has to do with the way ubuntu manages resources, I'm really guessing it is, but I would like a more detailed explanation if possible. That way I have another reason to participate (and bash windows :P) on a vista vs ubuntu discussion.

---

### Post by ddrichardson on 2008-11-01
This is purely conjecture without running objective tests on either OS installed on the same machine but I find that Vista has made a lot of changes which haven't been caught up with by develpers yet which seem to lead to high processor usage in almost every application.

Power management is for the most part configured by the manufacturer in their BIOS and firmware implementations so its most likely a combination of scheduling and resource management. 

Vista also hass some odd priorities (such as the network speed being dropped for multimedia playback, although that may have been patched in SP1) and the graphic effects are very resource hungry.

That said I would suggest that the biggest culprit is every damn installed application hogging resources at boot by preloading portions of its code. Try looking at the running processes in Vista when its doing nothing and looking at the number running in Linux, its quite surprising.

Vista bashing is a popular pastime but in al honesty once 3rd party developers produce applications fully compliant with the new security model I actually think its a step in the right direction for MS. Yes I know they're monopolistic and the system is bloated, etc but these arguments were all levelled at Windows XP which there are now a number of peopling hanging onto with white knuckles.

---

### Post by Bablefish on 2008-11-01
This is an easy solve, just go down to your local place that sells computers, or at least supplies and find a laptop cooling pad. They usually go for around $20 and are USB powered.

---

### Post by ddrichardson on 2008-11-01
> **Bablefish said:**
> This is an easy solve, just go down to your local place that sells computers, or at least supplies and find a laptop cooling pad. They usually go for around $20 and are USB powered.
He asked why it happens in Vista and not in Ubuntu, he already found the solution - run Ubuntu!:lolflag:

---

### Post by xrecar on 2008-11-03
Wow, Thankyou soooo much ddrichardson, that's the type of answer I wanted, an impartial one with the pros and cons about it for windows too. I learned something new today :D 

I also noticed last night that in about 3 hours ubuntu doesn't get to the level of heat that vista does in 45 minutes!, that said because I was recording a live DJ session on my laptop directly from the mixer with audacity and I even showed off ubuntu to some friend while recording and using the eyecandy (compiz' desktop wall, etc...) and seriously, It didn't heat as vista does in 45mins.. I really think HP should follow Dell's steps and start delivering ubuntu on their Desktops/Laptops.

Anyways, ddrichardson and bablefish, thanks sooo much for the answers!

---

### Post by ddrichardson on 2008-11-03
Glad it helps. For what it's worth, I've always found HP support to be very helpful but quite reluctant to support or be seen to support Linux - whether that's a policy I don't know and your mileage may vary.

HP also tends to have quite aggressive power management in firmware. They also release BIOS updates like there's no tomorrow, my TX1250 has had several this year and all have been aimed at power management.

---

### Post by xrecar on 2008-11-03
Oh, didn't know those details. Well, in my case I don't recall a bios update yet. I have an HP Compaq Presario CQ50-115NR and I really like it a lot, I also love to see ubuntu running on it. Again, thanks a lot for the info :D... you rock!

---

