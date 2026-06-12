---
title: "Advent 4123 - 3g internal card?"
date: 2010-01-19
forum: Hardware
---

### Post by Phosphorror on 2010-01-19
Greetings all,
 
As I have mentioned in an introductory thread in the Cafe, I own an Advent 4213 Notebook. This Notebook contains a built in Bluetooth and 3g Modem.
 
For the 3g modem, you remove the SIM card from the 3g dongle and insert it into the Notebook when you unclip the battery.
 
The big question is, will Ubuntu work with the Advent 4213's internal 3g card? Obviously, it works with the Huwawei 3g dongle, but it doesn't appear to recognise the 3g card built internally.
 
Any ideas would be appreicated. It's just a small thing really, but it can be messy when you want to go online in Ubuntu.

---

### Post by Phosphorror on 2010-01-24
PROBLEM SOLVED!

Simply press the blue Function 'FN' Key and press F2, to activate the internal 3g card inside the computer.

System > Preferences > Network Connections > Mobile Broadband > Add (enter details of what network you are on, etc). AND THEN try to connect.

You will know when you are successful when it says "Connection Established" with a signal graph and an antenna mast logo on the top of the screen where the usual signal bar would be displayed when accessing a WLAN connection.

Shame you only see the connection signal briefly though, not so bad if your mobile broadband dongle and your mobile phone are both on the same network (like me). Well, this is to the best of my knowledge so this may be useful to someone out there.

It appears the 3g card inside the PC is on by default in Windows, but it must be activated in a Linux install.

---

