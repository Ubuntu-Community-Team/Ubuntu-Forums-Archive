---
title: "Radeon or nVidia? That is the question. Need advice."
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Hopworks on 2007-12-20
I have two AGP cards available, but I'm not sure which one to use. If they were equally matched, the decision to go with the nVidia would be easy, but the Radeon I have is newer, and has more memory.

The two cards are;
Radeon 1650 Pro 512mb
nVidia 6600 GT 128mb

I read that Ubuntu Feisty 7.04 Server is much more friendly with nVidia hardware, so I'm inclined to go with the 6600 GT, but at 4x the memory on the Radeon, is it worth the hassle to try to use that card?

Any advice would be greatly appreciated.

The platform is P4 Prescott 3GHz 1mb cache, 2gb of DDR1. Mobo is the Asus P4P800 SE.

Thanks for your time!

---

### Post by nickoli_02 on 2007-12-20
Go with the Radeon, all you have to do is install the fglrx drivers. Your fresh install will probably start out broken as the default drivers wont work with ATI cards. You can switch to the vesa driver until you get fglrx installed. Instructions for installing fglrx in dapper and edgy are in my sig, you can probably find instructions for feisty pretty easily...

---

### Post by tech9 on 2007-12-20
> **Hopworks said:**
> I have two AGP cards available, but I'm not sure which one to use. If they were equally matched, the decision to go with the nVidia would be easy, but the Radeon I have is newer, and has more memory.

The two cards are;
Radeon 1650 Pro 512mb
nVidia 6600 GT 128mb

I read that Ubuntu Feisty 7.04 Server is much more friendly with nVidia hardware, so I'm inclined to go with the 6600 GT, but at 4x the memory on the Radeon, is it worth the hassle to try to use that card?

Any advice would be greatly appreciated.

The platform is P4 Prescott 3GHz 1mb cache, 2gb of DDR1. Mobo is the Asus P4P800 SE.

Thanks for your time!

[B]nVidia

I had a Radeon card that was not supported - bought a [/B]**nVidia had no problems**

---

### Post by Hopworks on 2007-12-20
> **nickoli_02 said:**
> Go with the Radeon, all you have to do is install the fglrx drivers. Your fresh install will probably start out broken as the default drivers wont work with ATI cards. You can switch to the vesa driver until you get fglrx installed. Instructions for installing fglrx in dapper and edgy are in my sig, you can probably find instructions for feisty pretty easily...

Thank you. I'll check that out. 

It's probably important to note that the card I don't choose will go into my better half's machine because her platform is AGP as well. I might put that 1650 in there so I don't have to change it later. I'm also seriously thinking hard on dual booting her machine so she can get a little exposure to Ubuntu Feisty, so that info you gave me will help. Thank you!

My 8800 GT is about a week or two away, and when I get it, it goes in my Core 2 Duo, and the 8600 GT in there now will go into the Linux box.

---

### Post by Linteg on 2007-12-20
A lot has happened with amd/ati and linux this year, their new drivers series are better (and support aiglx nowadays, although it's a bit buggy afaik), and they've released/promised to release specs so oss drivers can be made (the radeonHD project.)
In your system I'd say the bottleneck would be the processor anyway, so choose whichever you feel like, the drivers will probably be on par soon.

---

### Post by Hopworks on 2007-12-20
So, say I put the 6600 GT in, should I have to do anything extra? There is a nVidia TI 4200 in there now.

Thanks again for the advice.

---

### Post by Linteg on 2007-12-20
That depends, are you using the nv or any of the proprietary nvidia or nvidia-legacy drivers? The 6600gt uses the "nvidia" driver, but i think the ti4200 uses the nvidia-legacy one (if there is no nvidia-legacy driver in feisty, just ignore this). If you want to be on the safe side, you could edit xorg.conf and change the driver to vesa, that would make any card work (with abysmal performance, but it would at least work), and then you could go from there to install/set up the nvidia drivers.

---

### Post by ronacc on 2007-12-20
I would definately go with the nvidia card ati is geting more linux friendly since the amd buyout but IMHO is not there quite yet.  and a bit of heresy that I will probably get flamed for but I use the propriatary nvidia driver IT JUST WORKS .

---

