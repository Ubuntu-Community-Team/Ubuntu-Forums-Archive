---
title: "Support for ar242x wireless"
date: 2008-11-05
forum: Hardware
---

### Post by 000dom000 on 2008-11-05
I have intrepid installed, knowing that the ath5k drivers should load for what ubuntu sees as my ar242x wireless adapter.

I have tried blacklisting the ath-pci and ath-hal and also installing linux-backports-modules-intrepid which was also suggested here:

[http://ubuntuforums.org/showthread.php?t=940048](http://ubuntuforums.org/showthread.php?t=940048)

I can currently see a wlan0 in iwconfig.

iwlist scan gives me:
```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


```

wheras

sudo iwlist scan gives me:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```


nm applet reinforces this as it tells has a heading for wireless networks but there are none scanned.

lspci:
```

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```


Thanks for any help

---

