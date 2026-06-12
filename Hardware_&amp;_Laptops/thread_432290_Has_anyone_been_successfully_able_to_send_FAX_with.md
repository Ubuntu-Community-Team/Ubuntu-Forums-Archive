---
title: "Has anyone been successfully able to send FAX with WInModem with Ubuntu"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by kevdog on 2007-05-03
Hi

I currently have a Inspiron 5000e with LT Winmodem installed.  Despite what everyone states, it wasnt really all that hard to set up and install with the martian drivers in order to get the modem functionality working.

My problem however is with the fax portion of the modem.  Ive set up a Hylafax server and have been unable to fax using the modem -- basically boils down to fax not understanding AT-FTS and AT-FTR commands.  Ive  posted to hylafax users group but havent gotten much help.

Has anyone been able to set up WinModem and actually use the Fax capabilities with the modem?

---

### Post by cpbl on 2007-05-04
Sure. I have a winmodem on my laptop, and since Edgy at least have just installed two packages:

apt-get install efax-gtk slmodem

and then efax works beautifully. 
I'm not sure that slmodem is for every hardware...
I recall efax by itself didn't work, though the ubuntu documentation only mentions efax.
I think I commented on this bug (efax did not know it was dependent on slmodem) at some point and someone explained that it was on purpose...

c

---

