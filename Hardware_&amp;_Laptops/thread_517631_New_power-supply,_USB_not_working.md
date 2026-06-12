---
title: "New power-supply, USB not working"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2007-08-04
I recently grabbed a new power-supply, its a higher wattage than the unit it is replacing (which is dead). 

Everything works great except USB. Devices don't turn on when plugged in USB, including keyboard, webcam, etc.
I'm sure everything is properly hooked up, but there must be a reason USB specifically is not getting power. 

Is there typically BIOS problems when installing a new power-supply? Could that be the problem? Any ideas?

---

### Post by tgalati4 on 2007-08-04
What is the motherboard chipset?  What is the machine brand?

It's possible that the southbridge chip took a hit when the power supply let go.  It's also possible that the southbridge chip shorted causing the the power supply to crap out.  Either way, you may have lost USB capability.

Sometimes you may have luck removing the motherboard battery, shorting the CMOS pins (from 1-2 to 2-3 or vice versa) and reinstalling the battery and rebooting.

I have an eMachines carcass that someone gave me that blew a southbridge chip.  A google search shows that this is a common problem.

---

### Post by nalmeth on 2007-08-05
Hey, thanks for your thoughts! 
I have a Gigabyte 915 Series motherboard
Intel 915GL Express Chipset

I hope the southbridge isn't shorted like you suggest, wouldn't I have to buy a new motherboard to use USB if that is the case? 
I'll try the battery trick to reset the BIOS, and if that doesn't do it, start considering the shorted southbridge


Thanks for the advice

---

### Post by tgalati4 on 2007-08-05
If you read the specifications for either the north or southbridge chip, you will come away amazed that they work at all.  With all of the functions crammed into one chip, the voltage specifications have become narrow.  Running a few tenths of a volt high or low can fry the chip, resulting in loss of some functions or (at worst) a frozen motherboard.

Normally the southbridge will dissipate a couple of watts.  (Not the graphics chip, that is usually part of the northbridge).  It will feel warm, but not hot to the touch.  Anything hotter (as in you can't keep your finger on it) would indicate a higher heat dissipation (perhaps 15 watts).  This would indicate burned transistors.  I've seen blisters on some southbridge chips--not a good sign.  Dig out flashlight and magnifier and check the chip for surface defects and heat discolorations.

Because USB encounters all kinds of devices, it's not surprising that a static jolt or an overcurrent could fry that part of the southbridge.  Some boards have separate USB controllers, you will have to do some research.  Any chip that's super hot without a heat sink could be toast.

Another thing to check (if you are careful) is to take a voltmeter and measure the outside pins of the USB socket.  You should get 5VDC on the button.  It's possible that the power circuitry to the USB is fried.  If you are not getting voltage, then check the motherboard traces for a burned, surface-mount fuse.  If that is blown, then you can repair with with a pico-fuse (~1 amp).  A P4 board that I am looking at has a 6V, 1.1 amp surface-mount fuse and buffer capacitor (470 microFarad) for each USB port.  If it's blown, it would look burned, but you can test continuity with a meter.

Good luck.

---

