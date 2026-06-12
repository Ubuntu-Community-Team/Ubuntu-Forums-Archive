---
title: "New sub router printer iP address, HP LaserJET 4L"
date: 2012-05-13
forum: Hardware
---

### Post by LinuxBob on 2012-05-13
I added a new subrouter (kept my original router 192.168.0.xxx for wired attached PCs etc) with subnet of 192.168.1.xxx to inprove wireless network quality (it does that).  My Ubuntu laptop is wirelessly connected to new subrouter and an HP LaserJet 4 is wired to the new subrouter via Dlink printer network device.  I can ping the LaserJet and it was working when both laptop & laserjet were on the original router.  Both laptop and laserjet have new IP addresses so I deleted the laserjet printer and tried adding anew with new IP address.

I cannot print a test page, just says it is "processing."

Any ideas on how to add this printer?  Maybe just instructions on adding networked HP Laserjet will do as I did have it working before but it has been a long time since I needed to set it up.

---

### Post by LinuxBob on 2012-05-15
C'mon someone knows how to set this printer up!

---

### Post by LinuxBob on 2012-05-16
Test page printed out numerous symbols in one row across top of page, page after page.

So I suspect all I need is the correct driver.  Anyone know what that is?

---

### Post by LinuxBob on 2012-05-17
Bump

---

### Post by steeldriver on 2012-05-17
does it not give you a driver selection menu when you add the printer?

if not, maybe you can find something here --> [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

although I would be surprised if there is a more up to date driver than in the repo since it's an old device

btw I think mentioning routers and subnets may have confused people - it seems like this is not a networking issue, right?

---

