---
title: "Computer dead after power failures"
date: 2010-08-06
forum: Hardware
---

### Post by ratcheer on 2010-08-06
My house lost power twice in the past 15 hours, now my Linux PC will not power up. Nothing at all happens when I press the On switch. I have checked that power is available at the socket and that the computer's power cord is plugged in.

Where should I start troubleshooting? Computer's power supply, or something else?

Thanks,
Tim

---

### Post by endotherm on 2010-08-06
I would start by depriving it of power for about an hour, and trying again. also make sure that other devices on your outlet/powerstrip/ups are working (do the monitors power on for instance). 
if you aren't getting a bios screen at all, then the problem is either with your powersupply, or one of the core components (cpu, motherboard, or less likely, ram).

if you are still getting no response, open up the case, and you will find a 24pin cable running from the powersupply directly into the motherboard. unplug this cable (there is often a latch on one of the sides of the cable seat, so examine it before yanking), and plug it back in. i've had two PCs spring back to life over the last 10 years just by doing that. 

if you still aren't getting a startup signal, with the box plugged in, see if you notice any LEDS on the motherboard (or any other peripheral) that is on. are their any fans connected directly to the powersupply, that are running, while others connected to the motherboard are not? 

jsut some ideas. powerfail can do strange things to a box.

---

### Post by Yellow Pasque on 2010-08-06
Make sure the power switch on the PSU is on. Disconnect peripherals (cards, drives) and all but one stick of RAM (verify that stick with memtest in another computer if possible). Reset the CMOS on your mobo (usually with a jumper, read the manual).

If it still doesn't power, then you're down to the PSU, mobo, and CPU.

---

### Post by ratcheer on 2010-08-06
Thanks, guys. I will be trying your suggestions.

Tim

---

### Post by ryadav on 2010-08-06
google up your mobo spec, there might be a way to do a hard reset using jumper settings

---

### Post by epsolon77 on 2010-08-06
It sounds like a powersupply issue.  If you have a power supply tester you can check to make sure the power supply works and spins up using that.  Otherwise google how to short your power supply to force it on.  If memory serves there's a green wire you short to a black wire next to it, but google it to make sure.  If that doesn't work try a known good powersupply on your rig and see if it starts up.

---

### Post by ratcheer on 2010-08-06
endotherm, I don't understand it, either, but unplugging the machine for a while and plugging it back in did the trick. Lucid came up without so much as a disk check. I still need to reboot into Maverick.

Thank you so much. I never would have thought of that.

Also, I know it was getting power before I unplugged it, because the light was on the laser mouse and the network card light was on.

Tim

---

