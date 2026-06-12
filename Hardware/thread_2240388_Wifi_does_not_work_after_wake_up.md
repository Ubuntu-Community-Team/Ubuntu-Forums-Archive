---
title: "Wifi does not work after wake up"
date: 2014-08-19
forum: Hardware
---

### Post by coffeespoon on 2014-08-19
Hallo guys,

please could you help me. After move from 13.10 64bit to  14.4 64bit I've problem with wifi connection after waking up. When I wake up comp there is usually no wifi network found and I have to disable wifi. After enabling wifi it will connect my wifi network automatically.
Some times I see unsaved networks in my neighborhood after wakeup but my network is neither connected nor seen.
I tried a lots of solution without any impact.

My wifi 
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

I am not sure if it is problem but I found this in /vae/log/pm-powersave.log

```
Running hook /usr/lib/pm-utils/power.d/wireless false:
cat: /sys/class/net/wlan0/device/enable: No such file or directory
/usr/lib/pm-utils/power.d/wireless false: success.

```

and  similar error in /var/log/pm-suspend.log

```
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

```

Please could you advise me how to solve it?

Thanks in advance.

---

