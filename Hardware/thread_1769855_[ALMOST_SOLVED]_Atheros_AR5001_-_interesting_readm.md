---
title: "[ALMOST SOLVED] Atheros AR5001 - interesting readme."
date: 2011-05-28
forum: Hardware
---

### Post by cpucpu on 2011-05-28
Hi,
Most users have had problem with this before, most likely it is some sort of misconfiguration of wireless linux drivers that affect this type of cards on several distributions.

The thing is like this:
The wireless device is recognized, but does not detect any networks (AP), and when you click on the wireless icon it displays something like ´wireless is disabled´ seemingly saying the wireless is turned off.

It apparently happens because of a ´soft-switch´ turned off, that OS is not capable (or intended) to warn you about. While the physical button is a ´hard-switch´.

I an particular case for an AR5002 atheros wireless network, ´Tx-power´ was off (check with **iwconfig**) and also soft blocked (check with** rfkill list**). So, for the first: **iwconfig wlan0 txpower auto** where wlan0 is your actual wireless device; for second:** rfkill unblock 0** where 0 is your ¨device indentifier¨.

p.s. this could possibly a kernel bug, cause you are activating what´s de-activaded in the first place.

---

### Post by elnetotaca on 2011-10-11
I said this, and I will say it one more time(the last one! lol)


open terminal then;

gksu gedit /etc/modprobe.d/ndiswrapper

add;

sudo rmmod -f ath5k; sudo rfkill unblock all; sudo modprobe ath5k
save, close it, then reboot.
cheers

---

