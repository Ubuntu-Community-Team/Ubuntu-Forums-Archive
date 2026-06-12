---
title: "Question about wireless intenet for laptop"
date: 2008-11-18
forum: General Help
---

### Post by sbriggman on 2008-11-18
Hi,

I have a Compaq Presario V5101us. I tried to use internet in ubuntu and it wouldn't work. The wireless buttons arn't clickable. It's like it's not picking up the signal. It tried punching in the name of the network and the wep key and it still wouldn't work.

I went to the help menu and asked it what to do. It said to enter a command and this was the terminal's response

*-network:0 DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:7b:3d:21
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: ee:b2:17:4e:d1:65
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ *-network:0 DISABLED

So, it says it's disabled... well... how do I enable it. When I go into windows, wireless works fine. Just ubuntu won't let me use it. What should I do.

---

### Post by rampageoberon on 2008-11-18
Try the following code

```
sudo ifup wlan0
sudo ifup pan0
```

Hope that works

---

