---
title: "Slow USB2 support in Breezy?"
date: 2005-12-05
forum: General Help
---

### Post by mrguytx on 2005-12-05
I have an external DVD/CD RW USB2 device. Running Breezy.
Device is detected, and works, but is very slow.
For instance this device will burn at 40x under windows but no faster than 6x on Breezy.

Since it's external I can't do anything with DMA, at least not that I know of.

Is there something else that can speed up an external USB2 device?

TIA.

---

### Post by mad_pheonix on 2005-12-05
I notice the same thing with my iPod running through USB 2.  I dual boot windows/ubuntu and even though it definitely goes faster than my USB 1.1 port in Ubuntu, it goes probably half the speed that it does in Windows.

---

### Post by hw-tph on 2005-12-05
My HDD-based mp3 player (iAudio M3 40GB) is just as fast as in Windows. HighSpeed USB 2.0 using the ehci_hcd driver. Make sure the USB port you're using is powered by the correct driver.

---

### Post by linuxa on 2006-01-11
How did you manage to install the ehci_hcd drivers?

When I check my usb status in kinfocenter, it shows up as usb 1.1 even know it's suppose to be usb 2.

How do I get Kubuntu to correctly identify the usb device?

---

