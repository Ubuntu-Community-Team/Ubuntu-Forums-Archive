---
title: "Wireless network problem"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by the_nite_owl on 2007-07-08
Hi All,
I installed Ubuntu 7.04 x86 on an older IBM 390X laptop with a PCMCIA wirless network card.
I managed to get the mrv8335 driver installed but am running into odd problems.

If I turn off roaming and set the WEP password in the setup the card is always recognized as being installed but it will always fail to connect to the network.  If I set roaming enabled I can connect to the network but every time I reboot the computer it fails to re-start the wifi card.  If I enter udo modprobe ndiswrapper from a terminal session the card instantly comes back then connects to the network.

Have I done something wrong?  I want to set it up without roaming so it just connects to my network every time but this method always fails to connect.  And if left on roaming I have to enter the modprobe command before I get any response (no status lights at all) from the wifi card.
The laptop is for one of the kids to use so I need to get this smoothed out.

Any ideas?

---

### Post by Espreon on 2007-07-08
Do you need to enter sudo modprobe ndiswrapper to get the card started up?

Make sure you have the .ini or .inf file that is the driver file

First open synaptic:

Completely remove all ndiswrapper related stuff.

Then reinstall all the ndiswrapper stuff, search for ndisgtk, install it.

Then goto System>Administration>Windows Wireless Drivers and hit it.

Hit Install new driver and select the .ini or .inf file that is the driver.

Then connect to the network.

---

### Post by the_nite_owl on 2007-07-08
> **Espreon said:**
> Do you need to enter sudo modprobe ndiswrapper to get the card started up?

Yes.  But only when the card is set in Roaming mode.  When not set to roaming it seems to start up but will not ever connect even with the correct key.

---

### Post by Espreon on 2007-07-08
Um re read my post, since I edited it with more info.

---

### Post by the_nite_owl on 2007-07-08
> **Espreon said:**
> Um re read my post, since I edited it with more info.

No luck, same symptoms.
I first manually removed the driver with the ndiswrapper command then I removed all of the ndiswrapper stuff in Synaptics.  I rebooted and put in a wired adaptor so I could get a connection to do the reinstall of the ndiswrapper stuff then used the GUI tool to add the drivers back in.

I THINK I am doing things correctly but still the same problem.  If not in roaming mode the card comes active but does not seem to correctly pass the network key.  If in roaming mode I have to kick start the card manually then it will make a network connection.

I may give up and order a new card but this one SHOULD work.

---

### Post by Espreon on 2007-07-08
You are doing it correctly! Maybe ndiswrapper hates your card.

---

