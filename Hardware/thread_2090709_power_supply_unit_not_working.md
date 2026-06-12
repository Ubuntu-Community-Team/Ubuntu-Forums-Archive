---
title: "power supply unit not working"
date: 2012-12-03
forum: Hardware
---

### Post by Bigmon on 2012-12-03
Hi, wonder if anyone can help.

I have just upgraded my motherboard but can not get any power going to it. The psu is dead (just a faint clicking). I connected the psu to the old mobo and it works ok so it is not the psu.

As far as I can see I have connected the psu correctly to the mobo - using 24 pin connector and the ATX 12V. Has anyone any suggestions ?

The original mobo was a Gigabyte KV2 Lite and the new mobo is a Gigabyte GA-M57SLI-S4

Cheers.

---

### Post by Cheesemill on 2012-12-03
Have you connected your case power switch to the new motherboard correctly?

Also double check your motherboard manual for which connections have to be made to the power supply.

---

### Post by Bigmon on 2012-12-03
I have checked with the mobo's manual and I have connected the PSU correctly. I have checked the case power connector and system reset connector and they seem to be correct.

---

### Post by Cheesemill on 2012-12-03
Is the CPU installed correctly? I know some motherboards will refuse to power up the PSU fully if the CPU isn't installed.

---

### Post by Cheesemill on 2012-12-03
Also make sure you have attached the square 4-pin ATX connector, not just the rectangular 4-pin connector.

---

### Post by Bigmon on 2012-12-03
The CPU was already in the motherboard when i got it. All i did was put in the heatsink and fan. The CPU looked properly seated from what I could see.

---

### Post by Bigmon on 2012-12-03
I have attached the square four pin connector, but not the rectangular one. Is this one you are referring to, a bit similar to the four pin that comes off of the CPU heatsink and fan ? If this is the one, I cannot see where to connect it as the heatsink/fan is connected to the only connection I can see like that on the mobo ?

If you understand what I mean.

---

### Post by Cheesemill on 2012-12-03
I was thinking you might have used connectors 2 and 3 instead of 1 and 2, but you are correct (page 21 in your manual).

Also did you read this:
> If you use a 24-pin ATX power supply, please remove the small cover on the power connector on the motherboard before plugging in the power cord ; otherwise, please do not remove it.

---

### Post by Bigmon on 2012-12-03
Yes, I did read this, but did not really understand it ? Cannot see how you could plug in the power supply if there was a cover over it ?

---

### Post by Bigmon on 2012-12-03
If anyone else could suggest anything, it would be much appreciated !!

---

### Post by steeldriver on 2012-12-03
well I guess another possibility is that the PSU is not rated to deliver the current required by the new MB and its peripherals - and is shutting down to protect itself (overcurrent protection) - does the MB have a big graphics card plugged in to it or anything?

---

### Post by Bigmon on 2012-12-04
No, there is no graphics card in the mobo. The manual says that a psu of 400 w and upwards would be sufficient, and mine is 400.

---

### Post by Bigmon on 2012-12-06
I am still trying but to no avail. I took the mobo out of the case and tried to power it up this way, but nothing !! ( my other gigabyte mobo seems to power up with just the 24 pin and 12v in outside of the case ok )

I took the memory sticks out and the cpu and heat sink and tried the same process but also nothing. I put back the cpu etc and then tried it all again but still nothing happened.

The guy that I bought the mobo off of insists it was all ok. I am at a bit of a loose end. The only thing I can think of is what somebody mentioned and that 400w power supply is actually insufficient !!!

---

### Post by Bigmon on 2012-12-07
I got in touch with gigabyte and they suggested I do the following which solved the problem (although I did not attach the VGA card):

Hi,

1) Remove the M/B from the case.
2) Only install the basic components on the motherboard – CPU, CPU cooling fan, one memory module, VGA card (if there is no VGA onboard) and power supply.
3) Reset the CMOS once - Disconnect the power cord from the power supply & detach the CMOS battery for 5 minutes then put it back.
4) Connect the internal speaker.
5) Turn on the power to see your system can power up. (Connect only the power switch from the case to the M/B)

Thanks for all the help. !!!

---

