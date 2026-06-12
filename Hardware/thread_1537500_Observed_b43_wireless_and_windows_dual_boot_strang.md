---
title: "Observed b43 wireless and windows dual boot strangeness"
date: 2010-07-23
forum: Hardware
---

### Post by Alexis Phoenix on 2010-07-23
Something I noticed way back in Feisty, and still not resolved.

If I reboot my laptop (Inspiron 1501) into windows, turn the wireless off, and reboot into Ubuntu, I experience great problems connnecting wirelessly to a network.  Sometimes it's possible to connect manually, but wpa_supplicant repeatedly fails, blacklisting the AP.  The wireless is turned on, either by the button or by wpa_supplicant, just can't connect.

The only way to solve this is to reboot windows and turn on the wireless, then reboot into Ubuntu again.  Obviously I'd like a way to enable in Linux whatever it is that windows turns off.

I recently noticed the same effect if the proprietary wl driver is used (I found this using Syslinux rescue cd, which uses the wl driver) if the card is switched off whilst using wl and the system restarted.

Well, I give this as food for thought for those stuck with this card, rather than as a request for help, I hope it's of use to someone.

Alexis Phoenix

---

