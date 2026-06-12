---
title: "Wlan iwlwifi dmesg error"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by atlas95 on 2007-10-19
Hello, I have a lot of wlan error all second when i'm connect on wifi, how to disable it???


```
Oct 19 14:53:05 localhost kernel: [18241.020000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:05 localhost kernel: [18241.320000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:06 localhost kernel: [18241.620000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:06 localhost kernel: [18242.220000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:07 localhost kernel: [18242.520000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:07 localhost kernel: [18242.820000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:07 localhost kernel: [18243.120000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:08 localhost kernel: [18243.720000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:08 localhost kernel: [18244.020000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:08 localhost kernel: [18244.324000] wlan0: RX non-WEP frame, but expected encryption
Oct 19 14:53:09 localhost kernel: [18244.620000] wlan0: RX non-WEP frame, but expected encryption
```

Regards

---

### Post by jbernardo on 2007-11-25
I have exactly the same crap filling the logs with a Ralink RT2500 pci adapter. The connection is also extremely unstable to my wrt54l running dd-wrt. It is enough for someone to pass between the pc and the ap to trigger a reconnection. Any ideas?

---

### Post by atlas95 on 2007-12-12
Any idea?
This cause my hdd always write for nothing :( I always have those errors

---

### Post by jbernardo on 2007-12-12
I'm afraid we'll have to wait for a update of the wifi drivers to solve that. I have yet to find a solution.

---

