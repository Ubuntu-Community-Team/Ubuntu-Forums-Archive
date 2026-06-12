---
title: "thinkpad w500 high-pitched whine"
date: 2008-12-08
forum: Hardware
---

### Post by antmo on 2008-12-08
has anyone else with a new thinkpad noticed a high-pitched whine from the chipset?  it gets worse when running glxgears, so i assume it's the ati graphics card.  it is not the fan, since it doesn't correspond to cpu usage and/or fan speed.  it is always present, regardless of what apps are running, but just seems to be twice as loud with glxgears...

i have noticed that i also get this noise when booting windows, part way through the boot, but then it disappears once the desktop is up and doesn't return with anything i've tried thus far (including a number of graphics/opengl based benchmarking tools).

it seems like there's something that gets initialized in windows which silences the whining.

i've got the bios set to discrete graphics and disabled switching.

also, even though i know that glxgears is not a reliable benchmark, i do notice the fps performance i get fluctuates wildly...  at the default resolution, sometimes i get 6000+, sometimes i get less than 1000, and mostly i get 2500-3000...  i've tried a bunch of different things to try and re-create it, but the only consistency i notice is that it runs fastest the first time i run it after starting x, then it usually gets worse and then runs consistently about half as fast...

maybe it's just a driver issue?  perhaps ati will solve this?  mostly i'm just concerned about the whining, since it is both annoying and a very disconcerting sound, worse even than what i hear when windows boots...  i guess i'm a little concerned that the driver is damaging something in the chip.

thanks,
mjb

---

### Post by hardyn on 2008-12-08
Alot of my electronics do this, i understand its some highspeed switching going on.  (although i have always wondered how this works as sound is the displacement of air, and i don't see electronics displacing much air).

I think if you are using a ATI released driver that is not a beta you would be convered under warranty.  but i get a similar sound, a high pitched whine, when my computer is sleeping and the blue blinking LED that tells me it sleeping make noise when the led is on, and not when it is off.  it has worked fine for 3 years, i have resigned to the fact that my computer makes noise.

what about trying the radeon driver?  or the radionHD driver?

---

### Post by elektryk92 on 2009-01-06
I'm experiencing similar problem with my hp 6735s. After installing new ati driver high-pitched sound is heard from the inside of laptop. It is very irritating. It happens on 8.10. On 8.04 it worked fine with ati drivers. It must be combination kernel - ati driver. While i turn off ati driver it works fine, but i have no acceleration and compiz doesn't work - so it isn't solution. On the web i found out, that we are not alone, but there is no solution given. Maybe someone more advanced could help?

---

