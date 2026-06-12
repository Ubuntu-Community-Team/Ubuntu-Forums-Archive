---
title: "Blinking WiFi LED - Ubuntu  14.04.3 , Compaq 8510w"
date: 2016-01-30
forum: Hardware
---

### Post by michaelrachel on 2016-01-30
I have Compaq 8510w laptop with WiFe LED that blinks when WiFi is active. It is amazingly annoying. 

lspci shows: 
"10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

I have tried adding each of the statements to /etc/modprobe.d/wlan.conf, and rebooting with no success (the WiFi led still blinking):

options iwl_legacy led_mode=1
options iwlagn led_mode=1
options iwlwifi led_mode=1

How can I stop the WiFi led from blinking ? Please help !

---

### Post by weatherman2 on 2016-01-30
You might try this:

```

options iwlegacy led_mode=1

```

(The spelling is important.)

---

### Post by michaelrachel on 2016-01-30
Placed:
 options iwlegacy led_mode=1 in etc/modprobe.d/wlan.conf
Rebooted. No more WiFi LED blinking 

weatherman, thank you.

---

