---
title: "ndiswrappers and breezy"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by jrattner on 2005-10-14
(bcmwl5.inf is my driver)

I installed ndiswrappers from synaptic:

ndiswrapper-source
ndiswrapper-utils

Then I did:

ndiswrapper -i ~/home/jrattner/build/bcmwl5.inf

(In that directory is bcml5.inf and bcml5.sys)
-------------------------------

ndiswrapper -l it says:

Installed ndis drivers:
bcmwl5  driver present, hardware present
--------------------------------------

I also ran ndiswrapper -m and it says

modprobe config already contains alias directive
------------------------------------

And then if i type modprobe ndiswrapper I get 

FATAL: Module ndiswrapper not found.


Why cant it find the module it doesnt make sense? I need my wlan in breezy :(

---

### Post by spd106 on 2005-10-15
Try **sudo updatedb** then **sudo locate ndiswrapper** it should turn up the ndiswrapper.ko kernel module. I forget where. 

Also, you can only insert kernel modules as root (ie sudo modprobe).

Happy Hunting

spd106

---

### Post by jrattner on 2005-10-15
Ive located the .ko file what should i do next???


:) 
lib/modules/2.6.12-9-686-smp/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/src/ndiswrapper-1.4/driver/ndiswrapper.ko
/usr/src/ndiswrapper-1.4/driver/.ndiswrapper.ko.cmd

---

