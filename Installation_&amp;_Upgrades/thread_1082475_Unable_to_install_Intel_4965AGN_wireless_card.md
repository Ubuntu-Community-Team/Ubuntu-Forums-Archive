---
title: "Unable to install Intel 4965AGN wireless card"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by cipher_lx on 2009-02-27
Hi, 

I followed the instructions given in the link [http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

but when I ran the 'make install' I get the following error?

make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.

I'm not sure what this means?

---

### Post by hansdown on 2009-02-27
Hi cipher_lx.

This part should be a warning.

```
NOTE: The iwlwifi driver is experimental and may not work for you. YMMV.
```


You may be able to find help here, if you are using 8.10.


[http://www.google.ca/search?q=install+Intel+4965AGN+wireless+card+in+ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=install+Intel+4965AGN+wireless+card+in+ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by cipher_lx on 2009-02-28
Hi Hansdown,

Thank you for the google link. but no success... I went to couple of other sites including intellinuxwireless.org and install the driver listed.

I was able to successfully build and load the driver to the kernal. But still the hardware does not work.

I don't see wlan0 as a installed network interface. also, here is the output for few commands.

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:80:09:cf  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe80:9cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2938789 (2.9 MB)  TX bytes:269170 (269.1 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr ae:54:30:1f:58:e3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Output of "lshw -C network"
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:80:09:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 latency=64 link=yes maxlatency=255 mingnt=6 module=pcnet32 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:b8:b9:b2:3c:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Here is the output of "iwconfig"

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


Output of "iwlist scan"

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Can anyone help who had similar issues with installing inbuilt Intel 4965 wireless on an HP laptop

---

### Post by cipher_lx on 2009-03-01
Laptop: HP dv6000t
Ubuntu 8.10
Environment: Ubuntu is running as a guest under Windows Visa host OS

I have installed the latest drivers from intel linux wirelss org website. Following are the actions, I already performed:

Installed linux header: sudo aptitude install linux-headers-$(uname -r)

Downloaded and installed following driver:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)


Here is the output of few commands...

**cipher_lx:~$ uname -rm**
2.6.27-11-generic i686

**cipher_lx:~$] sudo iwlist sca**n
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

**cipher_lx:~$ dmesg | tail -50**
[  428.808190] iwlagn: Unknown symbol iwl_rx_statistics
[  428.808320] iwlagn: Unknown symbol iwl_setup_mac
[  428.808450] iwlagn: Unknown symbol iwl_update_tkip_key
[  428.808588] iwlagn: Unknown symbol iwl_send_cmd
[  428.808735] iwlagn: Unknown symbol iwl_tx_skb
[  428.808906] iwlagn: Unknown symbol iwl_power_enable_management
[  428.809037] iwlagn: Unknown symbol iwl_isr
[  428.809167] iwlagn: Unknown symbol iwl_tx_agg_start
[  428.809391] iwlagn: Unknown symbol iwl_tx_queue_reclaim
[  428.809521] iwlagn: Unknown symbol iwl_disable_interrupts
[  428.809706] iwlagn: Unknown symbol iwl_eeprom_check_version
[  428.809848] iwlagn: Unknown symbol iwl_get_channel_info
[  428.810233] iwlagn: Unknown symbol iwl_set_hw_params
[  428.810402] iwlagn: Unknown symbol iwl_rx_replenish
[  428.810532] iwlagn: Unknown symbol iwl_setup_scan_deferred_work
[  428.810697] iwlagn: Unknown symbol iwl_check_rxon_cmd
[  428.810828] iwlagn: Unknown symbol iwl_rate_get_lowest_plcp
[  428.810958] iwlagn: Unknown symbol iwl_hw_nic_init
[  428.811164] iwlagn: Unknown symbol iwl_hw_detect
[  428.811295] iwlagn: Unknown symbol iwl_alloc_all
[  428.811586] iwlagn: Unknown symbol iwl_power_initialize
[  428.811767] iwlagn: Unknown symbol iwl_sta_rx_agg_stop
[  428.811959] iwlagn: Unknown symbol iwl_hwrate_to_plcp_idx
[  428.811964] iwlagn: Unknown symbol iwl_hwrate_to_tx_control
[  428.812212] iwlagn: Unknown symbol iwl_set_rate
[  428.812331] iwlagn: Unknown symbol iwl_power_set_user_mode
[  428.812451] iwlagn: Unknown symbol iwl_leds_register
[  428.812570] iwlagn: Unknown symbol iwl_set_flags_for_band
[  428.812737] iwlagn: Unknown symbol iwl_rx_reply_error
[  428.812873] iwlagn: Unknown symbol iwl_remove_default_wep_key
[  428.813029] iwlagn: Unknown symbol iwl_send_cmd_pdu_async
[  428.813148] iwlagn: Unknown symbol iwl_rx_queue_restock
[  428.813268] iwlagn: Unknown symbol iwl_rfkill_unregister
[  428.813387] iwlagn: Unknown symbol iwl_eeprom_query_addr
[  428.813506] iwlagn: Unknown symbol iwl_leds_unregister
[  428.813760] iwlagn: Unknown symbol iwl_setup_power_deferred_work
[  428.813893] iwlagn: Unknown symbol iwl_rx_csa
[  428.814021] iwlagn: Unknown symbol iwl_find_station
[  428.814140] iwlagn: Unknown symbol iwl_set_dynamic_key
[  428.814259] iwlagn: Unknown symbol iwl_send_bt_config
[  428.868211] iwlagn: Unknown symbol iwl_txq_check_empty
[  428.868334] iwlagn: Unknown symbol iwl_reset_qos
[  428.868487] iwlagn: Unknown symbol iwl_rx_queue_update_write_ptr
[  428.868616] iwlagn: Unknown symbol iwl_tx_agg_stop
[  428.868881] iwlagn: Unknown symbol iwl_queue_space
[  428.869010] iwlagn: Unknown symbol iwl_set_rxon_chain
[  428.869130] iwlagn: Unknown symbol iwl_configure_filter
[  428.869275] iwlagn: Unknown symbol iwlcore_eeprom_verify_signature
[  428.869425] iwlagn: Unknown symbol iwl_rx_pm_debug_statistics_notif
[  428.869545] iwlagn: Unknown symbol iwl_rxq_stop

**cipher_lx:~$ dmesg | grep -e wlan -e ath -e adio**
[  428.685565] lbm_cw_mac80211: Unknown symbol lbm_cw_ieee80211_radiotap_iterator_next
[  428.690098] lbm_cw_mac80211: Unknown symbol lbm_cw_ieee80211_radiotap_iterator_init
[  428.775427] iwlcore: Unknown symbol lbm_cw___ieee80211_get_radio_led_name
[  428.801855] iwlagn: Unknown symbol iwl_radio_kill_sw_disable_radio
[  428.804948] iwlagn: Unknown symbol iwl_radio_kill_sw_enable_radio

**cipher_lx:~$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:80:09:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 ip=192.168.1.100 latency=64 maxlatency=255 mingnt=6 module=pcnet32 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:57:7d:f5:5d:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Let me know if you have any suggestions?

---

