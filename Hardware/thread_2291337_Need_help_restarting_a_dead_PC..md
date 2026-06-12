---
title: "Need help restarting a dead PC."
date: 2015-08-19
forum: Hardware
---

### Post by dtree46 on 2015-08-19
Using Ubuntu 14.04LTS. 64 bit, 2g mem, 64g hd.

What happened: trying to increase ram to 16g.
         What ram was installed: 2GB 204 - PIN DDR3 256MX64. See attached photos.
         Tried to install: 2x8gb PC3-8500 DDR3 1066 MHZ 140115
                When turning PC on, the power button lights up but nothing else happens.
                Monitor remains black. Not even a start screen.
                Same result with a different monitor.

Written on the main board next to two ram slots is: SODIMM DDR3 1066
According to the manual, the unit will accept up to 16gb.

Where does one begin in trying to solve this?
Any help appreciated.

dlw

---

### Post by weatherman2 on 2015-08-19
So is the PC "dead" with the old RAM too?

If not - sounds like the RAM simply isn't compatible with your motherboard.  Just because in theory it will accept some maximum size of RAM doesn't mean the exact RAM you've plugged into the RAM slots will work.  Very common problem.  Since we don't know what motherboard you have, it's difficult for anyone else to verify it.

Sometimes the motherboard or computer manufacturer will list exact types of RAM that have been tested on your motherboard on their website.

You might make sure the motherboard's BIOS/firmware is updated to the latest from manufacturer.  Sometimes a newer BIOS will recognize more RAM.

---

### Post by dtree46 on 2015-08-19
Thanks for replying.

Dead with old ram also.
Can not get to bios.

---

### Post by dino99 on 2015-08-19
test step by step: dont set all the ram sticks at once; read the mobo doc about ram; check the ram voltage (new sticks, the old ones: they need to have same voltage, cas; idealy only set the same brand/model), check the ram bios settings (maybe you need to set its settings manually if the bios is poor)

---

### Post by weatherman2 on 2015-08-19
OK, so to be clear: the PC worked fine until you tried to upgrade the RAM.

Now, it won't power up with either the old RAM or the new RAM?

The first step: go back to the old RAM.  Be certain the RAM is plugged in correctly, firmly in and each of the clips on the sides of the RAM stick are pushed IN to secure the RAM.  If they aren't clipped completely in, the RAM may not be firmly in the DIMM socket.

It's possible that, in the process of getting in there, you zapped the motherboard.  (ESD - Electrostatic Discharge - is a very real thing; if you have any sort of static charge and touch any component on the motherboard, you could zap it.)  I've not done this in recent memory, and I've long since stopped wearing a ground strap, but it can still happen. (I'm usually careful about not touching the metal connectors especially on any computer component.)

Or, could be the motherboard itself was marginal before and about to fail.  Are any capacitors bubbling?  Do a web search for "blown caps" to see what I mean.

You should also double check all your motherboard connections, of course.  Make sure all power supply connectors are firmly connected to the motherboard.

You might also try removing ALL RAM and powering on and see what happens.  (It won't boot up that way of course, but it might beep or something it didn't do before.)  Then, power off and plug the RAM back in.

Finally, try unplugging from power and removing the CMOS battery for about 60 seconds, then plugging it back in.

Don't even bother with the new RAM until you can get it working with the old RAM.  Keep in mind that motherboards do fail, though, so a dead motherboard is not beyond possibility.

Good luck!

---

### Post by dtree46 on 2015-08-19
Now idea how or why... but, it's working again.
Will not accept any of the ram except the original 2gb. See attached photo.
I'd like to find 2x8gb to put in but so far not having any luck.
Is there any way -software- that will tell what ram it takes or what motherboard is in the thing.
The motherboard has no marking of any kind except where to attach things.

Thanks for the help and suggestions.
Maybe one or more of your suggestions did the trick.
I do not know. I'm just glad it's working again.
All my data is backup in three different off site places so that was never a problem.
But... a new motherboard would have been.
Thanks again.

dlw

---

### Post by dtree46 on 2015-08-19
Forgot photo.

---

### Post by weatherman2 on 2015-08-19
Type this command to find out more about the hardware:

```
sudo lshw
```

The motherboard info should be near the top.

---

### Post by dtree46 on 2015-08-19
Thanks for the info.
Lot of information there but still do not know for sure is it will take 16gb.
When I bought it the guy said it would.
Maybe with this information I can find out.

---

### Post by weatherman2 on 2015-08-19
If you can find a motherboard model number (?) from the lshw output, that might help.

---

### Post by dtree46 on 2015-08-19
lshw worked very well.
Having the model # of the motherboard I found out max memory is 4gb.
The person I bought it from assured me it could take up to 16gb.
I'm sending a message tonight asking for a full refund.
We'll see.

---

