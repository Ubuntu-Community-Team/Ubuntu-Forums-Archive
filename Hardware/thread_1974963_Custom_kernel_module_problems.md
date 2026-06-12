---
title: "Custom kernel module problems"
date: 2012-05-06
forum: Hardware
---

### Post by xtjacob on 2012-05-06
hello, I just finished compiling and installing the 3.3.4 kernel for my computer and when I boot up into it my Atheros wireless card will not work. I tried to modprobe the module in and I got this error:
```
jacob@jacob-ubuntu:~$ sudo modprobe ath9k
[sudo] password for jacob: 
WARNING: Error inserting ath9k_hw (/lib/modules/3.3.4/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/3.3.4/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/3.3.4/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Dmesg said:
```
jacob@jacob-ubuntu:~$ dmesg | tail
[ 1909.401433] sd 7:0:0:0: [sdc] Write Protect is off
[ 1909.401440] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 1909.403409] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1909.417032]  sdc: sdc1 < sdc5 >
[ 1909.423411] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 1922.537828] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1922.540943] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1922.540948] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1944.786103] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 1944.786126] ath: Unknown symbol freq_reg_info (err 0)
```

I tried using a different wireless card and it doesn't work either. Dmesg said:
```
jacob@jacob-ubuntu:~$ dmesg | tail
[ 1984.891643] rt2x00lib: Unknown symbol ieee80211_tx_status (err 0)
[ 1984.891650] rt2x00lib: Unknown symbol ieee80211_stop_queue (err 0)
[ 1984.891658] rt2x00lib: Unknown symbol ieee80211_stop_queues (err 0)
[ 1984.891669] rt2x00lib: Unknown symbol wiphy_rfkill_start_polling (err 0)
[ 1984.891677] rt2x00lib: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err 0)
[ 1984.891690] rt2x00lib: Unknown symbol ieee80211_channel_to_frequency (err 0)
[ 1984.891698] rt2x00lib: Unknown symbol ieee80211_unregister_hw (err 0)
[ 1984.891709] rt2x00lib: Unknown symbol ieee80211_beacon_get_tim (err 0)
[ 1984.891717] rt2x00lib: Unknown symbol ieee80211_rts_get (err 0)
[ 1984.891729] rt2x00lib: Unknown symbol ieee80211_queue_work (err 0)
```

I have no idea what is wrong. Please help!:confused:

---

