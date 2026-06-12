---
title: "Radeon HD 6620G ATI/AMD graphics still not properly supported in 13.10"
date: 2013-10-30
forum: Hardware
---

### Post by 7-webmaster on 2013-10-30
The on-board graphics on my AMD based laptop, identified as Radeon HD 6620G by lspci, has never been properly supported.  Since the blurb for 13.10 advertised improved support for ATI graphics I just did the upgrade, but there is no improvement.  I have posted details of the problem here and on the X.Org site but two years, and 4 releases of Ubuntu, have gone by and the situation has not improved.

Basically if I use the proprietary driver fglrx from AMD then about 10% of the time when I reopen my laptop the screen stays blank and I have to reboot the system, losing all on-going work.  In particular if I shut the laptop before the system has completed all initialization activity, which can take several minutes, the laptop is unlikely to recover when I open the lid.  Also the binary only driver does not support using a full HD (1080x1920) display because it is hard-coded to a maximum total display space of 1600x1600 pixels, even though the AMD graphics obviously supports much more than that.

If I use the X.org driver I can exploit a full HD display but the X.org driver fails **100% of the time** to turn on the display backlight when the laptop is opened.  So if I use that driver I must reboot my laptop every single time after closing the lid.  I asked the X.org gurus how to manually turn on the backlight and their response was "The driver is supposed to do that for you."

---

