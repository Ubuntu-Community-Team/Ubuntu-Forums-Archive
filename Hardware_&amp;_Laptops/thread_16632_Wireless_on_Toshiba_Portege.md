---
title: "Wireless on Toshiba Portege"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by Melvin on 2005-02-22
I have got Warty installed on my old Portege 3110ct. Most of the stuff work well, except that I have not managed to get my Lucent Orinoco Silver to work.

When the card is plugged in, the lights appear (a steady power indicator, and a flashing activity light), so it appears to be working. The card still works on the Windows boot.

The Wireless Icon states "No Wireless Device".

In Device Manager, it shows up as "Unknown Device" and everything is "unknown", but it shows the correct MAC address.

In Network Settings, it shows up as eth1, Wireless LAN Card.  I can't seem to activate the card. Everytime I activate the device, it gets deactivated almost immediately.

In /etc/modules.conf, the line "alias wlan0 prism2_cs" is active.

Hopefully someone can make some sense of what is happening.  I am a newbie, so baby steps are helpful.  Thanks.

---

### Post by Melvin on 2005-02-22
I should also add that when I performed a dmesg in terminal, this was part of the output:

orinoco_lock() called with hw_unavailable (dev=c6cd2000)
eth1: Station identity 001f:0001:0008:0048
eth1: Looks like a Lucent/Agere firmware version 8.72
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:0B:AA:DC
orinoco_lock() called with hw_unavailable (dev=c6cd2000)
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 11, io 0x0100-0x013f
eth1: Unknown information frame received (type f202).
eth1: no IPv6 routers present
eth1: Unknown information frame received (type f202).

---

### Post by awahl on 2005-02-27
Melvin, It's been awhile since your last post, and hopefully you resolved the issue- I had a similar issue, setting the "enable" button, and having it switch off immediately...on an IBM Thinkpad 600E with a Linksys card. 

I used Synaptics to re-install Wireless-Tools- and all was well. Hope this helps you.

I love ubuntu -

---

### Post by oxalá on 2007-07-05
man, i wish i knew how you got Ubuntu installed on that old 3110CT in the first place...

---

