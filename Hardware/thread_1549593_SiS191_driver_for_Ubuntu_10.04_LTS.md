---
title: "SiS191 driver for Ubuntu 10.04 LTS"
date: 2010-08-10
forum: Hardware
---

### Post by Rex Reeve Rabacal on 2010-08-10
Hi everyone! I'm new to this forum and this is my first post. Yesterday night i triple boot installed (Mac OS X, Windows 7) and **[COLOR=Red]Ubuntu 10.04 LTS[/COLOR]** on my laptop - Asus F83SE Series, it was successfully installed, I like the new interface of Ubuntu 10 and it works flawless on my system like Graphics card, wifi and etc.. but except to my LAN connection it doesn't really work properly.. Ubuntu 10 uses [COLOR=Red]**SiS190 **[COLOR=Black]which is wrong for my hardware bcoz my hardware uses [COLOR=Red]**SiS191**[COLOR=Black] for LAN connection[/COLOR][/COLOR].. [/COLOR][/COLOR]please help me to find out this driver.. 
anyway here's my specs:

Brand: Asus F83SE Series 
CPU: Intel core2 duo T6600
Chipset: SiS 968
Graphics  card: ATI HD4570 512MB
memory: 4GiG
Wireless: Atheros AR9285
Lan: **[COLOR=Red]SiS191[/COLOR]** Ethernet Controller - Not working properly.

Thanks for Advice..:D

---

### Post by Rex Reeve Rabacal on 2010-08-17
bump....:icon_frown:.. I need everyone's help.. please.

---

### Post by mhgsys on 2010-08-17
Not sure if it works the same way for 10.04,(this was used in jaunty) but you could give it a try
(I can't test it since I don't have that card myself)


> **Sealbhach said:**
> Not good news about this particular ethernet adapter that you have. There's been problems with it for years, though it had been fixed in recent kernels, but the problem seems to have come back.

There's a bug report here about it:

[https://bugs.launchpad.net/ubuntu/+bug/345374](https://bugs.launchpad.net/ubuntu/+bug/345374)

[B]A workaround that some people report to have worked is to change the MTU to 1492.

You can try this by right-clicking on the network icon, select Edit Connections, choose Wired, click on eth0, click on Edit, change MTU from Automatic to 1492 and click Apply.
[/B]
Give it a try and see what happens.

.

---

### Post by Rex Reeve Rabacal on 2010-08-17
Thanks for the quick response, I'll give a try.

---

