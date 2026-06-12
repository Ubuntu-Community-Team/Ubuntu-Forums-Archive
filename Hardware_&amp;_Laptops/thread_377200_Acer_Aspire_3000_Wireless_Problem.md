---
title: "Acer Aspire 3000 Wireless Problem"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by jd_acer_aspire_3000 on 2007-03-05
Hi, have been using Ubuntu 6 for a little while without problems... until I got around to trying to get my wireless card to work.

I have had SuSE 10.1 on this same laptop.  After a little work, I was able to use ndiswrapper and the windows driver (bcmwl5) successfully.  Strangely after many months of operation the wireless just stopped working.  There is an indicator light on the front; this also went completely dead.  No idea what I did to cause it.  I have windows xp dual booting and the wireless still works when I boot windows.

Recently I got rid of suse and installed ubuntu and I've not been able to get the wireless working.  I ran the ndiswrapper setup an it seems like everything installed correctly, but still it's still not working.  The indicator light on the front never comes on.  Wireless still works for xp.

Could someone out there  please point me in the right direction?  I've searched around and most everything sends me to ndiswrapper, which I've tried but without success.

Thanks ahead of time!

---

### Post by dyous87 on 2007-03-05
If it just stopped working like that it is possible that your card blew out. Does lspci pick it up?

---

### Post by jd_acer_aspire_3000 on 2007-03-06
dyous87,

Yes, lspci finds it:

Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Plus, when I boot xp the card (and the button/light in front) works fine.

Any ideas as to where to go from here to troubleshoot it?

Thanks

---

