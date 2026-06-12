---
title: "Activating the WiFi in a Fujitsu Siemens Sa3650-L?"
date: 2009-09-01
forum: Hardware
---

### Post by KeeperOS on 2009-09-01
I'm looking into buying a small (12"-13") laptop and the **Fujitsu Siemens Sa3650-L** came to my attention.
The place I work at sells it and I can get it at a price that is more than right.

The biggest problem with it though is that many devices, notably the Wireless, Bluetooth, camera and mic are turned ON/OFF via function combos (the WiFi/Bluetooth with Fn+F1) with the default state when the PC is turned on being at **OFF**.

Sadly, when I loaded a Kubuntu 9.04 LiveCD to test it I found that while common functions like volume control/mute or screen brightness worked like a charm the function combo for turning the WiFi/Bluetooth ON (Fn+F1) did absolutely nothing, the LED for WiFi remaining OFF.

Is there a way to tell (K)ubuntu to turn it ON or will I be stuck to using LAN or an external USB WiFi adapter should I buy it?

---

### Post by newton21989 on 2009-09-03
Open up a terminal window and type "xev" Press the key combinations and see if they register. If they do, you can probably use a program like Lineak to bind the commands to those keystrokes. I have no clue what those commands might be, but this is a step in the right direction.

---

### Post by KeeperOS on 2009-09-04
I decided to buy the laptop afteral so all subsequent tests were done with my own personal machine instead of a display one.

No, Fn+F1 doesn't register nothing, just like the commands for the camera etc register nothing (even though the camera itself is turned on and off).

However Fujitsu-Siemens offered somewhat of a solution in the form of a new BIOS (both the test machine and mine had the original v1.00) which adds a setting where the user gets to choose for the machine instead of defaulting to OFF to remember the WiFi's last state (which upon flashing the BIOS is defaulted to ON).

In short, if you have Windows the WiFi will default to on until you manually turn it off whereas if you don't you simply won't be able to turn it off unless you enter the BIOS.

Happy that I would finally have wireless I loaded a LiveCD of Ubuntu 9.04 which this time detected my WiFi adapter.

Unfortunately Ubuntu doesn't have a proper driver for this Atheros adapter; It detects and loads it but the adapter itself couldn't detect my WPA-PSK protected network standing 30cm away whereas it detected two other real weak networks...
That however is a whole other story...

---

### Post by bishka on 2009-09-28
Hi KeeperOS,
 
I have same laptop as you, but my wi-fi work fine, i din't have a problem. The question did you manage with graphoc booster? Does it work?

---

