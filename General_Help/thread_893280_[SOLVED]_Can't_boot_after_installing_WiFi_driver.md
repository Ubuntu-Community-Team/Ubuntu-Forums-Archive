---
title: "[SOLVED] Can't boot after installing WiFi driver"
date: 2008-08-18
forum: General Help
---

### Post by mardawi on 2008-08-18
Hi,

I've installed the windows xp wifi driver for Intel® PRO/Wireless 3945ABG Network Connection using NdisWrapper (i guess) and everything seems to be alright. I rebooted and booting now hangs at the middle (when it tries to load the wifi driver) even in recovery mode. Is there any way to reverse that?

Please help, i'm now stuck with Windows Vista (I hate this thing :( )

---

### Post by mardawi on 2008-08-18
fixed by deleting "/etc/ndiswrapper"
```
sudo rm -rf /etc/ndiswrapper/ 
```

:guitar:

---

### Post by fragos on 2008-08-18
Intel® PRO/Wireless 3945ABG is automatically identified and the correct driver installed by Ubuntu. This is one of those cases where you should trust Linux to the right thing before charging to the command line. There are some WiFi chipsets that require ndiswraper to run a Windows DLL driver -- this isn't one of them.

---

### Post by mardawi on 2008-08-19
Yes, ubuntu identifies the driver, but it does not work at all! Can you please help?

---

### Post by fragos on 2008-08-19
When you replace a driver with an Windows DLL there are two steps -- blacklisting the old driver so it won't load and executing ndiswrapper in a sytem startup configuration file. By deleting ndiswrapper you cause the existing DLL driver load to fail -- not really the best way to do things. The blacklist also needs to be removed. If you didn't blacklist the Linux driver you'd have two drivers trying to control the same device which wouldn't work. Without knowing how you hacked your system It's difficult to recommend how to repair what you've broken.

---

