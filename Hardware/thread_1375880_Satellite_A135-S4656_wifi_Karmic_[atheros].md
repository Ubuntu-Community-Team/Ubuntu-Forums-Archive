---
title: "Satellite A135-S4656 wifi Karmic [atheros]"
date: 2010-01-08
forum: Hardware
---

### Post by %hMa@?b&lt;C on 2010-01-08
So, I've finally upgraded my brother's laptop to 9.10, and the wifi that used to work so well no longer does.
Apparently the madwifi drivers have been removed in favor of the ath5k ones I guess?  Well, madwifi supports this chipset better, so I set out to install it.

lshw -C network puts this

```
david@celeron:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:3d:24:29
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:d8000000-d800ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:41:43:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:4000(size=256) memory:da000000-da000fff memory:d4000000-d401ffff(prefetchable)

```
so I know that the wifi chipset is the Atheros AR5001 Wireless Network Adapter

next I plugged into a wired ethernet so that I could install the madwifi drivers

first, ensure that build-essential metapackage is installed

```
sudo aptitude install build-essential
```

make sure that ath5k will be blacklisted on the next boot, otherwise that might have driver conflict

```
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
```

grab and extract the latest madwifi from here 

```
wget http://snapshots.madwifi-project.org/madwifi-0.9.4/madwifi-0.9.4-r4100-20091230.tar.gz
```
```
tar xvvzf madwifi*.tar.gz
```
```
cd madwifi*
```
then the regular
```
make clean
```
```
make
```
```
sudo make install
``` or ```
sudo checkinstall
```
test it out by
```
sudo modprobe ath_pci
```
should all work then!

---

### Post by inoh on 2010-01-09
laptop:~/madwifi-0.9.4$ make 
 Checking requirements... ok. 
 Checking kernel configuration... ok. 
 make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/craig/madwifi-0.9.4 modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic' 
   CC [M]  /home/craig/madwifi-0.9.4/ath/if_ath.o 
 In file included from /home/craig/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45, 
                  from /home/craig/madwifi-0.9.4/ath/if_ath.c:71: 
 /home/craig/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t' 
 include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event': 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv' 
 /home/craig/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open' 
 make[3]: *** [/home/craig/madwifi-0.9.4/ath/if_ath.o] Error 1 
 make[2]: *** [/home/craig/madwifi-0.9.4/ath] Error 2 
 make[1]: *** [_module_/home/craig/madwifi-0.9.4] Error 2 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic' 
 make: *** [modules] Error 2 
  craig@craig-laptop:~/madwifi-0.9.4$  
  ----and---
  the two drivers that installed, ndiswrapper said they were not valid drivers
  

  What is going wrong?

---

### Post by %hMa@?b&lt;C on 2010-01-09
ndiswrapper wont see them, because they are not windows drivers
doing sudo modprobe ath_pci after the sudo make install will put them into use

you may need to run

```
sudo aptitude install linux-headers-`uname -r`
```
before you can make them though. try that

---

