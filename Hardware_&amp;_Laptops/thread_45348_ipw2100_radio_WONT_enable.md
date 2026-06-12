---
title: "ipw2100 radio WONT enable"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by edudlive on 2005-06-29
I'm guessing even though this has to do with Kubuntu I can post here?

Well, I have a Dell 600m with Intel PRO/Wireless 2100, it worked PERFECTLY under Ubuntu, but since I'm a KDE fan I decided I wanted Kubuntu.  The card seems to WORK under KWifiManager but the radio is disabled (but it is connected to my router).

Doing iwconfig eth1 txpower on gives me the error:

"SET failed on device eth1; invalid argument" and I can't enable it from KWifi either

Anyone got an idea?

---

### Post by alastair on 2005-06-29
Check you boot logs and pay close attention to any ethernet (wireless) probe or load :

/var/log/syslog

Also, output of :

 - iwconfig
 - ifconfig -a

But the device module has to load to be accessible.

---

### Post by edudlive on 2005-06-29
I fixed it, I disabled eth0 and that made it work.

---

### Post by cuboconojos on 2005-07-22
Could you be more especific. I have the same problem, KWifiManager says that the ratio is disabled, but my wireless card is working. And I read on the KWifiManager manual that the "enable ratio" thing on the menu is not working on current versions.

Thanks

---

### Post by andrius on 2005-12-06
[QUOTE=edudlive]I fixed it, I disabled eth0 and that made it work.[/QUOTE]

from bios? My intell wireless returns same "invalid" when trying to txpower on. :(

---

