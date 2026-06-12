---
title: "finding a power adapter for external hard drive"
date: 2008-09-19
forum: Hardware
---

### Post by pytheas22 on 2008-09-19
This question admittedly has nothing to do with Ubuntu, but I'm hoping someone can provide some help nonetheless.

I have a SimpleTech Pininfarina 320 GB external hard drive.  I lost the power adapter a while ago, which makes the drive useless.  I don't want the drive to go to waste, so I'm hoping to purchase a new power adapter for it.  There are plenty of DC adapters available on the Internet for around five dollars.

I don't have much information about what kind of adapter it takes, however, and am not sure if I need a certain kind of adapter or if any DC adapter would work.  I can't seem to find anything about this on the Internet, and on the drive itself it just says 'DC' below the power jack (no voltage mentioned).

Is there any way to find out exactly which kind of adapter I need?  Or can I buy any DC power adapter that will fit into the hole (whose diameter I guess I could just measure with a ruler)?  Does the voltage of the adapter matter?  I don't know much about these kinds of things and am hoping for some guidance.

And I don't suppose there's a way to get the drive to run off of the power provided via the USB cable, is there?

I'd hate to throw a hundred dollars out the window just because I lost the power adapter for this thing, so thanks in advance for any suggestions.

---

### Post by IntuitiveNipple on 2008-09-19
If it's USB then the power will be 5 volts DC. For a disk drive a PSU that can deliver 1 amp should easily be sufficient. The rated maximum for port-powered devices is 500mA (0.5 amps).

Almost any 5V DC PSU will do if it is intended for USB devices. The thing to sort out is the plug matching the socket - it is easy to cut the plug off it it doesn't fit and solder on one that does (remember that positive volts are in the center and ground is the outer).

I regularly chop PSUs up for customised USB cases and so forth.

---

### Post by pytheas22 on 2008-09-19
Thanks, that helps a lot.  Just a follow-up question though: is there no standardization to the plug diameter sizes?  Are they all just random?  I was assuming (hoping) they came in standard sizes, like 2mm or 3mm or something, that I could match to the input on my drive.

If the one on the adapter I buy doesn't fit, how can I find one that will (is that what you mean by soldering one on)?

---

### Post by IntuitiveNipple on 2008-09-19
You wouldn't believe what a mess the barrel-connector sector is! They have differing internal and external diameters and some only vary by 1/10th millimetre.

I built a self-powered aluminium flight-case that holds 8 USB devices and it has several devices powered directly from a battery (7-port hub, disk-drive, card-reader, PDA, USB charging socket, barrel-socket), plus two internal power supplies (7.2V battery charger and 5V 6A DC USB power) and every one had a slightly different size :mad:

I spent ages measuring with a micrometer to be sure I got the correct plugs for the power distribution circuit.

---

### Post by cariboo on 2008-09-19
You'll need a twelve volt power supply, the enclosure usally has a voltage regulator to drop the voltage down to 5 volts, as a hard drive meeds both 12 and 5 volts to run. Unfortunately, the plugs are not standard, so you prbably will have to do some circuit tracing to find which terminal is which. the other solution is to crack open the case and just use a drive connector from an old XT/AT power supply. You should be able to find one for next to nothing as they aren't good for anything but old XT/AT computers.

Jim

---

### Post by IntuitiveNipple on 2008-09-19
If it is this device then it claims not to need an external power supply.

