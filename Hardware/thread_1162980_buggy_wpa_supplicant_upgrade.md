---
title: "buggy wpa_supplicant upgrade?"
date: 2009-05-18
forum: Hardware
---

### Post by Alexis Phoenix on 2009-05-18
Hi folks

I have recently upgraded all the packages on my Dell Inspiron 1501 running Hardy Heron LTS and home brew 2.6.28 kernel, whilst connected to a public WiFi access point (Cloud Networks), which went fine (this laptop has a Broadcom wireless card and uses the b43 driver btw).  Since then I have tried to connect to my wireless router at home, which uses pass-phrase protection.  This was working fine about a year ago (last time I used it!) but now it just refuses to connect.  The router is working fine (connects to windows no problem) and running```
iwlist scanning
``` shows it up ok.  I can't connect using my usual ```
iwconfig eth1 essid home_net key blah
``` because iwconfig doesn't support passphrases yet.  Whilst wpa_supplicant used to work fine for this, it doesn't seem to now, whether invoked manually or through kwlan (which I had stopped using because it got very annoying) with some error I can't remember (I'm using computer in library).  Grr gnash spit grrr.  Gonna go home and play around in root and try not to kill tree now.

If anyone can suggest anything I might try, or if there is a known issue here, I would be very appreciative.

Cheers
Alexis Phoenix

---

### Post by Alexis Phoenix on 2009-05-31
Okay, update to this problem - the wireless does work, but everything's a bit random and unpredictable regarding whether the wireless button will work, whether the interface is up or down, and if I need to re-load the driver.  I'ts definitely related to the updates (and /not/ the kernel) though because it was ok before then.  Anyone else having an experience like this?  Any suggestions?

---

