---
title: "[CRITICAL] iwl3945 not working on secured wireless networks"
date: 2008-04-26
forum: Hardware
---

### Post by DoDoENT on 2008-04-26
Please help, people. I have Intel PRO/Wireless 3945 ABG Card, and I can't connect to my university's secured WLAN. On gutsy, I used ipw3945 and authentication worked with wpa_supplicant, but now on hardy it doesn't work anymore. Any solution?

Here is the output of wpa_supplicant while trying to connect to the wireless network:

dodo@2nd-of-12:~$ sudo wpa_supplicant -D wext -i wlan0 -c /home/dodo/wpa_supplicant/FERwlan.conf
Trying to associate with 00:40:96:54:28:37 (SSID='FERwlan' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:40:96:54:28:37 (SSID='FERwlan' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:40:96:54:28:37 (SSID='FERwlan' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
... and so on

On some thread I found that it is a kernel issue, but I applied the required patch (2.6.24-16 should have this patch applied) and it still doesn't work. Any ideas?

Btw. I tried compiling the ipw3945 driver, but compilation always fails.

---

### Post by oodlesOfmoodles on 2008-04-26
I too am having this problem. I am going to have to downgrade to 7.10 because of this.

This is really frustrating.

A bug report has been filed at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220640]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220640")

---

### Post by oodlesOfmoodles on 2008-04-26
Those who find this thread useful please "digg" up this brainstorm that I filed.

[http://brainstorm.ubuntu.com/idea/6281/]("http://brainstorm.ubuntu.com/idea/6281/")

---

