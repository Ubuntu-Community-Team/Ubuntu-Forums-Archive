---
title: "USB power stays on after shutdown"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Paki on 2007-01-21
The power to my USB ports stays on after shutting down my PC. Specifically, the LEDs on my keyboard, mouse, and flash memory drive remain illuminated.

I do not have this problem with Windows, FreeBSD, or K/Ubuntu releases through 5.10. I do think it is a problem with the Linux kernel, because it occurs with all Linux operating systems using kernel 2.13 or later (whereas all systems using kernel 2.12 or prior work fine).

The problem is also raised in the following threads, but no solutions are offered:
[http://www.ubuntuforums.org/showthread.php?t=186779](http://www.ubuntuforums.org/showthread.php?t=186779)
[http://www.ubuntuforums.org/showthread.php?t=206385](http://www.ubuntuforums.org/showthread.php?t=206385)

My PC's motherboard is an ASUS A7N8X-VM.

My thanks for any suggestions.

It would be helpful for filing a bug report if others having the same problem could specify their PCs or motherboards. My thanks for that information, too.

---

### Post by buddhaguy on 2007-02-06
Same happens on mine, Shuttle SN25P v2 with Y Bios on Dapper with 2.6.15-27-386.
It does come in handy for charging the palm though :) 

Guy

---

### Post by sultanoswing on 2007-02-06
Same here.

Gigabyte K8NS rev 2.x (socket 754, nForce3)

---

### Post by buddhaguy on 2007-03-03
Updated to edgy and still a problem.

Any news?

---

### Post by armalite on 2007-03-19
Just to say "same for me".

I have an Asus P5N32-SLI SE Deluxe motherboard (nforce4, socket 775) and it is the same in Edgy & Feisty.

I hope there will be soon a solution to this... i don't want to shutdown the pc with the rear switch just to shutdown the leds on mouse and card reader.

There are no jumpers on motherboard to cut usb power... this has to be done software.

---

### Post by Erlander on 2007-03-19
For me it is a hardware matter not operating system.  One pc is ok the other maintains the usb power.

I think it is from bios and there may even be a setting to turn it off.

Rob

---

### Post by armalite on 2007-03-19
> **Erlander said:**
> For me it is a hardware matter not operating system.  One pc is ok the other maintains the usb power.


Other operating systems do shutdown properly usb ports, this lead me to think that it isn't an hardware matter. I've already checked in bios, i'll redo that in very near future.

The real strange thing is that usbcore module is always busy and I can't rmmod it. If I only could unload usbcore module... maybe the lights will switch off.

---

### Post by Erlander on 2007-03-19
I base the hardware idea on the fact that the Gigabyte motherboard in my Ubuntu pc did this previously when used in a Windows pc but the Asus motherboard I put in that pc does shut the power down.

It may be related to "Wake Up On USB" or similar in the power management section of bios.

Rob

---

