---
title: "Wireless (Broadcom BC4311)"
date: 2011-08-11
forum: Hardware
---

### Post by headvampyre@hotmail.co.uk on 2011-08-11
Hi,
I've recently acquired a laptop (HP Pavilion dv200), and the only real issue I'm having is with WiFi. The "Additional Drivers" app shows the driver I need (I have confirmed this with lspci | grep Broadcom, which shows the same model). 
I've installed the drivers, but every time I install them, WiFi completely disappears from the network menu(It use to say "Required firmware missing"). 

Then I checked /etc/modprobe.d/blacklist-bcm43.conf and it the module is disabled, but the file is controlled  by bcmwl, and all changes will be lost. How would I enable this module?

Any ideas?

---

### Post by militantduck on 2011-08-11
have a look at this sticky post...

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

its under Networking & Wireless

edit: regarding the firmware issue..  for my card (atheros) i needed a firmware file (ar9271.fw) as well as the driver. I cant remember which folder it goes in, i take a look and check.

---

### Post by militantduck on 2011-08-11
ok, looks like you do need the firmware like my card.

take a look at this, it appears to have steps to get it working, they include getting the firmware.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

