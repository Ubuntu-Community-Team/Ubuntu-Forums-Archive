---
title: "Acer Aspire 5515 shuts down from overheating, fan not working"
date: 2011-02-27
forum: Hardware
---

### Post by aceraspire5515guy on 2011-02-27
Hello,
I have an Acer Aspire 5515 laptop.
I am running Ubuntu 10.10.
My fan is not working, and the computer shuts down whenever it gets around 78 degrees C, (according to xSensors).
I never had this problem on 8.10.
Anyone know how to fix this?
Thanks.

---

### Post by skeilman on 2011-03-03
Hi. I have the same problem. My Acer's fan (aspire 5715Z) work fine on Win7 but don't work on Ubuntu (powerpack 2010.2). and comp just shutdown after 30 min of web browsing. Please anybody help!

---

### Post by upchucky on 2011-09-04
I just fixed a customer acer aspire 5720 that was shutting down on high temp. My fix works for any OS, and even when Vista stops working properly.
Acer in its infinite un-wisdom decided to hand over fan control to windows vista "e-power" software. Upon system boot the fan would start up on post then shut down and wait for the os to load and then wait for e-power to start up. On this particular model only Vista has the software to run the fan. So if you install win xp, win 7 or Linux there is no software to control the fan after post.
My solution was to open the laptop, cut the red fan wire and solder it to the 5 volt supply of the USB port.

The fan is designed to run at 3 to 5 volts, the USB runs at 3 volts. the problem was solved.

The reason I chose this was because the so called Bios update from acer does not fix the fan problem, the ACPI grub command solution for ubuntu only works on some machines. My solution guarantees that the fan always runs when the machine is on.

For those that are concerned about the power load of the USB port, the fan consumes less power than a typical USB device.

---

### Post by Ner thumper on 2012-08-12
To upchucky.  I did it. i soldered the red fan wire to the first pin on the right of the aser aspire 5515 usb attached to the motherboard and it works. OMG THANK YOU SO MUCH.
I have spent days on this computer trying to get it to work and finally it work.  I bow to the master for his great suggestion and then do a dance of victory.

---

### Post by fidgaf on 2012-08-25
That would explain why wading through lm-sensors didn't help in any way. No fan detected.

Thanks.

Will try it soon and let you know.

---

### Post by fidgaf on 2012-09-28
Too late!

I delayed getting around to the fan wire fix and someone used the laptop and fried it. :-k

Ubuntu cost me a new laptop in this instance but still think it's great. :)

Suggestion:
If they can't do a software fix for this issue should we have a list somewhere of computers **NOT** to use Ubuntu on?

Acer Aspire 5515 seems to be one of these not to use Ubuntu on.


.

---

