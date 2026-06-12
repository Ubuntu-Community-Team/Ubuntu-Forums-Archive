---
title: "madwifi problems"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by Auratus on 2006-03-31
Hey guys,

Ive pretty much tried every guide on these forums to get this to work, but for some reason its not workin for me.  Here's an example of the most recent guide that ive followed outside of the restriced-linux package.
[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=madwifi-ng](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=madwifi-ng)

And here is the output i get from : sudo modprobe ath_pci
```
 id
[4303371.501000] ath_pci: disagrees about version of symbol ieee80211_chan2mode
[4303371.501000] ath_pci: Unknown symbol ieee80211_chan2mode
[4303371.501000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[4303371.501000] ath_pci: Unknown symbol ieee80211_getrssi
[4303371.501000] ath_pci: Unknown symbol ieee80211_pwrsave
[4303371.501000] ath_pci: disagrees about version of symbol ieee80211_find_txnode
[4303371.501000] ath_pci: Unknown symbol ieee80211_find_txnode
[4303371.501000] ath_pci: Unknown symbol ath_rate_newstate
[4303371.501000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4303371.501000] ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
[4303449.109000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303449.109000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303449.170000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303449.170000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303461.506000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303461.506000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303461.570000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303461.570000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303527.379000] ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
[4303527.379000] ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_siwrate
[4303527.381000] ath_pci: Unknown symbol ath_rate_tx_complete
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_encap
[4303527.381000] ath_pci: Unknown symbol ieee80211_encap
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_input
[4303527.381000] ath_pci: Unknown symbol ieee80211_input
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_siwap
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_ifattach
[4303527.381000] ath_pci: Unknown symbol ieee80211_ifattach
[4303527.381000] ath_pci: Unknown symbol if_printf
[4303527.381000] ath_pci: Unknown symbol ieee80211_sysctl_register
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_siwencode
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[4303527.381000] ath_pci: Unknown symbol ieee80211_beacon_update
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_setmlme
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_setoptie
[4303527.381000] ath_pci: Unknown symbol ieee80211_ioctl_giwmode
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_find_rxnode
[4303527.381000] ath_pci: Unknown symbol ieee80211_find_rxnode
[4303527.381000] ath_pci: Unknown symbol ath_rate_attach
[4303527.381000] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[4303527.382000] ath_pci: Unknown symbol ieee80211_ifdetach
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_free_node
[4303527.382000] ath_pci: Unknown symbol ieee80211_free_node
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_siwsens
[4303527.382000] ath_pci: Unknown symbol ath_rate_newassoc
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_notify_michael_failure
[4303527.382000] ath_pci: Unknown symbol ieee80211_notify_michael_failure
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_chanlist
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_getparam
[4303527.382000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[4303527.382000] ath_pci: Unknown symbol ieee80211_dump_pkt
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_giwrate
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_siwrts
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_giwname
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[4303527.382000] ath_pci: Unknown symbol ieee80211_cipher_none
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_setparam
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_siwpower
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_giwsens
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_media_change
[4303527.382000] ath_pci: Unknown symbol ieee80211_media_change
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
[4303527.382000] ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
[4303527.382000] ath_pci: Unknown symbol ieee80211_beacon_alloc
[4303527.382000] ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwap
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
[4303527.383000] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[4303527.383000] ath_pci: Unknown symbol ieee80211_ibss_merge
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwpower
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwrange
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwretry
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwrts
[4303527.383000] ath_pci: Unknown symbol ieee80211_iw_getstats
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_addmac
[4303527.383000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4303527.383000] ath_pci: Unknown symbol ath_rate_detach
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
[4303527.383000] ath_pci: Unknown symbol ieee80211_vlan_kill_vid
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_giwencode
[4303527.383000] ath_pci: Unknown symbol ieee80211_next_scan
[4303527.383000] ath_pci: Unknown symbol ieee80211_media_init
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_iwsetup
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl
[4303527.383000] ath_pci: Unknown symbol ieee80211_ioctl_delmac
[4303527.383000] ath_pci: Unknown symbol ieee80211_classify
[4303527.383000] ath_pci: disagrees about version of symbol ieee80211_media_status
[4303527.384000] ath_pci: Unknown symbol ieee80211_media_status
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_announce
[4303527.384000] ath_pci: Unknown symbol ieee80211_announce
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_setkey
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_delkey
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[4303527.384000] ath_pci: Unknown symbol ieee80211_chan2ieee
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwretry
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
[4303527.384000] ath_pci: Unknown symbol ath_rate_node_init
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwscan
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwmode
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_getoptie
[4303527.384000] ath_pci: Unknown symbol ath_rate_findrate
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_giwessid
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_giwscan
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[4303527.384000] ath_pci: Unknown symbol ieee80211_crypto_encap
[4303527.384000] ath_pci: Unknown symbol ieee80211_vlan_register
[4303527.384000] ath_pci: Unknown symbol ieee80211_ioctl_siwessid
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_chan2mode
[4303527.384000] ath_pci: Unknown symbol ieee80211_chan2mode
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[4303527.384000] ath_pci: Unknown symbol ieee80211_getrssi
[4303527.384000] ath_pci: Unknown symbol ieee80211_pwrsave
[4303527.384000] ath_pci: disagrees about version of symbol ieee80211_find_txnode
[4303527.384000] ath_pci: Unknown symbol ieee80211_find_txnode
[4303527.384000] ath_pci: Unknown symbol ath_rate_newstate
[4303527.384000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4303527.385000] ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
[4303907.481000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303907.481000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303907.542000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303907.542000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4338616.621000] ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
[4338616.621000] ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_siwrate
[4338616.623000] ath_pci: Unknown symbol ath_rate_tx_complete
[4338616.623000] ath_pci: disagrees about version of symbol ieee80211_encap
[4338616.623000] ath_pci: Unknown symbol ieee80211_encap
[4338616.623000] ath_pci: disagrees about version of symbol ieee80211_input
[4338616.623000] ath_pci: Unknown symbol ieee80211_input
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_siwap
[4338616.623000] ath_pci: disagrees about version of symbol ieee80211_ifattach
[4338616.623000] ath_pci: Unknown symbol ieee80211_ifattach
[4338616.623000] ath_pci: Unknown symbol if_printf
[4338616.623000] ath_pci: Unknown symbol ieee80211_sysctl_register
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_siwencode
[4338616.623000] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[4338616.623000] ath_pci: Unknown symbol ieee80211_beacon_update
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_setmlme
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_setoptie
[4338616.623000] ath_pci: Unknown symbol ieee80211_ioctl_giwmode
[4338616.623000] ath_pci: disagrees about version of symbol ieee80211_find_rxnode
[4338616.623000] ath_pci: Unknown symbol ieee80211_find_rxnode

```

However, my ath_hal loads cleanly, so im unsure of what i can do next, I feel like i have tried everything.  If you have any ideas, dont hesitate to aim me at Veritasvincit86 or im on IRC as Auratus as well.

Thanks
Alex

---

