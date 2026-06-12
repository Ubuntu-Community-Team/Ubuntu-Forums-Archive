---
title: "No ipw2200 after 24/5 kernel update"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by gasparov on 2005-05-25
Hi,
   just to point out that on my compaq/hp nx9030 ipw stopped working with with last 2.6.10-5-686 kernel,everything is cool with 2.6.10-5-386 ,even the utton to turn off/on the wireless work now.Was I  using the wrong kernel or the issue is differnet?

```
gas@notebook:~$ dmesg|grep ipw
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_freq_to_channel
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_get_geo
ipw2200: Unknown symbol ieee80211_is_valid_channel
gas@notebook:~$

```

---

### Post by luca_linux on 2005-05-26
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by gasparov on 2005-05-26
[QUOTE=luca_linux]Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]
 thanks luca but I've already followed that how-to,that's how I managed to get latest firmware and drivers.The fact is that everything was working after following your suggestions but after that upgrade is not anymore ,it just seemed stranged to me and don't know why (<kernel vers>?).However everything goes smooth with -386 kernel and don' have a clue.In any case I'll have look in my system re-viewing howto steps...

---

### Post by Arthemys on 2005-05-27
I had to do the howto -again- after having that patch installed. It's a weird quirk but it did work for me.

---

