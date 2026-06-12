---
title: "Radeon Mobility x2300 drivers on Sony VAIO VGN-CR13G"
date: 2010-08-14
forum: Hardware
---

### Post by onlybleeding on 2010-08-14
Hey guys

First time poster here.

Just trying to get the drivers working for the Radeon Mobility x2300 in my Sony VAIO VGN-CD13G.

Is there a way to check if they are currently working? Maybe they are already working but I have had a couple of error messages that make me think not.

What is the process for installing them?  I can't seem to find the x2300 drivers on the ATI site.  I have tried to install everything to do with ATI, Radeon or flgrx in synaptic package manager and it hasn't seemed to make a difference.

Any help?

Cheers

Edit: Oh yeah I am running Ubuntu 10.04 (Desktop?)

---

### Post by Yellow Pasque on 2010-08-15
The drivers are pre-installed. The proprietary driver doesn't support your device. Purge the fglrx stuff. [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by iknatius on 2010-08-15
I have just purged fglx following Temüjin's link instructions in my ASUS A8J (ATI Mobility Radeon X2300) with 10.04 and it seems that I am under an electronic war: my screen is barely usable, full of aleatory horizontal lines and  blinking all the time. It seems that X is not painting all the frames correctly and some of them are drawn in a different position (image attached).

Any help will be VERY much appreciated.

---

### Post by onlybleeding on 2010-08-15
> **Temüjin said:**
> The drivers are pre-installed. The proprietary driver doesn't support your device. Purge the fglrx stuff. [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)


Yay, that fixed it,  Cheers! :D

---

