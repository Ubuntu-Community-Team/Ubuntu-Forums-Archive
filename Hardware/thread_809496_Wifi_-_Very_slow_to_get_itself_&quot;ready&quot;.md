---
title: "Wifi - Very slow to get itself &quot;ready&quot;"
date: 2008-05-27
forum: Hardware
---

### Post by b3n87 on 2008-05-27
Hey,

My WiFi card takes a very long time to become "ready" to use, I have my WEP key saved so that it asks me for my password when its ready to connect to the WiFi network

Take a look at my dmesg output and see how long it takes to get itself ready from undoing the kill switch

```
[  127.774980] usb 1-1: USB disconnect, address 2
[  127.791098] iwl4965: Radio Frequency Kill Switch is On:
[  127.791103] Kill switch must be turned off for wireless networking to work.
[  130.526171] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  130.699538] usb 1-1: configuration #1 chosen from 1 choice
[  133.131009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  218.228852] NET: Registered protocol family 17
[  230.377238] wlan0: Initial auth_alg=0
[  230.377249] wlan0: authenticate with AP 00:1e:2a:1e:53:92
[  230.399624] wlan0: authenticate with AP 00:1e:2a:1e:53:92
[  230.400542] wlan0: RX authentication from 00:1e:2a:1e:53:92 (alg=0 transaction=2 status=0)
[  230.400550] wlan0: authenticated
[  230.400555] wlan0: associate with AP 00:1e:2a:1e:53:92
[  230.401969] wlan0: authentication frame received from 00:1e:2a:1e:53:92, but not in authenticate state - ignored
[  230.424176] wlan0: associate with AP 00:1e:2a:1e:53:92
[  230.425283] wlan0: RX AssocResp from 00:1e:2a:1e:53:92 (capab=0x431 status=0 aid=1)
[  230.425291] wlan0: associated
[  230.425399] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  230.429807] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  230.442171] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  230.442769] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  230.443319] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  230.444073] wlan0: association frame received from 00:1e:2a:1e:53:92, but not in associate state - ignored
[  232.258277] wlan0: no IPv6 routers present

```

Thats over a minute and a half from undoing the kill switch to connecting to my network.

Does anyone know how to improve this and any reasons why its so slow?

Thanks in advance!

---

### Post by b3n87 on 2008-05-28
Any ideas?

Could it be a hardware problem - if so how can i check this?

---

### Post by sshlyk on 2008-05-28
why do you need kill switch?

---

### Post by b3n87 on 2008-05-28
The wifi didnt seem to be connecting or finding any wifi points, so i used the kill switch, re-enabled it and tried again, after that I just waited to see how long it would take to find anything. Which was a long time.

---

### Post by sshlyk on 2008-05-28
> **b3n87 said:**
> The wifi didnt seem to be connecting or finding any wifi points, so i used the kill switch, re-enabled it and tried again, after that I just waited to see how long it would take to find anything. Which was a long time.


I had similar problems with my intel wireless after suspend mode. In Ununtu 8.04 this problems seems to be fixed. 
I believe your hardware takes as much time as it needs ;)

---

