---
title: "I need help!!! Wireless set up with broadcom STA driver"
date: 2010-01-24
forum: Hardware
---

### Post by valjes on 2010-01-24
[LIST=1]
[*]Hi,I'm new to the forums but am a long time lurker and I need help. I've searched for this already and haven't found a thing. PLZ help! D:
[/LIST]
  My Broadcom STA driver isn't installing properly it gives me an error and tells me to check the log. It still works after the error, but sometimes it gets stuck in the driver install then I have to reboot and do it again and it adds a lot of time to my start up.

  I've already updated and upgraded with the sudo commands and tried reinstalling on syp. pack manager I need some help.

anyhow here's the jockey.log so you guys can tell me whats wrong. Thanks in advance for the help

2010-01-24 17:42:21,348 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b203ac>
2010-01-24 17:42:21,349 DEBUG: reading modalias file /lib/modules/2.6.31-14-generic/modules.alias
2010-01-24 17:42:21,539 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-24 17:42:21,545 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-24 17:42:21,584 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-24 17:42:21,587 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-24 17:42:21,592 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-24 17:42:21,598 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-24 17:42:21,601 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-24 17:42:21,601 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-24 17:42:22,309 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-24 17:42:22,309 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-24 17:42:22,310 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-24 17:42:22,314 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

---

### Post by valjes on 2010-01-24
Please help!  D:

---

### Post by PRC09 on 2010-01-24
The following may give you some help with Broadcom cards if you havent already tried........

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

