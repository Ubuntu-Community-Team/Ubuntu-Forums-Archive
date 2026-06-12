---
title: "Network error!"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by mirtux on 2005-03-01
Hi,
   i've had a working wireless ipw2200 since yesterday. Then, i don't know what i did, i have know this problem during boot up:

 ```

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.1
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: ipw-2.2-boot.fw load failed: Reason -2
ipw2200: Unable to load firmware: 0xFFFFFFFE
ipw2200: failed to register network device
ipw2200: probe of 0000:02:04.0 failed with error -5

tg3.c:v3.10 (September 14, 2004)
tg3: tg3_request_firmware (eth%d): Couldn't get firmware "tg3/tso_5705-1.1.0".
tg3: eth%d: Firmware "tg3/tso_5705-1.1.0" not loaded; continuing without TSO.
tg3: eth0: Link is up at 100 Mbps, full duplex.
tg3: eth0: Flow control is on for TX and on for RX.

``` 
Normal net (tg3) is working but ipw2200 is not working!

Any ideas?
MC

---

### Post by alastair on 2005-03-01
Did you do any upgrades?

The ipw firmware is loaded via hotplug (I think). The firmware is in :

ls -l /lib/hotplug/firmware/ipw*

---

### Post by jerome bettis on 2005-03-01
[QUOTE=alastair]Did you do any upgrades?

The ipw firmware is loaded via hotplug (I think). The firmware is in :

ls -l /lib/hotplug/firmware/ipw*[/QUOTE]
 hmmm ok ... what did you do?  :P

i would try going into /lib/modules/(version)/drivers/net/wireless  and moving the ipw2200.ko (and related) files somwhere else.  then download the source from ipw2200.sf.net and the firmware.  extract the tarball and do sudo make ; sudo make install.  then move all the .fw files to /usr/lib/hotplug/firmware (actually just try the firmware thing first .. then if it doesn't work reinstall the driver).

---

### Post by retrakker on 2005-03-01
Same problem here - are you using Hoary and updated to kernel image 2.6.10-4 ... thats most probably the cause here? I tried to add links with the respective names in /lib/hotplug/firmware but it does not work

Also my USB stopped working and the Realtek module does not get loaded (8139cp) but that was easy to fix through /etc/modules

As far as I understand the situation firmware should be "unaware" of the processor  of the system as it runs on the respective hardware - thus I think it is unnecessary for the linux-restricted-modules package to produce lengthy names like 
ipw2100-1.3.i-2.6.10-4-368.fw etc. pp. 

Maybe that should go into bugzilla? Anyone from the developing team?

---

### Post by mirtux on 2005-03-02
Ok guys, it seems i've found the solution, but a warning: i'm not using Ubuntu but Debian unstable.     ------------> it is due to **udev-0.054-1**, so i've downgraded to udev-0.053 and all the problems vanished!

Hope this can help,
MC

---

