---
title: "Printer - Documents in Queue, will not print."
date: 2013-02-04
forum: Hardware
---

### Post by CFet on 2013-02-04
Hi There,

I have a HP Deskjet 5740 that was printing fine until a recent update. I have no idea why it has stopped printing. All it does not is have documents sit in queue forever and not print. I have tried removing cups via the software center and re-instlaling but no luck. Have also tried installing HPLIP-CUPS via the center and no luck. I'm really stumped and would like this to work again. Any help is appreciated, I'm unsure how to troubleshoot it effectively. Printer is connected via usb. 

Regards,
Chris

---

### Post by Tom Collier on 2013-02-04
Chris,

You may want to consider installing hplip, from hplipopensource.com. The site allows you to drill down to device-specific information, and updates periodically to include more HP devices. Here's the link to get started with the specifics that apply to the HP Deskjet 5740:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

I know I was never able to get a satisfactory resolution by relying on the standard stuff available from the respositories.

Hope this helps...

Tom

---

### Post by cybrsaylr on 2013-02-04
Something similar happened to me recently with an HP 5440 printer. It did exactly the same as you after putting in a new 'refilled' B&W ink cartridge. New cartridge ran good for a week them did what yours did. Had HP Toolbox installed with Ubuntu and it reported 'no communication' between printer and cartridge. Tried reinstalling the newly refilled cartridge a couple times but kept getting the same report from HP Toolbox.

 Ended up taking that refilled cartridge back to store. They tested cartridge and said the electronics on it had 'shorted out' causing this problem. They said it just happens sometimes with HP cartridges. They gave me a new cartridge since it was still under their 90 day warranty. Put the new one in and it works like a charm again. Maybe that happened to you also.

---

### Post by CFet on 2013-02-04
> **Tom Collier said:**
> Chris,

You may want to consider installing hplip, from hplipopensource.com. The site allows you to drill down to device-specific information, and updates periodically to include more HP devices. Here's the link to get started with the specifics that apply to the HP Deskjet 5740:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

I know I was never able to get a satisfactory resolution by relying on the standard stuff available from the respositories.

Hope this helps...

Tom

HOLY SCHNIKIES, IT WORKS!

Thank you so much Tom!

Chris

---

