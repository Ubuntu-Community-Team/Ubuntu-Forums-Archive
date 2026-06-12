---
title: "hp laserjet 1000 printer stop working"
date: 2009-11-22
forum: Hardware
---

### Post by barhoma56 on 2009-11-22
i have hp laser-jet 1000 printer it was working in the previous releases of Ubuntu but it stop working with Ubuntu 9.10 please help if there is any idea
thank you

---

### Post by sgosnell on 2009-11-22
Have you tried to install it?  You have to do it with new installations.  System/Administration/Printing, then click the New button to install a new printer.  It should find your printer and install the drivers for it.

---

### Post by barhoma56 on 2009-11-23
> **sgosnell said:**
> Have you tried to install it?  You have to do it with new installations.  System/Administration/Printing, then click the New button to install a new printer.  It should find your printer and install the drivers for it.
thank you for interest yes i did the steps for adding the printer but i tack the order and saying the page has been sent to printer but no out put

---

### Post by sgosnell on 2009-11-23
Can you send a test page to the printer?  It may have the wrong driver.

---

### Post by rudy.b on 2009-11-23
> **barhoma56 said:**
> thank you for interest yes i did the steps for adding the printer but i tack the order and saying the page has been sent to printer but no out put

I had a similar issue with my HP LaserJet 1000 when installing using the recommended driver (Foomatic/foo2zjs).  When I printed a test page the job appeared in the queue and seemed to process fine... except nothing actually printed.

However, I changed to the alternative driver (hpijs) and it seems to work now.  Here are the steps I used to make this change:

[LIST]
[*]System > Administration > Printing
[*]Select your printer and click the 'Change...' button on the 'Make and Model' line
[*]HP > LaserJet 1000 
[*]Select the hpijs driver
[*]I chose to 'Try to copy the option settings over from the old PPD.' and then clicked 'Apply' (I'm not sure what the implications are here, but it seems to work.)
[/LIST]

---

