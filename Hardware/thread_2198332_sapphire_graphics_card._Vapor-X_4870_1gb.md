---
title: "sapphire graphics card. Vapor-X 4870 1gb"
date: 2014-01-08
forum: Hardware
---

### Post by johndowling01 on 2014-01-08
Hi Guys, I bought this card a while ago now it works great on my windows boot partition but the ubuntu partition the CPU goes through the roof when just watching a simple video.

I assume that this would be the driver but this is my first linux machine so unable to verify. Is there a driver for this type of card. I have trawled the manufacturers site and google but no joy as of yet.

I dont want to buy a card for the sake of it.

Many thanks

John

---

### Post by mastablasta on 2014-01-08
there is a driver and you are already it :-)

i take itthis is actually radeon 4870? if so you will be able to get proprietary AMD driver only with version 12.04 (not with 12.04.2 or.3). just search for additional drivers in the OS and they will pop out. now if you ahve a newer version then you are out of luck. you could only try xorg edgers PPA which should get you newer opensoruce driver.

---

### Post by Yellow Pasque on 2014-01-09
I highly recommend this PPA: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
It will give you VDPAU video acceleration to take the load off the CPU. It works pretty well on my 4550, and the 4870 has a lot more shader power (shaders are used for open-source VDPAU). Unfortunately, the PPA is only available for Ubuntu 13.10/Saucy.

---

### Post by mastablasta on 2014-01-10
one can only wonder why AMD can't do this what these good poeple do in ther PPA.

i mean legacy - fine - no new features and such but at leats make it work propperly with newer kernels or help more with FOSS drivers.

---

