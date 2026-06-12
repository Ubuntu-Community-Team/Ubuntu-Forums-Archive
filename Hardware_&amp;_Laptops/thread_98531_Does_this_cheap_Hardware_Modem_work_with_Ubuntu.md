---
title: "Does this cheap Hardware Modem work with Ubuntu?"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by pcatiprodotnet on 2005-12-03
Does this modem work with Ubuntu?  It says "Linux Compatible" and "100% Hardware fax modem".
[http://xiertekusa.com/product.php?pid=249&xcSID=dd422f8dd7172e96ac71f404c0f3d700](http://xiertekusa.com/product.php?pid=249&xcSID=dd422f8dd7172e96ac71f404c0f3d700)
If so, I'm stocking up because it's cheap ($11 plus free shipping if you buy 4+).
Thanks, -pc

[update]
Also found this "semi-hardware" (dsp) modem (only $8 if you buy 20 plus free ship)...
[http://www.acortech.com/.sc/ms/dd/1050711616103849/085805/nc/Modem--GENERIC/514/Intel%20Chipset%20Internal%2056K%20V%2E92%20Internet%20PCI%20Fax%20%5E2FVoice%20](http://www.acortech.com/.sc/ms/dd/1050711616103849/085805/nc/Modem--GENERIC/514/Intel%20Chipset%20Internal%2056K%20V%2E92%20Internet%20PCI%20Fax%20%5E2FVoice%20)
It supposedly has a GPL linux driver, but haven't verified.

---

### Post by mlomker on 2005-12-03
I'd assume it's fine.  The key distinction is hardware vs. software modems.  The DSP modems can be a pita to get working, but hardware modems are 100%.

---

### Post by az on 2005-12-03
[QUOTE=mlomker] can be a pita to get working,[/QUOTE]


Mmmmmm Souvlaki! :)

A pci modem should be autoconfigured by alsa at boot and may be assigned device /dev/ttyS14.  The modem gui is not intuitive and may not autodetect it, although if you enter the device by hand it will work.

---

