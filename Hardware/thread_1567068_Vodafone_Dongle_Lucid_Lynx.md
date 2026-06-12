---
title: "Vodafone Dongle Lucid Lynx"
date: 2010-09-03
forum: Hardware
---

### Post by nuffink666 on 2010-09-03
Hi all,

Have searched the forum and have found various bits on how to get the vodafone dongle K3570-Z top work with LL, but what i havent found out is whether the BetaVine connection Manager runs alongside or "overtakes" the normal Network Manager in LL? I would prefer to use standard manager if possible but is there anything i need to install to get this to work. I spoke to Vodafone who gave a heap of setting stuff which tbh made no sense at all so if anyone got a working step by step for the idiot (me) on how to set this up i might leave them something in my will

TIA.

---

### Post by IcarusR on 2010-09-03
This is a quote from the betavine forums from a member called Andrewbird who posts a lot & seems to know what hes talking about.

> BCM has two pieces, as does Network manager. Our wader-core component replaces Network manager's 'Modem Manager' part, but the BCM client doesn't change Network Manager itself, so Wi-Fi, Ethernet and other funky stuff that NM does won't be affected. After installing BCM / Wader-core, you should endup up with wader-core doing the modem stuff, and both BCM and Network Manager use that to make mobile broadband connections.

After you install our updated usb-modeswitch-data package the device should be switched into modem mode just after you insert the stick into the PC. I suspect that your standard Network manager should now be able to 'see' the modem, though I don't know whether it's able to use such a new device properly.


So it would seem that betavine will work alongside network manager.

Having said that don't blame me if he's wrong.
Hope this helps.

See post 7 of this thread on getting it to work with network manager.

[http://ubuntuforums.org/showthread.php?t=1554716]("http://ubuntuforums.org/showthread.php?t=1554716")

Or failing that this might help.

[http://offog.org/articles/linux-3g/]("http://offog.org/articles/linux-3g/")

---

