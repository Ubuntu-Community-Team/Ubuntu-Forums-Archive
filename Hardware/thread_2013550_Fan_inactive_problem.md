---
title: "Fan inactive problem"
date: 2012-07-01
forum: Hardware
---

### Post by Bisneff on 2012-07-01
Hi guys!

I'm running psensor on my Ubuntu 12.04, cause I see that my laptop (Acer Extensa 5620Z with 2.5gb ram) warms up fast.  

By the way I notice that the fan starts to run just around 60°-65° C (core temperature is around 55-60). 

There is any way to make the fan run a bit earlier?  

If possible I'm looking for something that make the fan more "active" when the pc is plugged in, but "save power" when I'm using battery.

I have Jupiter too, but even in power saving mode, nothing changes.


Thank You!

EDIT: I make a try with fancontrol, but my output on pwmconfig is: /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

---

### Post by Bisneff on 2012-07-03
Up. Please someone help me :)

---

### Post by Redblade20XX on 2012-07-03
I believe that the fan is controlled by the BIOS so maybe that's where you should look at. See if there is an advance BIOS menu with any fan control options or thermal trip point options. If not, you'll probably will have to do some hacking yourself, if it really bothers you.

-Red

---

### Post by jonnyboysmithy on 2012-07-03
You could also check for a bios update..

---

### Post by jonnyboysmithy on 2012-07-04
Keep bumping this thread around.. Maybe you should also do some googling. 
Check out a package called thinkpad, its aimed at manually configuring fans speeds.
Just search for "fan" (without quotes) in ubuntu software centre or synaptic package manager.

---

