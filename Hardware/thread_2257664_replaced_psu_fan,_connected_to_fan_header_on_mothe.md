---
title: "replaced psu fan, connected to fan header on motherboard"
date: 2014-12-21
forum: Hardware
---

### Post by jedispork on 2014-12-21
The fan on my 650 watt corsair psu started making some bad noises so I ordered a noctua fan to replace it. I switched the plugs from the old fan (two pin power only) and I'm not sure if it worked properly. I know some newer psu's will shut down the fan at times. When starting the machine the notua fan would spin up then stop. I've heard this was a signature of corsair supplies to verify that your fan was still working but it doesn't seem to spin up at all after that. Maybe the fan header in the psu is not be compatible with the electronics in the fan. 

Anyway hopefully I didn't stress any compnents in my psu while trying to get the fan to spin up. I put the default connectors back on and routed the wires out of the psu and connected it to the system fan port on my mobo. At full speed even a notua fan makes a lot of noise so I used the smart fan control in the bios. I need to check the rpm of the fan but its still moving a lot of air this way and the noise is tolerable. My psu is already over sized for my system so I'm hoping this will be ok. I don't have any case fans since my basic setup seems to run cool enough without them. 

Do you think I will have any issues running the fan like this? It should at least speed up when things get warm? 

thanks

---

### Post by weatherman2 on 2014-12-21
Yes, the fan should come on when the PSU warms up but may not right away.

Is the new fan also a 2-pin?  A 3-pin fan should work though if you connect to the right pins - the 3rd pin is for sensing the rotation speed, not controlling the speed.  A 4-pin fan can be controlled to slow it down.

---

### Post by jedispork on 2014-12-21
the noctua is a 4 pin fan. I cut off the connector and swapped it with the old psu 2 pin fan connector. However it didn't seem to be working so I switched it back to the 4 - pin and hooked it up to the system fan header on the mobo. With smart fan control enabled in the bios the fan doesn't run at full speed which is what I wanted. I'm hoping this way it may run somewhat similar to being controlled by the psu. Increased power - heat - crank up system fan which is the psu fan now.

---

### Post by tgalati4 on 2014-12-21
That is a clever way to work around the problem.  The other way is to wire up some switches on your case to power the fan with 5VDC, 7VDC (12VDC-5VDC), and 12VDC.  That gives you OFF, low speed, medium speed, and high speed.  Then manually switch the fan as your needs require.  You can put temperature monitors on your panel with temperature limits that give pop-ups when temperatures exceed a certain level.  CPU temperature is roughly correlated with power draw.  After all, all CPU's are only 1% efficient, so 99% of the CPU power is eventually given off as heat.  So when the CPU gets hot, the power draw is increased.  You can monitor your GPU temperatures as well (on some graphics cards).

Understand that PSU components get hot at idle as well, since the power regulation is throwing off power that is not used.  Having an oversized PSU can contribute to this.  Better-quality PSU's (those with near 100% power factor) have better power regulation and are less wasteful, and thus need less cooling.  To be conservative, you want your PSU fan running all the time at low speed.  You can't overcool a PSU.  The extra air will keep your case internals cooler as well.  So find a voltage that runs your fan reasonably fast, yet quiet.  That will typically be 7VDC, but your testing will dictate.

There may be a circuit to convert a 2-pin to 4-pin fan connection.  For that, you will have to do a web search.

---

### Post by Yellow Pasque on 2014-12-21
I'm confused as to why you're hooking up the PSU fan to the mobo. I've seen some power supplies that have an extra connecter to a mobo fan header to allow you to monitor the RPM, but the fan itself is still connected/powered inside the PSU.

---

### Post by jedispork on 2014-12-21
> **Temüjin said:**
> I'm confused as to why you're hooking up the PSU fan to the mobo.

Because my psu fan was failing and for whatever reason the replacement would not power properly from the internal header in the psu

thanks to everyone for all of the suggestions

---

### Post by weatherman2 on 2014-12-21
Sounds dangerous to me.  The PSU should control the fan speed based on its needs, not the motherboard.  The motherboard has no idea how hot the PSU is or whether the fan should be coming on.

---

