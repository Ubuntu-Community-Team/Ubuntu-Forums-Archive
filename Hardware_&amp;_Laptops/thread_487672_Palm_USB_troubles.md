---
title: "Palm USB troubles"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by gga73 on 2007-06-29
I used to have a Palm Pilot working with KPilot, but now it fails to sync.
I upgraded from Edgy to Feisty and I also incorrectly did something that I was told could hose USB, which was to briefly plug a two male USB cable between two computers.
I'm trying to detect whether the reason things no longer work is a simple misconfiguration issue or I hosed my USB port.

I can properly see the USB port with KInfoCenter and my palm device does get power from the USB port.
Still, no communication happens and /dev/pilot no longer automounts.

Any ideas of things to try?

---

### Post by Morgonte on 2007-07-22
I had a similar problem with my Treo 600 and Gnome-Pilot. Pressing the Hotsync button on the Treo-USB cable only resulted in a somewhat cryptic error message suggesting that the sync failure had something to do with "USB-Serial". The problem occured when I upgraded to Feisty Fawn.
However, I could get the Treo to sync by first setting the Cradle USB settings in gnome-pilot Settings to "usb:" instead of "/dev/pilot" and then in the Hotsync app on my Treo set connection to "Cable" instead of "Cradle/Cable".

Maybe this is of no help at all to you, but on the other hand, it might be what you need (if you haven't come up with a solution already).:)

/Stefan

---

