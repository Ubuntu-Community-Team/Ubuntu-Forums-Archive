---
title: "Kernel 2.6.24-21-x does not load intel ipw2200 wifi"
date: 2008-08-24
forum: Hardware
---

### Post by dentaku65 on 2008-08-24
With the update of today of the restricted modules for kernel 2.6.24-21-x, the module of ipw2200 is wrong and does not work

```
dmesg |grep ipw2200
```

```
[   26.154407] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   26.154567] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   26.154622] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   26.154792] ipw2200: disagrees about version of symbol ieee80211_txb_free
[   26.154795] ipw2200: Unknown symbol ieee80211_txb_free
[   26.154879] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   26.155065] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   26.155114] ipw2200: Unknown symbol escape_essid
[   26.155239] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   26.155534] ipw2200: Unknown symbol ieee80211_set_geo
[   26.155711] ipw2200: Unknown symbol ieee80211_rx
[   26.155857] ipw2200: Unknown symbol ieee80211_channel_to_index
[   26.156156] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[   26.156158] ipw2200: Unknown symbol ieee80211_rx_mgt
[   26.156211] ipw2200: Unknown symbol ieee80211_get_geo
[   26.156301] ipw2200: Unknown symbol free_ieee80211
[   26.156548] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   26.156668] ipw2200: Unknown symbol alloc_ieee80211
```

Switch back to 2.6.24-20-x everything is working.

---

### Post by patrickfromspain on 2008-08-24
The -20 and -21 are in hardy proposed, so they are not oficially released, they aren't stable. If you have problems with those, you should report the bugs found in launchpad

---

