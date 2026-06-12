---
title: "Hawking HWUG1 Not Working"
date: 2008-07-18
forum: Hardware
---

### Post by oxsyn on 2008-07-18
When I insert it, I see the following mesages in /var/log/messages:

> Jul 17 23:11:46 poisontongue kernel: [  707.308967] usb 5-5: USB disconnect, address 2
Jul 17 23:11:51 poisontongue kernel: [  708.597874] usb 5-5: new high speed USB device using ehci_hcd and address 4
Jul 17 23:11:51 poisontongue kernel: [  708.868914] usb 5-5: configuration #1 chosen from 1 choice
Jul 17 23:11:51 poisontongue kernel: [  708.966345] rt2x00lib: Unknown symbol ieee80211_register_hw
Jul 17 23:11:51 poisontongue kernel: [  708.966458] rt2x00lib: Unknown symbol ieee80211_tx_status_irqsafe
Jul 17 23:11:51 poisontongue kernel: [  708.966609] rt2x00lib: Unknown symbol ieee80211_ctstoself_get
Jul 17 23:11:51 poisontongue kernel: [  708.966661] rt2x00lib: Unknown symbol ieee80211_start_queues
Jul 17 23:11:51 poisontongue kernel: [  708.966765] rt2x00lib: Unknown symbol ieee80211_stop_queues
Jul 17 23:11:51 poisontongue kernel: [  708.966890] rt2x00lib: Unknown symbol ieee80211_unregister_hw
Jul 17 23:11:51 poisontongue kernel: [  708.967026] rt2x00lib: Unknown symbol ieee80211_rts_get
Jul 17 23:11:51 poisontongue kernel: [  708.967076] rt2x00lib: Unknown symbol ieee80211_beacon_get
Jul 17 23:11:51 poisontongue kernel: [  708.967200] rt2x00lib: Unknown symbol ieee80211_register_hwmode
Jul 17 23:11:51 poisontongue kernel: [  708.967256] rt2x00lib: Unknown symbol ieee80211_rx_irqsafe
Jul 17 23:11:51 poisontongue kernel: [  708.969135] rt2x00usb: Unknown symbol rt2x00lib_suspend
Jul 17 23:11:51 poisontongue kernel: [  708.969197] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
Jul 17 23:11:51 poisontongue kernel: [  708.969306] rt2x00usb: Unknown symbol ieee80211_free_hw
Jul 17 23:11:51 poisontongue kernel: [  708.969356] rt2x00usb: Unknown symbol ieee80211_alloc_hw
Jul 17 23:11:51 poisontongue kernel: [  708.969412] rt2x00usb: Unknown symbol ieee80211_wake_queue
Jul 17 23:11:51 poisontongue kernel: [  708.969548] rt2x00usb: Unknown symbol rt2x00lib_rxdone
Jul 17 23:11:51 poisontongue kernel: [  708.969717] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
Jul 17 23:11:51 poisontongue kernel: [  708.969787] rt2x00usb: Unknown symbol rt2x00lib_txdone
Jul 17 23:11:51 poisontongue kernel: [  708.969837] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
Jul 17 23:11:51 poisontongue kernel: [  708.969936] rt2x00usb: Unknown symbol ieee80211_stop_queue
Jul 17 23:11:51 poisontongue kernel: [  708.969986] rt2x00usb: Unknown symbol ieee80211_get_hdrlen
Jul 17 23:11:51 poisontongue kernel: [  708.970035] rt2x00usb: Unknown symbol rt2x00lib_resume
Jul 17 23:11:51 poisontongue kernel: [  708.971841] rt2500usb: Unknown symbol rt2x00mac_add_interface
Jul 17 23:11:51 poisontongue kernel: [  708.971892] rt2500usb: Unknown symbol rt2x00mac_get_stats
Jul 17 23:11:51 poisontongue kernel: [  708.971991] rt2500usb: Unknown symbol rt2x00usb_disable_radio
Jul 17 23:11:51 poisontongue kernel: [  708.972040] rt2500usb: Unknown symbol rt2x00usb_enable_radio
Jul 17 23:11:51 poisontongue kernel: [  708.972090] rt2500usb: Unknown symbol rt2x00usb_vendor_request_buff
Jul 17 23:11:51 poisontongue kernel: [  708.972139] rt2500usb: Unknown symbol rt2x00lib_get_ring
Jul 17 23:11:51 poisontongue kernel: [  708.972275] rt2500usb: Unknown symbol rt2x00usb_write_tx_data
Jul 17 23:11:51 poisontongue kernel: [  708.972324] rt2500usb: Unknown symbol rt2x00mac_config_interface
Jul 17 23:11:51 poisontongue kernel: [  708.972374] rt2500usb: Unknown symbol rt2x00mac_remove_interface
Jul 17 23:11:51 poisontongue kernel: [  708.972424] rt2500usb: Unknown symbol rt2x00usb_vendor_request
Jul 17 23:11:51 poisontongue kernel: [  708.972473] rt2500usb: Unknown symbol rt2x00usb_probe
Jul 17 23:11:51 poisontongue kernel: [  708.972522] rt2500usb: Unknown symbol rt2x00mac_config
Jul 17 23:11:51 poisontongue kernel: [  708.972572] rt2500usb: Unknown symbol rt2x00lib_write_tx_desc
Jul 17 23:11:51 poisontongue kernel: [  708.972621] rt2500usb: Unknown symbol rt2x00usb_suspend
Jul 17 23:11:51 poisontongue kernel: [  708.972671] rt2500usb: Unknown symbol rt2x00mac_conf_tx
Jul 17 23:11:51 poisontongue kernel: [  708.972720] rt2500usb: Unknown symbol rt2x00mac_start
Jul 17 23:11:51 poisontongue kernel: [  708.972770] rt2500usb: Unknown symbol rt2x00mac_stop
Jul 17 23:11:51 poisontongue kernel: [  708.972870] rt2500usb: Unknown symbol rt2x00usb_disconnect
Jul 17 23:11:51 poisontongue kernel: [  708.972919] rt2500usb: Unknown symbol rt2x00mac_tx
Jul 17 23:11:51 poisontongue kernel: [  708.972982] rt2500usb: Unknown symbol rt2x00mac_erp_ie_changed
Jul 17 23:11:51 poisontongue kernel: [  708.973055] rt2500usb: Unknown symbol rt2x00mac_get_tx_stats
Jul 17 23:11:51 poisontongue kernel: [  708.973126] rt2500usb: Unknown symbol rt2x00usb_resume
Jul 17 23:11:51 poisontongue kernel: [  708.973183] rt2500usb: Unknown symbol rt2x00usb_uninitialize
Jul 17 23:11:51 poisontongue kernel: [  708.973232] rt2500usb: Unknown symbol rt2x00usb_initialize
Jul 17 23:11:51 poisontongue kernel: [  709.002220] rt2x00lib: Unknown symbol ieee80211_register_hw
Jul 17 23:11:51 poisontongue kernel: [  709.002332] rt2x00lib: Unknown symbol ieee80211_tx_status_irqsafe
Jul 17 23:11:51 poisontongue kernel: [  709.002482] rt2x00lib: Unknown symbol ieee80211_ctstoself_get
Jul 17 23:11:51 poisontongue kernel: [  709.002535] rt2x00lib: Unknown symbol ieee80211_start_queues
Jul 17 23:11:51 poisontongue kernel: [  709.002639] rt2x00lib: Unknown symbol ieee80211_stop_queues
Jul 17 23:11:51 poisontongue kernel: [  709.002764] rt2x00lib: Unknown symbol ieee80211_unregister_hw
Jul 17 23:11:51 poisontongue kernel: [  709.002900] rt2x00lib: Unknown symbol ieee80211_rts_get
Jul 17 23:11:51 poisontongue kernel: [  709.002950] rt2x00lib: Unknown symbol ieee80211_beacon_get
Jul 17 23:11:51 poisontongue kernel: [  709.003073] rt2x00lib: Unknown symbol ieee80211_register_hwmode
Jul 17 23:11:51 poisontongue kernel: [  709.003129] rt2x00lib: Unknown symbol ieee80211_rx_irqsafe
Jul 17 23:11:51 poisontongue kernel: [  709.004986] rt2x00usb: Unknown symbol rt2x00lib_suspend
Jul 17 23:11:51 poisontongue kernel: [  709.005037] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
Jul 17 23:11:51 poisontongue kernel: [  709.005157] rt2x00usb: Unknown symbol ieee80211_free_hw
Jul 17 23:11:51 poisontongue kernel: [  709.005208] rt2x00usb: Unknown symbol ieee80211_alloc_hw
Jul 17 23:11:51 poisontongue kernel: [  709.005264] rt2x00usb: Unknown symbol ieee80211_wake_queue
Jul 17 23:11:51 poisontongue kernel: [  709.005399] rt2x00usb: Unknown symbol rt2x00lib_rxdone
Jul 17 23:11:51 poisontongue kernel: [  709.005567] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
Jul 17 23:11:51 poisontongue kernel: [  709.005637] rt2x00usb: Unknown symbol rt2x00lib_txdone
Jul 17 23:11:51 poisontongue kernel: [  709.005687] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
Jul 17 23:11:51 poisontongue kernel: [  709.005786] rt2x00usb: Unknown symbol ieee80211_stop_queue
Jul 17 23:11:51 poisontongue kernel: [  709.005836] rt2x00usb: Unknown symbol ieee80211_get_hdrlen
Jul 17 23:11:51 poisontongue kernel: [  709.005885] rt2x00usb: Unknown symbol rt2x00lib_resume
Jul 17 23:11:51 poisontongue kernel: [  709.008330] rt73usb: Unknown symbol rt2x00mac_add_interface
Jul 17 23:11:51 poisontongue kernel: [  709.008383] rt73usb: Unknown symbol rt2x00mac_get_stats
Jul 17 23:11:51 poisontongue kernel: [  709.008481] rt73usb: Unknown symbol rt2x00usb_disable_radio
Jul 17 23:11:51 poisontongue kernel: [  709.008531] rt73usb: Unknown symbol rt2x00usb_enable_radio
Jul 17 23:11:51 poisontongue kernel: [  709.008586] rt73usb: Unknown symbol rt2x00usb_vendor_request_buff
Jul 17 23:11:51 poisontongue kernel: [  709.008662] rt73usb: Unknown symbol rt2x00usb_write_tx_data
Jul 17 23:11:51 poisontongue kernel: [  709.008712] rt73usb: Unknown symbol rt2x00mac_config_interface
Jul 17 23:11:51 poisontongue kernel: [  709.008762] rt73usb: Unknown symbol rt2x00mac_remove_interface
Jul 17 23:11:51 poisontongue kernel: [  709.008811] rt73usb: Unknown symbol rt2x00usb_vendor_request
Jul 17 23:11:51 poisontongue kernel: [  709.008860] rt73usb: Unknown symbol rt2x00usb_probe
Jul 17 23:11:51 poisontongue kernel: [  709.008910] rt73usb: Unknown symbol rt2x00mac_config
Jul 17 23:11:51 poisontongue kernel: [  709.008959] rt73usb: Unknown symbol rt2x00lib_write_tx_desc
Jul 17 23:11:51 poisontongue kernel: [  709.009009] rt73usb: Unknown symbol rt2x00usb_suspend
Jul 17 23:11:51 poisontongue kernel: [  709.009058] rt73usb: Unknown symbol rt2x00mac_conf_tx
Jul 17 23:11:51 poisontongue kernel: [  709.009120] rt73usb: Unknown symbol rt2x00mac_start
Jul 17 23:11:51 poisontongue kernel: [  709.009169] rt73usb: Unknown symbol rt2x00mac_stop
Jul 17 23:11:51 poisontongue kernel: [  709.009269] rt73usb: Unknown symbol rt2x00usb_disconnect
Jul 17 23:11:51 poisontongue kernel: [  709.009318] rt73usb: Unknown symbol rt2x00mac_tx
Jul 17 23:11:51 poisontongue kernel: [  709.009381] rt73usb: Unknown symbol rt2x00mac_erp_ie_changed
Jul 17 23:11:51 poisontongue kernel: [  709.009454] rt73usb: Unknown symbol rt2x00mac_get_tx_stats
Jul 17 23:11:51 poisontongue kernel: [  709.009520] rt73usb: Unknown symbol rt2x00usb_resume
Jul 17 23:11:51 poisontongue kernel: [  709.009570] rt73usb: Unknown symbol rt2x00usb_uninitialize
Jul 17 23:11:51 poisontongue kernel: [  709.009619] rt73usb: Unknown symbol rt2x00usb_initialize
Help?

---

### Post by oxsyn on 2008-07-18
I finally found the answer here: [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

---

