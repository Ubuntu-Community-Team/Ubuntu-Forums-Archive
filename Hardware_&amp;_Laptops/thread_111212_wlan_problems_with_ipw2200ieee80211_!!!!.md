---
title: "wlan problems with ipw2200/ieee80211 !!!!"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by dynamo on 2006-01-01
good morning!

well i tried a lot and don't know, why it isn't working.
old and new drivers of ipw2200 give the same errors as follows:
(i was so happy, that i could compile it at last, but than...)

a "modprobe ipw2200" gives (/var/log/syslog) following errors:
> ieee80211_crypt: unregistered algorith 'NULL' (deinit)
ieee80211_crypt: registered algorithm 'NULL'
ieee80211_crypt: 802.11 data/management/control stack 1.1.6
ieee80211_crypt: Copyright (C) 2003-2005 Intel Corporation
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.7
ipw2200: Copyright(c) 2003-2005 Intel Corporation
ipw2200 Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200:Radio Frequenzy Kill Switch is On:
Kill switch must be turned off for wireless networking to work

note: there is a switch(hardware) for giving power to the wlan card and this is the message, when the switch is turned off.

if wlan is switched on, following comes:

> ieee80211_crypt: unregistered algorith 'NULL' (deinit)
ieee80211_crypt: registered algorithm 'NULL'
ieee80211_crypt: 802.11 data/management/control stack 1.1.6
ieee80211_crypt: Copyright (C) 2003-2005 Intel Corporation
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.7
ipw2200: Copyright(c) 2003-2005 Intel Corporation
ipw2200 Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Unable to initialize device after 5 attempts.
ipw2200: failed to register network device
ipw2200: probe of 0000:06:04.0 failed with error -5

could this be a hardware problem with the switch?!

another thing is, if the switch is turned on, "modprobe ipw2200" goes much faster and iwconfig shows the interface. it says "radio off" and that's so true :] after switching on, it shows "unassociated" ... isn't that funny?

the other way round, when switched on, an "iwconfig" gives nothing.

please help me, or give me a direction to search for more possible reasons, why this thing isn't working. ah, i'm using Kubuntu with 1.6.12 kernel version.
the card works under Ubuntu, but not Kubuntu! hm

i'm done, thanks for answers!

dnm :confused:

---

### Post by dynamo on 2006-01-02
solved it! 

looked after firmware in /lib/firmware where i placed it once, but it wasn't there any more. so i exported it in

/lib/firmware
/etc/firmware and
/usr/lib/hotplug

than i restarted and everything went "ok"!

dnm

---

