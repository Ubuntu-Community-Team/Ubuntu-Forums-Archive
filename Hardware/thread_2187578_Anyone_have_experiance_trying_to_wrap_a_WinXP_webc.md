---
title: "Anyone have experiance trying to wrap a WinXP webcam driver with ndiswrapper?"
date: 2013-11-12
forum: Hardware
---

### Post by jnyhuis on 2013-11-12
I have a Lenovo thinkpad X230 running Ubuntu 12.04 and it is 'almost' the perfect laptop.
Unfortunately, the laptop's integrated webcam does not have a hardware vendor provided linux driver, and this driver has not made it to open source yet.  :-(
I do have a lenovo WinXP driver for the webcam, and I've been playing around with ndiswrapper to see if I could get the WinXP webcam driver to run under Ubuntu.

Has anyone used ndiswrapper with webcam drivers before?  I have not had much luck adapting the NIC wrapper examples I've googled, and i have not found any specifically for webcams.  Has anyone else done this for a webcam?   

My integrated webcam hardware info:
Lenovo Part number: 04W2668
HS Camera L22/glenn bsn
63Y0248
KD4/DS2CM2/BL/CD
63Y0250
KD4/DS2CM2/BL/CD

---

### Post by Mark Phelps on 2013-11-13
Maybe I'm misunderstanding what you're trying to do, but NDISWrapper is for network drivers, not webcam drivers.

---

