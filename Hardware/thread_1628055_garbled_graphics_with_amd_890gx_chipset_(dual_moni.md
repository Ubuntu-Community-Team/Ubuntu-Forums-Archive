---
title: "garbled graphics with amd 890gx chipset (dual monitor)"
date: 2010-11-22
forum: Hardware
---

### Post by ampetrosillo on 2010-11-22
I have the following hardware configuration:

ASUS M4A89GTD PRO/USB3 with ATI Radeon HD 4290 integrated graphics
AMD Phenom X4 955 (3.2GHz)
4 GB RAM DDR3/1600
Western Digital 1TB 7200rpm 64MB cache
ASUS PCI-G31 wireless card

I have a dual monitor configuration, a 22" through the DVI-D port and a 17" through the D-Sub/VGA port.

When I first logged in Ubuntu 10.10, I had a low resolution on my primary display, and I think I was using the community drivers for my graphics adapter.
I installed the fglrx drivers from the "Restricted Drivers" tool, and when I logged in, after the reboot, graphics was poor, completely garbled with horizontal lines everywhere. In fact, it was impossible to read the menus. I tried installing the drivers from the ATI official website and it was even worse, X wouldn't start with something like "incompatible module" as an error message somewhere.

What to do? I thought my motherboard was fully supported in Ubuntu.

---

### Post by typhoon_tip on 2010-11-22
Ciao,

You can't install ATI driver (.run file) directly, by executing the installer, I did the same thing and miserably fail with random errors from time to time (even cannot boot sometimes).

Follow very clearly those instructions (especially see the bottom notes first !):
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

Especially read the section "Before you start" and then you can follow the procedure for "Updating the driver".

The first sentence is:
> DO NOT try to install a new version over an old one.

Hope it helps, good luck !

EDIT: I checked and the driver is the same as for my ATI card, you should get around it too.

---

### Post by ampetrosillo on 2010-11-23
Ok, I reinstalled everything, I'm with the restricted drivers supplied by Canonical, they kind of work, there are only some small glitches during login (although I can't even see the login dialog, I just follow the procedure by heart), but if I can fix that as well it would be great, as I'd like to have a flawless Ubuntu system :D

Would I have any luck with the manually installed drivers?

---

### Post by Fafler on 2010-11-23
You really should stick with the drivers from the repository. Manually installed drivers tend to break from time to time when the rest of the system is upgraded.

---

### Post by Kir_B on 2010-12-18
Same exact issue here.

It's a new computer that's running a fresh install of lucid 10.04.1 (maintenance release). 

Proprietary drivers are installed and come with a very pleasantly designed watermark, which says "AMD Unsupported hardware" and is annoyingly located on the bottom right of my desktop. There appears to be no way to disable the watermark. 

The other graphics issues described by the OP (original poster), are also being experienced, along with frequent lockups/freezing when viewing videos (hockey games) in full screen mode (frequent = 6 times in two and a half hours).

Anyone figure out a way to get these issues fixed?

Do the drivers from the AMD website rectify any of these issues, or do they just complicate things further?

Thanks. Kirby

P.S. 
_**Hardware:**_
Motherboard: Asus M4A89GTD PRO/USB3  
Graphics: ATI Radeon HD 4290 onboard graphics
CPU: AMD Phenom x6 1055t
RAM: gskill - 4 GB RAM DDR3/1600

---

