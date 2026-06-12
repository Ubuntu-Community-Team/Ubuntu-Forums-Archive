---
title: "Intel Corporation PRO/Wireless 4965 and Aircrack"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by eatayeh on 2009-08-27
Hello,

I am trying to get aircrack to work but wasn't successful so far.

I followed the steps here: "http://linuxwireless.org/en/users/Download" to install the latest intel driver.


However when i run $ modprobe mac80211

I get:

FATAL: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/kernel/net/wireless/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$dmesg would give...:
..........
[ 1331.405772] mac80211: Unknown symbol wiphy_register
[ 1331.405977] mac80211: Unknown symbol wiphy_new
[ 1331.408642] mac80211: Unknown symbol wiphy_unregister
[ 1331.409114] mac80211: Unknown symbol ieee80211_radiotap_iterator_init
[ 1331.409437] mac80211: Unknown symbol __ieee80211_get_channel
[ 1331.410832] mac80211: Unknown symbol ieee80211_radiotap_iterator_next
[ 1331.411071] mac80211: Unknown symbol ieee80211_channel_to_frequency
[ 1331.412485] mac80211: Unknown symbol ieee80211_frequency_to_channel
[ 1331.413503] mac80211: Unknown symbol wiphy_free
[ 1438.968708] wlan0: beacon loss from AP f63766b8 - sending probe request


Any ideas?

Thanks a million!

---

