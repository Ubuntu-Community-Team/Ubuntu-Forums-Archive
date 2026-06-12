---
title: "Wireless not working on Aspire 5315-2639 in 8.10"
date: 2008-11-29
forum: Hardware
---

### Post by dragonwisard on 2008-11-29
My sister recently bought an Acer Aspire 5315-2639 (because it was cheap) and then later decided she wanted to use Linux. I installed Ubuntu 8.10 and everything seems to be working fine with the rather important exception of the wireless adapter.

lspci reports:
```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I installed 'linux-backports-modules-intrepid' as suggested in one thread for a similar model, but that didn't seem to help. Can anyone point me in the right direction?

Edit:
I tried this guide: [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

But loading ath5k failed with "Unknown symbol in module, or unknown parameter (see dmesg)".

The relevant dmesg:
```
[12028.488184] ath5k: Unknown symbol lbm_cw_ieee80211_frequency_to_channel
[12028.488620] ath5k: Unknown symbol lbm_cw_ieee80211_get_hdrlen_from_skb
[12028.488780] ath5k: Unknown symbol lbm_cw_ieee80211_alloc_hw
[12028.489236] ath5k: Unknown symbol lbm_cw_ieee80211_tx_status
[12028.489510] ath5k: Unknown symbol lbm_cw_lbm_cw_ieee80211_stop_queues
[12028.489682] ath5k: Unknown symbol lbm_cw_ieee80211_hdrlen
[12028.489848] ath5k: Unknown symbol lbm_cw_ieee80211_register_hw
[12028.490230] ath5k: Unknown symbol lbm_cw_ieee80211_stop_queue
[12028.490622] ath5k: Unknown symbol lbm_cw_ieee80211_free_hw
[12028.490792] ath5k: Unknown symbol lbm_cw_lbm_cw_ieee80211_wake_queues
[12028.490999] ath5k: Unknown symbol lbm_cw_ieee80211_generic_frame_duration
[12028.491160] ath5k: Unknown symbol lbm_cw_ieee80211_beacon_get
[12028.491344] ath5k: Unknown symbol lbm_cw_ieee80211_unregister_hw
[12028.491488] ath5k: Unknown symbol lbm_cw___ieee80211_get_rx_led_name
[12028.491631] ath5k: Unknown symbol lbm_cw___ieee80211_get_tx_led_name
[12028.492108] ath5k: Unknown symbol __lbm_cw_ieee80211_rx
```

Any ideas?

---

### Post by dragonwisard on 2008-12-02
Bump.Not sure if that's acceptable here, but it's been a few days with no replies. 

Does anyone have any advice or should I just replace the card with an IPW3945 card?

---

### Post by MockY on 2008-12-20
*empty*

---

