---
title: "Braodcom B43 Driver not working with new kernel"
date: 2009-01-12
forum: Hardware
---

### Post by redserpent7 on 2009-01-12
I have recently updated my Ubuntu 8.04. The update manager suggested to install the new kernel which is "2.6.24-23-generic" so I did. Then the unexpected happened. My Wlan stopped working. I've checked its status via System/Administration/Hardware Drivers and its there, checked but with a red circle next to it and a Not in Use status. And when I click on the network icon on my panel I get an error message of something not found, I don't remember what the specific error was though.

Anyways I tried using the old kernel, i.e. "2.6.24-22-generic" and it worked.

I'm not sure if I should reinstall the driver or if there is something else that I have to do to make my WLAN work with the new kernel update.

Oh and one other thing that I noticed is that I now have two entries in the Hardware Drivers window. The first is the "Broadcom B43 Wireless Lan" which is enabled and marked as being used in the old kernel yet has a different status in the new one.
The other one is "Broadcom STA wireless lan" which is disabled and marked as "Not in Use" in both kernels.

Hope someone can help me with this. Its really annoying

Regards

---

### Post by Favux on 2009-01-12
Hi redserpent7,

The new driver "Broadcom STA wireless lan" looks to be the Broadcom proprietary driver "wl".  It looks like your updated kernel supports it so Ubuntu now offers it.  To activate it you have to go to System>Administration>Hardware Drivers.  I don't know if you have to blacklist your old one.  Was it a ndis wrapper?

---

### Post by licensedorchid on 2009-01-12
> **Favux said:**
> Hi redserpent7,

The new driver "Broadcom STA wireless lan" looks to be the Broadcom proprietary driver "wl".  It looks like your updated kernel supports it so Ubuntu now offers it.  To activate it you have to go to System>Administration>Hardware Drivers.  I don't know if you have to blacklist your old one.  Was it a ndis wrapper?

FYI, I had to plug in and update the repos before I could activate my B43 drivers.

---

### Post by redserpent7 on 2009-05-22
Thanx to Jaunty now my WLAN drive works fine.......

---

