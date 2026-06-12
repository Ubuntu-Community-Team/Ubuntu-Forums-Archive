---
title: "My USB WiFi works on 16.04 but not on 14.04"
date: 2017-03-10
forum: Hardware
---

### Post by rahul_bhise on 2017-03-10
I have a [USB 2.0 wireless LV-UW03]("http://www.amazon.in/Receiver-300Mbps-802-11b-Wireless-Network/dp/B0141EZMAI?_encoding=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s01") bought on amazon [hear]("http://amzn.in/9EYjqON")
It Work perfectly out of the box on my Ubuntu 16.04. But on my Ubuntu 14.04 nothing happens

On 14.04
```
rahul@PC1404ME:~$ **lsusb**
**Bus 002 Device 003: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter**
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

On 16.04
```
bhagya@bhagya:~$ sudo lshw -C network
  
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.6
       logical name: wlx20e41601aa3b
       serial: 20:e4:16:01:aa:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=4.4.0-64-generic firmware=N/A ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11bgn

```

what should i do so it gets detected on 14.04 also
i have also got a cd with it. with windows and linux drivers but i dont know how to install a driver on linux.
also there are 3 folders i dont know which one to install.
[URL="https://www.dropbox.com/sh/28ld7bznllfz74j/AAA53Op4q2dBgpwhy9_TCWw9a?dl=0"]1>DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2
2>mt7610u_wifi_sta_v3002_dpo_20130916.tar.bz2
3>MT7612U_DPO_LinuxSTA_3.0.0.1_20140718.tar.bz2[/URL]

---

### Post by mörgæs on 2017-03-10
Why do you want to keep 14.04 if you know that it works well on 16.04?

---

### Post by rahul_bhise on 2017-03-10
the 16.04 is for my daughter i always keep it to the latest.
But the 14.04 setup is for me.
I have lots of applications set it up and fine tune it.
also some windows application like Tally in WINE.
now to take all of them to a new fresh setup requires time, lots and lots of time.... and asking question on forums.... and googling some of them.
upgrading OS always gives a lot of problem then fresh install.

---

### Post by rahul_bhise on 2017-03-14
bump

---

### Post by kurt18947 on 2017-03-14
A couple thoughts but I am not an expert by any definition. The driver for that device is in recent kernels but not in the default kernels used by 14.x.  

- One thought would be to enable wireless backports - I haven't had to mess with backports in years so am not sure if they even still exist.

- Would using a 4.4.x  kernel in your 14.x install break things?

Again, I don't know if either of these solutions are viable for you. SWMBO is using Xubuntu 14.04 which goes out of support in April. I'm not looking forward to moving all her tweaks and customizations. I guess I should be smart this time around and make a separate /home for her.

---

### Post by rahul_bhise on 2017-04-16
I tried lots of things. and nothing helped. but then
 something went wrong. i dont know what.
And i hade to do a complete new install.
The mess-up was so deep i was not able to recover the Firefox .default folder.
Lots of things were lost. Though nothing much important, because i had a separate partition for Videos, Music, Pictures and Document.
But after a month I say all is fine now

---

