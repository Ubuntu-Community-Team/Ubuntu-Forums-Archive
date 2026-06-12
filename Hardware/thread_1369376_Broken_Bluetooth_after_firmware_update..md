---
title: "Broken Bluetooth after firmware update."
date: 2009-12-31
forum: Hardware
---

### Post by prosigna on 2009-12-31
I have a Thinkpad T60 with a Broadcom BCM2045B bluetooth adapter.  This laptop is a dual boot XP/9.10 machine.  The bluetooth worked fine after a clean install.  I then ran a firmware update on the XP system and now Ubuntu can not negotiate a connection with my Nokia 6085.  The Gnome Bluetooth Properties 2.28.1 gui can see other devices but the 6085 can not see the computer. The "make computer discoverable" box is checked.

I tried removing the bluetooth packages and re-installing them using the Completely Remove function in Synaptic Package Manager.  The problem remained.

I am stumped.

---

### Post by prosigna on 2009-12-31
This ohone was paired with the XP system on this machine.  I removed that pairing from the phone.  Then the phone was able to see the computer properly.  I guess the bluetooth card registers a MAC address (or something like it) with the phone and not just the name you assign to the connection.  The phone refused to connect with the same MAC address twice.  All is fine now.  Thanks.

---