[SimpleTech 320GB SimpleDrive Portable Hard Drive](http://www.simpletech.com/parts/spu25320.htm)

---

### Post by pytheas22 on 2008-09-19
> If it is this device then it claims not to need an external power supply.

Yeah, that's the device and I read the manual available on that site, which does indeed say you can power it using the USB cable.  But that's not working for me, using the USB cable that shipped with the drive.  I emailed them to ask if the manual provides misinformation (I'm almost positive that my drive shipped with a power adapter, even though the manual says it's not included, so I don't know how accurate the rest of the manual is); hopefully they'll respond.

Thanks again for your responses.  I'm sure with that information I'll be able to figure this out.

In a worst case, as cariboo907 says, I can take the thing apart (unfortunately it doesn't look easy--no screws or anything--so I'll save that as a last resort).

---

### Post by IntuitiveNipple on 2008-09-19
Are you connecting it directly to a port on the PC, or via a hub? That can and does make a difference.

I had an issue with the Freecom external USB drive in the flight-case that was connected to the powered hub but would fall over.

Connected directly to the PC it worked perfectly.

Now it is back in the case and has its own power (as I described earlier) and works fine via the hub.

---

### Post by pytheas22 on 2008-09-19
It's connected directly to the front case USB port of my machine.  It's possible that the USB cable is bad (I know it worked before for data transfer but I guess the power cables in it could be shot)--I don't have another one around right now to test--but beyond that I'm not sure what could be wrong other than that the drive can't really be powered using a USB cable.

---

### Post by IntuitiveNipple on 2008-09-19
I just grabbed the [user guide PDF](http://www.simpletech.com/support/guides/user-guides/60000-00146-001.pdf) and it says:

> 
What You Should Have:

USB/AUX PWR cable

and later:
> 
DC-IN Jack
JackSocket for connecting an AC power adapter to
SimpleDrive.

and then:
> 
USB/AUX PWR Cable
Use this cable to connect SimpleDrive your
computer.
• Mini-B USB plug
   Connects to SimpleDrive to provide signal and
   USB bus power source to SimpleDrive.
• Type A USB plug (Power and signal)
   Connects to a USB port on your computer to provide
   signal and USB bus power source to SimpleDrive.
• Type A USB plug (Power only)
   Connects to a USB port on your computer to provide a
   secondary USB bus power source to SimpleDrive.

The illustration next to that shows a Y-cable with two type-A plugs, one of which is purely to draw power. That suggests the drive requires more than the 500mA per port that USB provides.

Later still:
> 
Connecting Secondary Power
SimpleDrive receives power through your computer’s USB port. If the port cannot
provide sufficient power to run the drive, connect SimpleDrive to your computer using both
USB plugs on the USB/AUX PWR cable.

and finally in the Specifications section at the end it says:
> 
Power USB bus-powered or 5 VDC, 1.0A external power adapter (not provided)

So, we're back to where I started. It needs a 5V 1A DC PSU :)

---

### Post by pytheas22 on 2008-09-20
I noticed the dual-head USB cord.  The strange thing is that my drive doesn't have the same ports at all as the one in the illustration, even though by all other indications it's the same model as that manual was written before, and it looks (same color and shape) like the one in the photo on the site.  I have one USB port on the left and a DC jack on the right--so USB/AUX won't work.  So I'm less and less inclined to believe that what that document applies to my device.

Perhaps they made more than one model of 320 gigabyte external hard drives, and mine is not the one for which the document was written, but the site doesn't make that clear.

Hopefully they'll just email me back by next week so that I can figure stuff out.

---

### Post by IntuitiveNipple on 2008-09-20
> **pytheas22 said:**
> I noticed the dual-head USB cord.  The strange thing is that my drive doesn't have the same ports at all as the one in the illustration, even though by all other indications it's the same model as that manual was written before, and it looks (same color and shape) like the one in the photo on the site.  I have one USB port on the left and a DC jack on the right--so USB/AUX won't work.  So I'm less and less inclined to believe that what that document applies to my device.
I think you might be confused here.

The Y-cable has a single type-B connector that connects to the drive. The two type-A plugs connect to the PC. There aren't two connections to the drive, all the power still goes in via the single type-B connection.

The DC jack is only used with an external PSU, in which case a regular USB cable can be used for data (type-B to type-A).

---

### Post by pytheas22 on 2008-09-20
> The Y-cable has a single type-B connector that connects to the drive. The two type-A plugs connect to the PC. There aren't two connections to the drive, all the power still goes in via the single type-B connection.

aha, I see.  That makes more sense; thanks for the clarification.  The drawing in the manual is still inaccurate--my USB-in port is on the left side, not the right.  And I'm pretty sure that the device never came with a USB/AUX cable.  But I'll try to get hold of one and see if the drive turns on that way.

---

### Post by IntuitiveNipple on 2008-09-20
> **pytheas22 said:**
> aha, I see.  That makes more sense; thanks for the clarification.  The drawing in the manual is still inaccurate--my USB-in port is on the left side, not the right.  And I'm pretty sure that the device never came with a USB/AUX cable.  But I'll try to get hold of one and see if the drive turns on that way.

You could make one relatively easily if you can wield a soldering iron.

Get a couple of type-A plugs and a type-B, then solder one type-A to the type-B using all four connections (+ve, data+ data-, -ve). For the 2nd type-A only solder +ve and -ve (pins 1 and 4) to the type-B. Mark this as power-only.

You can find pin-out diagrams for the connectors on wikipedia and many other sites (hint: google image search).

---

