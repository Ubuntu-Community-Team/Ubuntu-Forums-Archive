---
title: "new build, computer won't turn on"
date: 2008-06-10
forum: Hardware
---

### Post by pytheas22 on 2008-06-10
This question isn't really specific to Ubuntu, but I'm hoping someone can point me in the right direction.

I'm building a new machine with a Core 2 Duo processor, a PC Chips P17G/1333 motherboard and a 300W power supply.  Right now I have just those things connected, along with a stick of RAM, as I'm just trying to make sure that everything works before I attach the rest of my devices.

If I plug in just the 24-pin power connector, the system fan and the CPU fan both spin up and stay on until I cut the power, but nothing else happens--no video, no beeps, nothing at all.  I figured that this was because the BIOS wouldn't run until the auxiliary power connector is also plugged in.

However when I plug the auxiliary connector in and jump the power switch, the CPU fan and the system fan sputter for half a second and then stop, and nothing else happens.  I've tried it half a dozen times with the same behavior.

I tried resetting the CMOS and reseating the RAM and power connectors, but it made no difference.  I don't know where to look next.  I'm not an expert on building machines--this is only my second--but I'm hoping that I'm just missing something and that there's not a problem with the motherboard or CPU.

The CPU bus speed is lower than the maximum supported by the motherboard; that shouldn't matter, right?

I'm very grateful for any suggestions on what I could try next.

---

### Post by logos34 on 2008-06-10
if it was the ram (incompatible specs/brand, or not seated properly) you'd hear beeps (but if your board is like mine there's a tiny speaker you have to plug into a header).

maybe the board does not support that particular C2duo model number?  

your board bus speed should always be equalt to or higher than processor (not the other way round).  so you're fine there

---

### Post by stchman on 2008-06-10
> **pytheas22 said:**
> This question isn't really specific to Ubuntu, but I'm hoping someone can point me in the right direction.

I'm building a new machine with a Core 2 Duo processor, a PC Chips P17G/1333 motherboard and a 300W power supply.  Right now I have just those things connected, along with a stick of RAM, as I'm just trying to make sure that everything works before I attach the rest of my devices.

If I plug in just the 24-pin power connector, the system fan and the CPU fan both spin up and stay on until I cut the power, but nothing else happens--no video, no beeps, nothing at all.  I figured that this was because the BIOS wouldn't run until the auxiliary power connector is also plugged in.

However when I plug the auxiliary connector in and jump the power switch, the CPU fan and the system fan sputter for half a second and then stop, and nothing else happens.  I've tried it half a dozen times with the same behavior.

I tried resetting the CMOS and reseating the RAM and power connectors, but it made no difference.  I don't know where to look next.  I'm not an expert on building machines--this is only my second--but I'm hoping that I'm just missing something and that there's not a problem with the motherboard or CPU.

The CPU bus speed is lower than the maximum supported by the motherboard; that shouldn't matter, right?

I'm very grateful for any suggestions on what I could try next.

There should be a second 4 pin power cord that needs to be plugged into the mobo.

Also a 300W supply is not going to cut it.  The proc takes about 95W by itself.  I would recommend a 500W supply minimum.  This is especially true if you get a higher end video card for gaming.

---

### Post by pytheas22 on 2008-06-10
I figured it out.  The psu apparently has two square four-pin connectors and I had the wrong one plugged in, I guess.  Plugging in the other one (which was buried between the other power wires) makes it boot and run BIOS.

I'm only going to be using onboard Intel video so I think 300W will be fine for power.  I built a very similar system last summer and it runs great with 300W.  I have the machines on all the time and like to keep electricity consumption down.

Thank you both for the responses, and sorry for not noticing my error before starting a thread.

---

### Post by logos34 on 2008-06-10
> **stchman said:**
> There should be a second 4 pin power cord that needs to be plugged into the mobo.

Looks like you hit the nail right on the head.  

good job

---

### Post by stchman on 2008-06-10
> **logos34 said:**
> Looks like you hit the nail right on the head.  

good job

I have had this happen too many times so it is with me forever.

Thanks.

---

