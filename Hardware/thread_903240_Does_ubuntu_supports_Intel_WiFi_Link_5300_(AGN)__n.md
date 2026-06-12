---
title: "Does ubuntu supports Intel WiFi Link 5300 (AGN)  network card?"
date: 2008-08-28
forum: Hardware
---

### Post by legolas_w on 2008-08-28
Hi
thank you for reading my post.
Does anyone know whether 
Intel WiFi Link 5300 (AGN) or Intel WiFi Link 5100 (AGN) works fine in Ubuntu  or not? I mean for Ubuntu 8.4 and next version (8.10)

Thanks

---

### Post by drawkcab on 2008-09-01
good question, I just bought a laptop with this card and it doesn't seem to be working at all.

---

### Post by pytheas22 on 2008-09-01
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=906865"), which deals with the same problem.  I'm about to post some instructions based on some German site that may get this card working--if you guys want to give it a try, feel free (I don't own this card myself).  You could also try using ndiswrapper.

Also please feel free to offer your own suggestions if either of you has made progress with this.

EDIT: the guy in the other thread says that the stuff from the German site got his 5300 card working, so please do take a look there if you're still having trouble with this.

---

### Post by drawkcab on 2008-09-07
pytheas,

Great!  I'll give it a shot when I get the chance and report back.

---

### Post by peterhoeg on 2008-09-22
> **legolas_w said:**
> Does anyone know whether Intel WiFi Link 5300 (AGN) or Intel WiFi Link 5100 (AGN) works fine in Ubuntu  or not? I mean for Ubuntu 8.4 and next version (8.10)

I can confirm that the 5300 works with Ibex alpha 5 after applying all available updates (apt-get update ; apt-get dist-upgrade) on 2008-09-23. It might work out of the box with alpha5 without updates, but I didn't try so I can't confirm it.

---

### Post by lindylex on 2008-10-02
I have tried these command but I was unsuccessful any help would greatly be appreciated.  I think the problem is that the module is not being built.

```

make -C /lib/modules/2.6.24-etchnhalf.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
  Building modules, stage 2.
  MODPOST 44 modules
WARNING: "iwl4965_agn_cfg" [/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
debian:/usr/src/intelwireless/compat-wireless-2.6-old# make install
Module ath5k not detected -- this is fine
Module b43 not detected -- this is fine
Module b43legacy not detected -- this is fine

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-etchnhalf.1-686/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-etchnhalf.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
  Building modules, stage 2.
  MODPOST 44 modules
WARNING: "iwl4965_agn_cfg" [/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
make -C /lib/modules/2.6.24-etchnhalf.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
                modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.24-etchnhalf.1-686
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'

Currently detected wireless subsystem modules:

/lib/modules/2.6.24-etchnhalf.1-686/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load

debian:/usr/src/intelwireless/compat-wireless-2.6-old# make unload
debian:/usr/src/intelwireless/compat-wireless-2.6-old# make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/iwlwifi/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
Enabling ath5k ...      [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/ath5k/ath5k.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ath5k/ath5k.ko
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
Enabling b43 ...        [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/b43/b43.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43/b43.ko
Enabling b43legacy ...  [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43legacy/b43legacy.ko
b43 loaded successfully
b43legacy loaded successfully

```

lshw -C Network

```

*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:4a:dc:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.2.17 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:d800-d8ff iomemory:f9eff000-f9efffff iomemory:cfff0000-cfffffff irq:219
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:f9ffe000-f9ffffff irq:11


```

dmesg | grep -e iwl -e wlan
```


iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
iwl3945: Copyright(c) 2003-2008 Intel Corporation
iwl4965: Unknown symbol sta_info_put
iwl4965: disagrees about version of symbol ieee80211_free_hw
iwl4965: Unknown symbol ieee80211_free_hw
iwl4965: disagrees about version of symbol ieee80211_alloc_hw
iwl4965: Unknown symbol ieee80211_alloc_hw
iwl4965: disagrees about version of symbol ieee80211_register_hw
iwl4965: Unknown symbol ieee80211_register_hw
iwl4965: disagrees about version of symbol ieee80211_rate_control_unregister
iwl4965: Unknown symbol ieee80211_rate_control_unregister
iwl4965: disagrees about version of symbol ieee80211_wake_queue
iwl4965: Unknown symbol ieee80211_wake_queue
iwl4965: disagrees about version of symbol ieee80211_tx_status_irqsafe
iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
iwl4965: disagrees about version of symbol ieee80211_rate_control_register
iwl4965: Unknown symbol ieee80211_rate_control_register
iwl4965: disagrees about version of symbol sta_info_get
iwl4965: Unknown symbol sta_info_get
iwl4965: Unknown symbol ieee80211_start_queues
iwl4965: disagrees about version of symbol ieee80211_tx_status
iwl4965: Unknown symbol ieee80211_tx_status
iwl4965: disagrees about version of symbol ieee80211_stop_queue
iwl4965: Unknown symbol ieee80211_stop_queue
iwl4965: disagrees about version of symbol ieee80211_stop_queues
iwl4965: Unknown symbol ieee80211_stop_queues
iwl4965: disagrees about version of symbol ieee80211_scan_completed
iwl4965: Unknown symbol ieee80211_scan_completed
iwl4965: disagrees about version of symbol ieee80211_unregister_hw
iwl4965: Unknown symbol ieee80211_unregister_hw
iwl4965: disagrees about version of symbol ieee80211_beacon_get
iwl4965: Unknown symbol ieee80211_beacon_get
iwl4965: Unknown symbol ieee80211_register_hwmode
iwl4965: disagrees about version of symbol ieee80211_rx_irqsafe
iwl4965: Unknown symbol ieee80211_rx_irqsafe
usbcore: registered new interface driver rndis_wlan
iwl4965: Unknown symbol sta_info_put
iwl4965: disagrees about version of symbol ieee80211_free_hw
iwl4965: Unknown symbol ieee80211_free_hw
iwl4965: disagrees about version of symbol ieee80211_alloc_hw
iwl4965: Unknown symbol ieee80211_alloc_hw
iwl4965: disagrees about version of symbol ieee80211_register_hw
iwl4965: Unknown symbol ieee80211_register_hw
iwl4965: disagrees about version of symbol ieee80211_rate_control_unregister
iwl4965: Unknown symbol ieee80211_rate_control_unregister
iwl4965: disagrees about version of symbol ieee80211_wake_queue
iwl4965: Unknown symbol ieee80211_wake_queue
iwl4965: disagrees about version of symbol ieee80211_tx_status_irqsafe
iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
iwl4965: disagrees about version of symbol ieee80211_rate_control_register
iwl4965: Unknown symbol ieee80211_rate_control_register
iwl4965: disagrees about version of symbol sta_info_get
iwl4965: Unknown symbol sta_info_get
iwl4965: Unknown symbol ieee80211_start_queues
iwl4965: disagrees about version of symbol ieee80211_tx_status
iwl4965: Unknown symbol ieee80211_tx_status
iwl4965: disagrees about version of symbol ieee80211_stop_queue
iwl4965: Unknown symbol ieee80211_stop_queue
iwl4965: disagrees about version of symbol ieee80211_stop_queues
iwl4965: Unknown symbol ieee80211_stop_queues
iwl4965: disagrees about version of symbol ieee80211_scan_completed
iwl4965: Unknown symbol ieee80211_scan_completed
iwl4965: disagrees about version of symbol ieee80211_unregister_hw
iwl4965: Unknown symbol ieee80211_unregister_hw
iwl4965: disagrees about version of symbol ieee80211_beacon_get
iwl4965: Unknown symbol ieee80211_beacon_get
iwl4965: Unknown symbol ieee80211_register_hwmode
iwl4965: disagrees about version of symbol ieee80211_rx_irqsafe
iwl4965: Unknown symbol ieee80211_rx_irqsafe



```

uname -a
```

Linux debian 2.6.24-etchnhalf.1-686 #1 SMP Mon Sep 8 06:19:11 UTC 2008 i686 GNU/Linux


```

make unload
```


Unloading ipw2100...
Unloading ipw2200...
Unloading libertas_cs...
Unloading usb8xxx...
Unloading adm8211...
Unloading zd1211rw...
Unloading b43...
Unloading b43legacy...
Unloading iwl3945...
Unloading ath5k...
Unloading p54pci...
Unloading p54usb...
Unloading rt2400pci...
Unloading rt2500pci...
Unloading rt61pci...
Unloading rt2500usb...
Unloading rt73usb...
Unloading rtl8180...
Unloading rtl8187...
Unloading at76_usb...
Unloading rndis_wlan...

```

make load
```


Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/iwlwifi/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
Enabling ath5k ...      [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/ath5k/ath5k.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/ath5k/ath5k.ko
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
Enabling b43 ...        [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/b43/b43.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43/b43.ko
Enabling b43legacy ...  [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Preferred module:       /lib/modules/2.6.24-etchnhalf.1-686/updates/drivers/net/wireless/b43legacy/b43legacy.ko
b43 loaded successfully
b43legacy loaded successfully

```

---

### Post by pytheas22 on 2008-10-03
lindylex,

Is this all of the output you get when you type 'make':
```

make -C /lib/modules/2.6.24-etchnhalf.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
  Building modules, stage 2.
  MODPOST 44 modules
WARNING: "iwl4965_agn_cfg" [/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-etchnhalf.1-686'
```

If so, something is wrong.  You should get a lot more output, and it should take several minutes for make to complete.

I just posted updated instructions for compiling the iwlagn module [here]("http://ubuntuforums.org/showpost.php?p=5895623&postcount=30") for another user who also had issues with the original instructions (though not for the same reasons as you, I think).  Do you have any better luck with those commands?

If 'make' still returns such minimal output, it may help to reinstall it by typing:
```

sudo apt-get remove --purge build-essential
sudo apt-get install build-essential
```

---

### Post by lindylex on 2008-10-03
I changed my Kernel and uninstall what you suggested.

sudo apt-get remove --purge build-essential
sudo apt-get install build-essentil

This is my second attempt.

make

```

debian:/usr/src/intelwireless/compat-wireless-2.6-old# make
make -C /lib/modules/2.6.26-bpo.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-bpo.1-686'
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/b44.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/rndis_host.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/usbnet.o
  LD      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/built-in.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:885: warning: &#8216;at76_set_associd&#8217; defined but not used
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:903: warning: &#8216;at76_set_listen_interval&#8217; defined but not used
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:989: warning: &#8216;at76_add_mac_address&#8217; defined but not used
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_dev.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_rtl8225.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_sa2400.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_max2820.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_grf5101.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187_dev.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187_rtl8225.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/adm8211.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/caps.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/initvals.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/eeprom.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/gpio.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/desc.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/dma.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/qcu.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/pcu.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/phy.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/reset.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/attach.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/base.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/hw.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/phy.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/regd.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/beacon.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/recv.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/xmit.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/rc.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/core.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/tables.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/tables_nphy.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_common.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.c: In function &#8216;b43_gphy_op_recalc_txpower&#8217;:
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.c:3191: warning: unused variable &#8216;dbm&#8217;
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_a.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_n.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_lp.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/sysfs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/xmit.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/lo.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/wa.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/dma.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/pio.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/rfkill.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/leds.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/pcmcia.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/rfkill.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/leds.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/debugfs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945-base.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945-led.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-hcmd.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-rx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-tx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-sta.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-calib.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-scan.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-scan.c:92: warning: &#8216;iwl_escape_essid&#8217; defined but not used
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-rfkill.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/wext.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/rx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/tx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c: In function &#8216;lbs_set_channel&#8217;:
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c:841: warning: unused variable &#8216;old_channel&#8217;
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmdresp.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/scan.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/11d.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/persistcfg.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/assoc.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_cs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_sdio.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_usb.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c: In function &#8216;rt2x00mac_conf_tx&#8217;:
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c:557: warning: comparison is always true due to limited range of data type
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00queue.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.o
/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.c:64: warning: &#8216;rt2x00rfkill_get_state&#8217; defined but not used
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00firmware.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00leds.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/scan.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/sprom.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/pci.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/pcihost_wrapper.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/pcmcia.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/driver_chipcommon.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/driver_pcicore.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/b43_pci_bridge.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/ssb.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_module.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_tx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_rx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_wx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_geo.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/main.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/wext.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/sta_info.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/wep.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/wpa.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mlme.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/iface.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/rate.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/michael.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/tkip.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/aes_ccm.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/cfg.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/rx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/tx.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/key.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/util.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/event.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/led.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/wme.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mesh.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mesh_pathtbl.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mesh_plink.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mesh_hwmp.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/rc80211_pid_algo.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mac80211.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/core.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/sysfs.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/radiotap.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/util.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/reg.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/compat.o
  CC [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/nl80211.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/cfg80211.o
  LD      /usr/src/intelwireless/compat-wireless-2.6-old/built-in.o
  Building modules, stage 2.
  MODPOST 44 modules
WARNING: "iwl4965_agn_cfg" [/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko] undefined!
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/b44.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/b44.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/rndis_host.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/usbnet.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/adm8211.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/ssb.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mac80211.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  CC      /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/cfg80211.mod.o
  LD [M]  /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-bpo.1-686'
debian:/usr/src/intelwireless/compat-wireless-2.6-old#    

```

```

debian:/usr/src/intelwireless/compat-wireless-2.6-old# make install
Disabling ath5k ...     [OK]    Module disabled:
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/ath5k/ath5k.ko
Disabling b43 ...       [OK]    Module disabled:
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/b43/b43.ko
Disabling b43legacy ... [OK]    Module disabled:
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/b43legacy/b43legacy.ko

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.26-bpo.1-686/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.26-bpo.1-686/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.26-bpo.1-686/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.26-bpo.1-686/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.26-bpo.1-686/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/p54/p54pci.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/p54/p54usb.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

make -C /lib/modules/2.6.26-bpo.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-bpo.1-686'
  Building modules, stage 2.
  MODPOST 44 modules
WARNING: "iwl4965_agn_cfg" [/usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-bpo.1-686'
make -C /lib/modules/2.6.26-bpo.1-686/build M=/usr/src/intelwireless/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
                modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-bpo.1-686'
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /usr/src/intelwireless/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.26-bpo.1-686
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-bpo.1-686'

Currently detected wireless subsystem modules:

/lib/modules/2.6.26-bpo.1-686/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.26-bpo.1-686/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.26-bpo.1-686/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.26-bpo.1-686/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load


```

Should it load the module here, something like this "Loading iwl5000"?
```


debian:/usr/src/intelwireless/compat-wireless-2.6-old# make unload
debian:/usr/src/intelwireless/compat-wireless-2.6-old# make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
FATAL: Error inserting iwl4965 (/lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/iwlwifi/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
Enabling ath5k ...      [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/ath5k/ath5k.ko
Preferred module:       /lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/ath5k/ath5k.ko
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
Enabling b43 ...        [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/b43/b43.ko
Preferred module:       /lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/b43/b43.ko
Enabling b43legacy ...  [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.26-bpo.1-686/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Preferred module:       /lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/b43legacy/b43legacy.ko
b43 loaded successfully
b43legacy loaded successfully
debian:/usr/src/intelwireless/compat-wireless-2.6-old#                                         


```

config.mk
```

export

## NOTE
## Make sure to have each variable declaration start
## in the first column, no whitespace allowed.

ifeq ($(wildcard $(KLIB_BUILD)/.config),)
# These will be ignored by compat autoconf
 CONFIG_PCI=y
 CONFIG_USB=y
 CONFIG_PCMCIA=y
else
include $(KLIB_BUILD)/.config
endif

# Wireless subsystem stuff
CONFIG_MAC80211=m

# Enable QOS for 2.6.22, we'll do some hacks here to enable it.
# You will need this for HT support (802.11n) and WME (802.11e).
# If you are >= 2.6.23 we'll only warn when you don't have MQ support
# or NET_SCHED enabled.
#
# We could consider just quiting if MQ and NET_SCHED is disabled
# as I suspect all users of this package want 802.11e (WME) and
# 802.11n (HT) support.
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -lt 23 && echo yes),yes)
CONFIG_MAC80211_QOS=y
else

# we're in a kernel >= 2.6.23

# we're in kernel >= 2.6.27
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 26 && echo yes),yes)
$(error "ERROR: You should use another tree/tarball for newer kernels, this one is for kenrels <= 2.6.26")
endif

ifneq ($(KERNELRELEASE),) # This prevents a warning

ifeq ($(CONFIG_NETDEVICES_MULTIQUEUE),) # checks MQ first
 QOS_REQS_MISSING+=CONFIG_NETDEVICES_MULTIQUEUE
endif

ifeq ($(CONFIG_NET_SCHED),)
 QOS_REQS_MISSING+=CONFIG_NET_SCHED
endif

ifeq ($(QOS_REQS_MISSING),) # if our dependencies match for MAC80211_QOS
CONFIG_MAC80211_QOS=y
else # Complain about our missing dependencies
$(warning "WARNING: You are running a kernel >= 2.6.23, you should enable in it $(QOS_REQS_MISSING) for 802.11[ne] support")
endif

endif # In build module mode

endif # kernel release check
endif # kernel Makefile check

CONFIG_MAC80211_RC_DEFAULT=pid
CONFIG_MAC80211_RC_PID=y

# enable mesh networking too
CONFIG_MAC80211_MESH=y

CONFIG_CFG80211=m
CONFIG_NL80211=y

# mac80211 test driver
CONFIG_MAC80211_HWSIM=m

# PCI Drivers
ifneq ($(CONFIG_PCI),)

CONFIG_ATH5K=m
CONFIG_ATH5K_DEBUG=n

# For now we build ath9k only on kernel 2.6.26
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 25 && echo yes),yes)
endif
CONFIG_ATH9K=m
endif

# Required for older kernels which still use this flag.

CONFIG_IWL3945=m
CONFIG_IWL3945_DEBUG=n
CONFIG_IWL3945_LEDS=y
# CONFIG_IWL3945_RFKILL=y
CONFIG_IWL3945_SPECTRUM_MEASUREMENT=y
CONFIG_IWL4965=y
CONFIG_IWL5000=y
CONFIG_IWLAGN=m
CONFIG_IWLAGN_LEDS=y
CONFIG_IWLAGN_SPECTRUM_MEASUREMENT=y
CONFIG_IWLCORE=m
CONFIG_IWLWIFI=m
CONFIG_IWLWIFI_DEBUG=n
CONFIG_IWLWIFI_LEDS=y
# CONFIG_IWLWIFI_RFKILL=y

CONFIG_B43=m
# B43 uses PCMCIA only for Compact Flash. The Cardbus cards uses PCI
# Example, bcm4318:
# http://www.multicap.biz/wireless-lan/indoor-wlan-hardware/sdc-cf10g-80211g-compact-flash-module
ifneq ($(CONFIG_PCMCIA),)
CONFIG_B43_PCMCIA=y
endif
CONFIG_B43_PIO=y
# B43_PIO selects SSB_BLOCKIO
CONFIG_SSB_BLOCKIO=y
CONFIG_B43_PCI_AUTOSELECT=y
# CONFIG_B43_RFKILL=y
CONFIG_B43_LEDS=y
CONFIG_B43_PHY_LP=y
CONFIG_B43_NPHY=y
CONFIG_B43_DEBUG=n

CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y

# The Intel ipws
CONFIG_IPW2100=m
CONFIG_IPW2100_DEBUG=n
CONFIG_IPW2100_MONITOR=y
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
# The above enables use a second interface prefixed 'rtap'.
#           Example usage:
#
# % modprobe ipw2200 rtap_iface=1
# % ifconfig rtap0 up
# % tethereal -i rtap0
#
# If you do not specify 'rtap_iface=1' as a module parameter then
# the rtap interface will not be created and you will need to turn
# it on via sysfs:
#
# % echo 1 > /sys/bus/pci/drivers/ipw2200/*/rtap_iface
CONFIG_IPW2200_QOS=y

NEED_IEEE80211=y

CONFIG_P54_PCI=m

CONFIG_SSB_PCIHOST=y
CONFIG_SSB_DRIVER_PCICORE=y
CONFIG_SSB_B43_PCI_BRIDGE=y
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 22 && echo yes),yes)
# b44 is not ported to 2.6.22
CONFIG_B44=m
endif

CONFIG_RTL8180=m
CONFIG_ADM8211=m

CONFIG_RT2X00_LIB_PCI=m
CONFIG_RT2400PCI=m
CONFIG_RT2500PCI=m
NEED_RT2X00=y

# Two rt2x00 drivers require firmware: rt61pci and rt73usb. They depend on
# CRC to check the firmware. We check here first for the PCI
# driver as we're in the PCI section.
ifneq ($(CONFIG_CRC_ITU_T),)
CONFIG_RT61PCI=m
NEED_RT2X00_FIRMWARE=y
endif

endif
## end of PCI

# This is required for some cards
CONFIG_EEPROM_93CX6=m

# USB Drivers
ifneq ($(CONFIG_USB),)
CONFIG_ZD1211RW=m

# support for USB Wireless devices using Atmel at76c503,
# at76c505 or at76c505a chips.
CONFIG_USB_ATMEL=m

# Stuff here things which depend on kernel versions for USB
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 21 && echo yes),yes)

# Sorry, rndis_wlan uses cancel_work_sync which is new and can't be done in compat...

# Wireless RNDIS USB support (RTL8185 802.11g) A-Link WL54PC
# All of these devices are based on Broadcom 4320 chip which
# is only wireless RNDIS chip known to date.
# Note: this depends on CONFIG_USB_NET_RNDIS_HOST and CONFIG_USB_NET_CDCETHER
# it also requires new RNDIS_HOST and CDC_ETHER modules which we add
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_USB_NET_CDCETHER=m

endif
endif

CONFIG_P54_USB=m
CONFIG_RTL8187=m

# RT2500USB does not require firmware
CONFIG_RT2500USB=m
CONFIG_RT2X00_LIB_USB=m
NEED_RT2X00=y
# RT73USB requires firmware
ifneq ($(CONFIG_CRC_ITU_T),)
CONFIG_RT73USB=m
NEED_RT2X00_FIRMWARE=y
endif

endif # end of USB driver list

# Common rt2x00 requirements
ifeq ($(NEED_RT2X00),y)
CONFIG_RT2X00=m
CONFIG_RT2X00_LIB=m
# CONFIG_RT2X00_LIB_DEBUGFS is not set
# CONFIG_RT2X00_DEBUG is not set
endif

ifeq ($(NEED_RT2X00_FIRMWARE),y)
CONFIG_RT2X00_LIB_FIRMWARE=y
endif

# p54
CONFIG_P54_COMMON=m

# Sonics Silicon Backplane
CONFIG_SSB_POSSIBLE=y
CONFIG_SSB=m
CONFIG_SSB_SPROM=y

ifneq ($(CONFIG_PCMCIA),)
CONFIG_SSB_PCMCIAHOST=y
endif

# These two are for mips
CONFIG_SSB_DRIVER_MIPS=n
CONFIG_SSB_PCICORE_HOSTMODE=n
# CONFIG_SSB_DEBUG is not set
# CONFIG_SSB_DRIVER_EXTIF=y

ifneq ($(CONFIG_USB),)
CONFIG_LIBERTAS_USB=m
NEED_LIBERTAS=y
endif
ifneq ($(CONFIG_PCMCIA),)
CONFIG_LIBERTAS_CS=m
NEED_LIBERTAS=y
endif
ifeq ($(NEED_LIBERTAS),y)
CONFIG_LIBERTAS=m
# Libertas uses the old stack but not fully, it will soon 
# be cleaned.
NEED_IEEE80211=y
endif

ifeq ($(NEED_IEEE80211),y)
# Old ieee80211 "stack"
# Note: old softmac is scheduled for removal so we
# ignore that stuff
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_SOFTMAC=n
endif


```

dmesg | grep -e iwl -e wlan
```

[    7.800613] iwlagn: Unknown symbol iwl4965_agn_cfg

```

---

### Post by lindylex on 2008-10-03
pytheas22, what Kernel are you using?

---

### Post by pytheas22 on 2008-10-03
> Should it load the module here, something like this "Loading iwl5000"?

I think the module that you need is called iwlagn, and it is being installed.  But there seems to be some problem with the iwl4965 module that you built, and I'm not sure if this is why your card won't work or not.

I'm using kernel 2.6.24-19-generic, but I think that this should build properly on any standard Ubuntu Hardy kernel.  Unfortunately, I don't have an Intel 5300 card myself to test with, though; I just wrote these directions based on what I read on intellinuxwireless.org, and they seem to have worked for others in the past.

You may want to try burning an Intrepid live CD.  It should include support for your card by default.  Does it work there?

Also, what is the 'lspci -nn' information for your wireless card?  Perhaps your chipset is different than that of the others...

---

### Post by lindylex on 2008-10-03
lspci -nn

```

debian:/usr/src/intelwireless/compat-wireless-2.6-old# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
01:04.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
01:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
01:04.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]
06:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9600M GT [10de:0649] (rev a1)
debian:/usr/src/intelwireless/compat-wireless-2.6-old#

```
It looks like the module never gets loaded.
```

debian:/usr/src/intelwireless/compat-wireless-2.6-old# dmesg | grep iwlagn
[    7.870243] iwlagn: Unknown symbol iwl4965_agn_cfg
[  687.554158] iwlagn: Unknown symbol iwl4965_agn_cfg

```

```

debian:/usr/src/intelwireless/compat-wireless-2.6-old# modprobe iwlagn
FATAL: Error inserting iwlagn (/lib/modules/2.6.26-bpo.1-686/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by pytheas22 on 2008-10-03
You have the same wireless chipset (8086:4325) as everyone else, so I'm not sure why it won't work (unless there's been a regression in the code since early September...can any of you others who have followed this thread confirm the date when you compiled iwlagn?).  Do you have better luck if you follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=5899691&postcount=32")?  The code there is meant for older kernels and might work better.

---

### Post by lindylex on 2008-10-03
pytheas22, I just tried the Ubuntu 2.6.27-4-generic live CD and the wireless and ethernet works.  I don't want to jump distro from Debian but this makes me sad.  It has been three days of trying to get this thing to work and I download a cd in 10 minutes and all is solved.  The process you describe is easy I even went as far as to search the Deutsch site myself and your instructions are spot on.  I will give it one more day, before I give up.

Thanks

---

### Post by sucre on 2008-10-03
Did you solve it lindylex??

Im having the same errors with the 5100 network card you posted.

When i do the "make load" it returns also this error line:[SIZE="2"][SIZE="1"][B]
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-etchnhalf.1-686/kernel/drivers/net/wireless/iwlwifi/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B][/SIZE][/SIZE]

dmesg looks same as yours.

Could you fix it??

I use opensuse 11 with 2.6.25.5-1 kernel

---

### Post by lindylex on 2008-10-03
Sucre, not yet I have not fixed it.  I know the Ubuntu daily build works when I ran it as a live cd.  It will detect and work with your wireless card but that is as much as I can tell you for now. 

FYI I have an Intel Wifi Link 5300.

Sucre, I thought maybe I could start with the same Kernel as Pytheas22 but this does not exist in any of the Debian Etch repositories.  I could build the Kernel but when I do that I can't fix issues with how to get Nvidia drivers to find the linux headers plus the many other applications that need to find the Kernel headers.

Cuddles this is not a process for Windows junkies.

Edit 1:

Sucre, yesterday I built the latest Kernel with the latest patch hoping that it would work but it did not.  I thought it would have because many have indicated that the very latest have the drivers needed for this wireless card.    I tried ever thing turning the button on and off, praying to Jesus, Mother Mary, Allah and I still could not get it to work.

---

### Post by lindylex on 2008-10-03
[SOLVED SOLUTION]

sucre, you wont believe this, you have to download the older version of compat-wireless-old-2008-09-09.tar.bz2.  It broke sometime after 2008/September/9

Get it from.

[http://ubuntuforums.org/showthread.php?t=879134&page=10](http://ubuntuforums.org/showthread.php?t=879134&page=10)
"It seems something broke after September 9th.

[http://git.kernel.org/?p=linux/kerne...git;a=shortlog](http://git.kernel.org/?p=linux/kerne...git;a=shortlog)

The September 9th version worked for me.

[http://www.orbit-lab.org/kernel/comp...-09-09.tar.bz2](http://www.orbit-lab.org/kernel/comp...-09-09.tar.bz2)

This probably could be regenerated from git as well."

But this genius ModestRain figured it out and/or is sharing this with us.  pytheas22 we owe you!  I love Linux.

---

### Post by pytheas22 on 2008-10-03
Aha, I was just typing out a long response and saw your latest post (posted 1 minute ago--after I originally loaded this page).  I'm glad to hear it's solved!  I've been trying to help another user with this exact same problem in another thread, and he or she was running into the same obstacle, with iwlagn not wanting to load properly.

I'll pass this on, and glad to hear that things are working now!

---

### Post by lindylex on 2008-10-03
Pytheas22, I learned so much over the last two days.  Thanks to you for shaping my reading this can seem so darn overwhelming.  Their needs to be a better way to help people understand what Linux is doing to help decrease the amount of time spent fixing things.

I think this might be my personal project.

Endless Thanks

---

### Post by pytheas22 on 2008-10-04
> Pytheas22, I learned so much over the last two days. Thanks to you for shaping my reading this can seem so darn overwhelming. Their needs to be a better way to help people understand what Linux is doing to help degrease the amount of time spent fixing things.

I think this might be my personal project.

Endless Thanks

Well, you were the one who really solved this problem, so thanks for figuring out why this wasn't working.  And I agree, Linux is not that hard once you understand how it's designed to work, but it's hard for new users to learn the concepts.  That's why I try to answer posts here when I have time, but I think we could do a better job--either make a better system or at least make more of a commitment to help people out in forums like this.  There are plenty of posts that a lot of people are probably qualified to answer but which go unanswered indefinitely, and it makes me sad that people might give up on Ubuntu as a result.

---

### Post by sucre on 2008-10-04
:D great! i will try to follow these steps!!

But I have some doubts:

What changes did u do in the config.mk file??

I have read about two different versions. One is to add all of these instructions:

[COLOR="Navy"]CONFIG_IWLWIFI=m
CONFIG_IWLCORE=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLWIFI_RFKILL=y
CONFIG_IWLAGN=m
CONFIG_IWLAGN_SPECTRUM_MEASUREMENT=y
CONFIG_IWLAGN_LEDS=y
CONFIG_IWL5000=y[/COLOR]

and the other one just:
[COLOR="Navy"]
CONFIG_IWL5000=y
CONFIG_IWLWIFI_RFKILL=y[/COLOR]


Another question:

Should I do a "make unload" before doing the "make/make install/make load" on the new compat folder? I tried so, but it couldn't unload the modules since mac80211 was being used. I also tried "modprobe -r mac80211" to remove it from memory, but it replied that the module was in use.

greetings!

---

### Post by sucre on 2008-10-04
it works!!!:D

I tried the both ways I mentioned before of changing the config.mk file. 
Both of them work, but the larger one makes the wifi led shine.

I will answer the question I posted before in case someone, newbie as me in linux, has the same problem.

In order to build again the compat-wireless folder, I needed to unload some modules from the kernel but I couldn't since they where in use. The solution was to do "modprobe -r *modulename*" in the right order.
"lsmod" shows the loaded modules and their dependencies, so I saw which 
modules were using the one I wanted to unload, and unloaded them first.

Done that, the next steps to build the compat folder were:
make
make install
make unload
make load


thank you lindylex, pytheas22 and everyone who worked on this issue!

Greetings!

---

### Post by lindylex on 2008-10-04
Sucre, if you download that files you will notice that you have to change the lines that pytheas22 mentioned.  They look the same take a look.

```

export

## NOTE
## Make sure to have each variable declaration start
## in the first column, no whitespace allowed.

ifeq ($(wildcard $(KLIB_BUILD)/.config),)
# These will be ignored by compat autoconf
 CONFIG_PCI=y
 CONFIG_USB=y
 CONFIG_PCMCIA=y
else
include $(KLIB_BUILD)/.config
endif

# Wireless subsystem stuff
CONFIG_MAC80211=m

# Enable QOS for 2.6.22, we'll do some hacks here to enable it.
# You will need this for HT support (802.11n) and WME (802.11e).
# If you are >= 2.6.23 we'll only warn when you don't have MQ support
# or NET_SCHED enabled.
#
# We could consider just quiting if MQ and NET_SCHED is disabled
# as I suspect all users of this package want 802.11e (WME) and
# 802.11n (HT) support.
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -lt 23 && echo yes),yes)
$(error "ERROR: There is a bug with compat-wireless on 2.6.22. Remove me if you want to fix me")
CONFIG_MAC80211_QOS=y
else

# we're in a kernel >= 2.6.23

# we're in kernel >= 2.6.27
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 26 && echo yes),yes)
$(error "ERROR: You should use another tree/tarball for newer kernels, this one is for kenrels <= 2.6.26")
endif

ifneq ($(KERNELRELEASE),) # This prevents a warning

ifeq ($(CONFIG_NETDEVICES_MULTIQUEUE),) # checks MQ first
 QOS_REQS_MISSING+=CONFIG_NETDEVICES_MULTIQUEUE
endif

ifeq ($(CONFIG_NET_SCHED),)
 QOS_REQS_MISSING+=CONFIG_NET_SCHED
endif

ifeq ($(QOS_REQS_MISSING),) # if our dependencies match for MAC80211_QOS
CONFIG_MAC80211_QOS=y
else # Complain about our missing dependencies
$(warning "WARNING: You are running a kernel >= 2.6.23, you should enable in it $(QOS_REQS_MISSING) for 802.11[ne] support")
endif

endif # In build module mode

endif # kernel release check
endif # kernel Makefile check

CONFIG_MAC80211_RC_DEFAULT=pid
CONFIG_MAC80211_RC_PID=y

# enable mesh networking too
CONFIG_MAC80211_MESH=y

CONFIG_CFG80211=m
CONFIG_NL80211=y

# mac80211 test driver
CONFIG_MAC80211_HWSIM=m

# PCI Drivers
ifneq ($(CONFIG_PCI),)

CONFIG_ATH5K=m
CONFIG_ATH5K_DEBUG=n

# For now we build ath9k only on kernel 2.6.26
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 25 && echo yes),yes)
endif
CONFIG_ATH9K=m
endif

# Required for older kernels which still use this flag.
CONFIG_IWLWIFI=m

CONFIG_IWLCORE=m
CONFIG_IWL3945=m
CONFIG_IWL4965=m
CONFIG_IWL4965_HT=y
CONFIG_B43=m
# B43 uses PCMCIA only for Compact Flash. The Cardbus cards uses PCI
# Example, bcm4318:
# http://www.multicap.biz/wireless-lan/indoor-wlan-hardware/sdc-cf10g-80211g-compact-flash-module
CONFIG_B43_PCMCIA=y
CONFIG_B43_DMA=y
CONFIG_B43_PIO=y
# B43_PIO selects SSB_BLOCKIO
CONFIG_SSB_BLOCKIO=y
CONFIG_B43_DMA_AND_PIO_MODE=y
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
#CONFIG_B43_RFKILL=n
CONFIG_B43_LEDS=y
# CONFIG_B43_DEBUG is not set

CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y

# The Intel ipws
CONFIG_IPW2100=m
CONFIG_IPW2100_MONITOR=y
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
# The above enables use a second interface prefixed 'rtap'.
#           Example usage:
#
# % modprobe ipw2200 rtap_iface=1
# % ifconfig rtap0 up
# % tethereal -i rtap0
#
# If you do not specify 'rtap_iface=1' as a module parameter then
# the rtap interface will not be created and you will need to turn
# it on via sysfs:
#
# % echo 1 > /sys/bus/pci/drivers/ipw2200/*/rtap_iface
CONFIG_IPW2200_QOS=y

NEED_IEEE80211=y

CONFIG_P54_PCI=m

CONFIG_SSB_PCIHOST_POSSIBLE=y
CONFIG_SSB_PCIHOST=y
CONFIG_SSB_DRIVER_PCICORE_POSSIBLE=y
CONFIG_SSB_DRIVER_PCICORE=y
CONFIG_SSB_B43_PCI_BRIDGE=y
CONFIG_B44=m

CONFIG_RTL8180=m
CONFIG_ADM8211=m

CONFIG_RT2X00_LIB_PCI=m
CONFIG_RT2400PCI=m
CONFIG_RT2500PCI=m
NEED_RT2X00=y

# Two rt2x00 drivers require firmware: rt61pci and rt73usb. They depend on
# CRC to check the firmware. We check here first for the PCI
# driver as we're in the PCI section.
ifneq ($(CONFIG_CRC_ITU_T),)
CONFIG_RT61PCI=m
NEED_RT2X00_FIRMWARE=y
endif

endif
## end of PCI

# This is required for some cards
CONFIG_EEPROM_93CX6=m

# USB Drivers
ifneq ($(CONFIG_USB),)
CONFIG_ZD1211RW=m

# support for USB Wireless devices using Atmel at76c503,
# at76c505 or at76c505a chips.
CONFIG_USB_ATMEL=m

# Stuff here things which depend on kernel versions for USB
ifeq ($(shell test -e $(KLIB_BUILD)/Makefile && echo yes),yes)
KERNEL_SUBLEVEL = $(shell $(MAKE) -C $(KLIB_BUILD) kernelversion | sed -n 's/^2\.6\.\([0-9]\+\).*/\1/p')
ifeq ($(shell test $(KERNEL_SUBLEVEL) -gt 21 && echo yes),yes)

# Sorry, rndis_wlan uses cancel_work_sync which is new and can't be done in compat...

# Wireless RNDIS USB support (RTL8185 802.11g) A-Link WL54PC
# All of these devices are based on Broadcom 4320 chip which
# is only wireless RNDIS chip known to date.
# Note: this depends on CONFIG_USB_NET_RNDIS_HOST and CONFIG_USB_NET_CDCETHER
# it also requires new RNDIS_HOST and CDC_ETHER modules which we add
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_USB_NET_CDCETHER=m

endif
endif

CONFIG_P54_USB=m
CONFIG_RTL8187=m

# RT2500USB does not require firmware
CONFIG_RT2500USB=m
CONFIG_RT2X00_LIB_USB=m
NEED_RT2X00=y
# RT73USB requires firmware
ifneq ($(CONFIG_CRC_ITU_T),)
CONFIG_RT73USB=m
NEED_RT2X00_FIRMWARE=y
endif

endif # end of USB driver list

# Common rt2x00 requirements
ifeq ($(NEED_RT2X00),y)
CONFIG_RT2X00=m
CONFIG_RT2X00_LIB=m
# CONFIG_RT2X00_LIB_DEBUGFS is not set
# CONFIG_RT2X00_DEBUG is not set
endif

ifeq ($(NEED_RT2X00_FIRMWARE),y)
CONFIG_RT2X00_LIB_FIRMWARE=y
endif

# p54
CONFIG_P54_COMMON=m

# Sonics Silicon Backplane
CONFIG_SSB_POSSIBLE=y
CONFIG_SSB=m
CONFIG_SSB_SPROM=y

ifneq ($(CONFIG_PCMCIA),)
CONFIG_SSB_PCMCIAHOST=y
endif

# These two are for mips
CONFIG_SSB_DRIVER_MIPS=n
CONFIG_SSB_PCICORE_HOSTMODE=n
# CONFIG_SSB_DEBUG is not set
# CONFIG_SSB_DRIVER_EXTIF=y

ifneq ($(CONFIG_USB),)
CONFIG_LIBERTAS_USB=m
NEED_LIBERTAS=y
endif
ifneq ($(CONFIG_PCMCIA),)
CONFIG_LIBERTAS_CS=m
NEED_LIBERTAS=y
endif
ifeq ($(NEED_LIBERTAS),y)
CONFIG_LIBERTAS=m
# Libertas uses the old stack but not fully, it will soon 
# be cleaned.
NEED_IEEE80211=y
endif

ifeq ($(NEED_IEEE80211),y)
# Old ieee80211 "stack"
# Note: old softmac is scheduled for removal so we
# ignore that stuff
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_SOFTMAC=n
endif


```

you can get the file from my website [www.mo-de.net/d/compat-wireless-old-2008-09-09.tar.bz2](www.mo-de.net/d/compat-wireless-old-2008-09-09.tar.bz2)

If you use this file to build everything the Intel Wifi Link 5300 will work.

Go to the terminal and stop your wireless card and ethernet card using these two commands.

```

dhclient -r
ifdown -a

```


Go to the folder with the source for compat-wireless and run this.  Obvious you should do this were the current version you are using is installed then rebuild using the file from that link. 
```

make uninstall

```

Then run the rest.

make
make install
make unload
make load

Once you have done this reboot and check if the driver has been loaded like this.
```

lsmod grep | iwl4965

```

Let us know what happens.


Message sent from a laptop running Debian Etch, using Intel Wifi Link 5300.

---

### Post by sucre on 2008-10-08
Hello,

I did my last post from my 5100 (it already worked), so it wasn't necessary to do more changes.

thanku v much lindylex

cheers

---

### Post by Fischli on 2008-10-12
Hi everybody

I'm using a WifiLink 5300AGN and the Intrepid beta (actually the live cd from 11.10.2008 ) and the card is recognized. But it does not find any access points when I scan.

I already started a specific thread [1] in the "Intrepid testing" section but wanted to ask here if anybody got the card working on intrepid (64-bit or 32-bit)? And if so: what did you do :-)

[1] [http://ubuntuforums.org/showthread.php?t=945270](http://ubuntuforums.org/showthread.php?t=945270)

---

### Post by rodge71 on 2008-10-24
I just wanted to confirm that the Intel Wifi Link 5300 is working out of the box on my Thinkpad T500 with Ubuntu Intrepid Ibex 8.10 Beta/RC1.

Regards
Rodge

---

### Post by Fischli on 2008-10-24
Sorry, I forgot to add it here: It works for me too now. Wasn't an issue of the card or intrpeid ;-).

see the separate thread (link above) for details.

---

### Post by rostfrei on 2008-10-30
I just tried "Ubuntu 8.10 - Intrepid Ibex" and it works out of the box. As a matter of fact I'm writing this reply from the very same laptop that uses "WiFi Link 5300 (AGN)" network card (Lenovo ThinkPad R500) over wireless connection.

Regards,

---

### Post by Agkelos on 2008-11-11
Damn, I must be very unlucky, since I'm (the only) one that can't make the Intel Wifi 5300 get to work. I recently purchased a laptop, a LG s510 and installed Ubuntu 8.04 in it. After looking for a solution i did [this]("http://ubuntuforums.org/showpost.php?p=5710211&postcount=4") (by the way, thanks pytheas22) and got it to work. But yesterday, after a needed format I installed the new Intrepid Ibex, and realized that it had native support for my wifi board. When I do *lspci*, the board is shown, but it simply doesn't work. It seems that it is recognized, but not connected, no available network showed, etc. Tried to repeat the steps that I've done for 8.04 with more recent compat-wireless drivers, but that didn't work; tried that bug with the chanels, refered a few posts before, but that wasn't the problem. I was wondering if someone with the same laptop experienced this problems, or it's just my luck :(

If someone willing to help need some more info, just ask me.

Thanks in advance.

---

### Post by pytheas22 on 2008-11-11
Agkelos: sorry to hear that you can't get it to work.  You may have a different version of the 5300 chipset than the others.

Please post the output of the following commands:
```

lspci -nn
lshw -C Network
modinfo iwlagn
modinfo iwl4965
sudo iwlist scan
dmesg | grep -e wlan -e iwl
```

---

### Post by Agkelos on 2008-11-12
Well, today I got a surprise... Without making anything, my intel 5300 started to work. The wireless led on the laptop is now on, and therefore, bam!, wireless on the go.

Thanks for the quick answer anyway, pytheas22. If it stops working all of a sudden I'll ask for your help again :).

---

### Post by lindylex on 2008-12-19
This is so easy to fix.

1. Compile a kernel >= 2.6.27
- If you use Debian use this tutorial on how to compile a kernel.
[http://forums.debian.net/viewtopic.php?t=20789](http://forums.debian.net/viewtopic.php?t=20789)
- If you use Ubuntu use this.
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

2. Use this link to download the correct kernel
[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

3. When you get to this command from the tutorials "make menuconfig", navigate to this part of the kernel configuration menu.
Device Drivers/Network device support/Wireless LAN/
+ Scroll down and choose.
Intel Wireless Wifi Next Gen AGN
+ Choose the following and place an star next to.
Intel Wireless WiFi 5000AGN
+ Choose Exit at the bottom until you save and exit.
4. Continue with the kernel compiling.

Work for me Debian Lenny, Linux trabajar 2.6.27.8 #1 SMP Sat Dec 13 01:18:36 EST 2008 x86_64 GNU/Linux, Intel Wireles 5300 AGN

---

### Post by SteveONCSU on 2009-05-05
> **lindylex said:**
> This is so easy to fix.

3. When you get to this command from the tutorials "make menuconfig", navigate to this part of the kernel configuration menu.
Device Drivers/Network device support/Wireless LAN/
+ Scroll down and choose.
Intel Wireless Wifi Next Gen AGN
+ Choose the following and place an star next to.
Intel Wireless WiFi 5000AGN
+ Choose Exit at the bottom until you save and exit.
4. Continue with the kernel compiling.



You know of all the threads I've read, this seems to be the crucial piece I've been missing.  Trying now...

I'm having the same problem with my thinkpad T500.  I MUST get the wireless working.

---

### Post by pytheas22 on 2009-05-05
> You know of all the threads I've read, this seems to be the crucial piece I've been missing. Trying now...

I'm having the same problem with my thinkpad T500. I MUST get the wireless working.

You don't need to compile an entire kernel just to get the Intel wireless working, and unless you're an experienced Linux hacker, you'll probably find that compiling a kernel is not "so easy" as lindylex writes above.

If you're using Ubuntu 8.10 or 9.04, the Intel wireless driver you need is already built into the kernel.  If you're using an older release of Ubuntu, you can download the latest compat-wireless code (which contains the Linux wireless drivers) from [http://wireless.kernel.org](http://wireless.kernel.org) and just compile that--no need to compile the entire kernel, which will take a really long time and requires advanced understanding of Linux.  I'd be happy to provide instructions on what you need to do if you post the output of these commands:
```

uname -rm
lspci -nn
lshw -C Network
```

---

### Post by GXP on 2009-05-05
This card is built-in on the Gateway P-7805u FX and it works out-of-the-box with 8.10, and 9.04 Beta2 (which I would also believe it to work with 9.04 final). It also works in 8.04.2 as this kernel has the driver also.

Did NOT work with 8.04 or 8.04.1

At the moment I am using 8.04.2 on this machine and have a 2nd partition to install 9.04 final. The iwlist, and related commands, work here - that is display results.

When I tried 9.04 beta2 from LiveUSB the iwlist was not showing the AP's  - actually I think the only option that worked was rate, but I will have to check again. Another thing I noticed with 9.04 was that instead of a connection speed of 48-54Mb like under 8.04.2 and Vista it was only around 1M under 9.04, and *sometimes* will connect at 48Mb. DISLAIMER: This might have been a 9.04 Beta 2 issue and I have not been able to find the time to try 9.04 final on this machine.

Suspend was not resuming if the interface was left on, if I turn off the interface and then suspend the machine will resume.

---

### Post by SteveONCSU on 2009-05-05
pytheas, I'm on 9.04 and I'm still having problems with the intel wireless 5300.  I can connect to any network and maintain a connection.  But then I randomly loose signal and the kernel crashes.  I get the flashing caps lock light to indicate this.

here is the output you wanted:

```
uname -rm
2.6.28-11-generic x86_64
```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236]
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff)
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)
```

```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:68:0a:5f:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 ip=192.168.1.104 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:17:0d:84
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:58:b7:a6:37:c7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Any guidance would be much appreciated.

---

### Post by pytheas22 on 2009-05-05
Those of you having trouble with Intel wireless on 9.04 should please follow the instructions below, which will compile the iwlagn driver from the latest code.  This should hopefully fix the issues you're experiencing.

First, go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the file named *compat-wireless-2.6.tar.bz2*.  Save it to your desktop.  Then run these commands to compile and install the new driver:
```

cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make ###it will take a few minutes here to compile
sudo make unload
sudo make load
sudo make install
```

After this, reboot and see if it works better.  If you still experience stability or speed problems, please post the output of:
```

modinfo iwlagn
dmesg | grep -e wlan -e iwl
```

---

### Post by SteveONCSU on 2009-05-05
Thanks for the instructions.  Everything seems to be fine right now.  I can't speak to early because normally it takes about 24 hours for the first crash to happen.  Guess if I make it through the next few days then it worked.

---

### Post by SteveONCSU on 2009-05-05
Having seen the kernel crash yet (feeling a tad bit more confident).  Here is one error I've noticed by using the dmesg command:

```
[10101.382414] wlan0: AP denied association (code=12)
```

I've had a few drops here in the past hour and this seems to be the error.  I also remember this prior to my last few kernel crashes.  Could this be associated with my router?  I do have DD-WRT setup on it...

---

### Post by pytheas22 on 2009-05-06
I'm not sure if that error message is related to the crash or not--failure to associate sounds like it would have to do with connecting to the router the first time, not losing the connection after you're already connected.  Do you see anything else in dmesg that looks relevant to the dropping connection?

That said, I did google the error line you posted and found this [bug report]("https://bugs.launchpad.net/ubuntu/+bug/183619").  Someone there (see the last post) says that changing his or her router's settings to operate at 24MB/s rather than 'Auto' solved the problem.  It might be worth a shot to see if it would also help in your case.

---

### Post by SteveONCSU on 2009-05-06
Good news, my system didn't crash all day after applying the drivers.  I think your method worked :)

---

### Post by pytheas22 on 2009-05-07
> Good news, my system didn't crash all day after applying the drivers. I think your method worked 

Good to hear; please report back if it does crash.  You should also keep in mind that you will need to recompile the wireless driver using the steps in post #36 when you update to a newer kernel; otherwise you'll revert back to the stock Ubuntu driver, which apparently is not stable for you (of course, they may fix that in the future, obviating the need to compile your own driver).

(Ubuntu updates will push out a new kernel about once a month; you'll know when it's installed because you will be prompted to restart your system.)

---

### Post by mystrangeusername on 2009-05-20
My Intel WiFi Link 5300 AGN is not working on Ubuntu 9.04. I tried using the gnome network manager, wicd  and compiling by myself the driver as suggested in one of the last post. I can see the networks but I can not connect to no one, neither disabling the encryption.

With "dmesg | grep -e wlan -e iwl" I obtain:
```

[    9.409731] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.409732] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.409838] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.409864] iwlagn 0000:0e:00.0: setting latency timer to 64
[    9.409944] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.430782] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.430840] iwlagn 0000:0e:00.0: irq 2295 for MSI/MSI-X
[    9.480961] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.067890] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   14.280937] iwlagn 0000:0e:00.0: loaded firmware version 5.4.1.16
[   14.436306] Registered led device: iwl-phy0::radio
[   14.436731] Registered led device: iwl-phy0::assoc
[   14.436743] Registered led device: iwl-phy0::RX
[   14.436752] Registered led device: iwl-phy0::TX
[   14.517447] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.104251] Registered led device: iwl-phy0::radio
[   57.104270] Registered led device: iwl-phy0::assoc
[   57.104282] Registered led device: iwl-phy0::RX
[   57.104293] Registered led device: iwl-phy0::TX
[   57.121900] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.205805] wlan0: direct probe to AP ffff88013d165b28 try 1
[   57.205818] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   57.404052] wlan0: direct probe to AP ffff88013d165b28 try 2
[   57.404075] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   57.604048] wlan0: direct probe to AP ffff88013d165b28 try 3
[   57.604057] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   57.804048] wlan0: direct probe to AP ffff88013d165b28 timed out
[   72.193729] Registered led device: iwl-phy0::radio
[   72.194772] Registered led device: iwl-phy0::assoc
[   72.194786] Registered led device: iwl-phy0::RX
[   72.194797] Registered led device: iwl-phy0::TX
[   72.213877] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.909794] wlan0: direct probe to AP ffff88013d165b28 try 1
[   75.910368] wlan0: direct probe to AP ffff88013d165b28 try 1
[   75.910884] wlan0: direct probe to AP ffff88013d165b28 try 1
[   76.108043] wlan0: direct probe to AP ffff88013d165b28 try 2
[   76.308032] wlan0: direct probe to AP ffff88013d165b28 try 3
[   76.508263] wlan0: direct probe to AP ffff88013d165b28 timed out
[   83.972677] wlan0: direct probe to AP ffff88013d165b28 try 1
[   84.172266] wlan0: direct probe to AP ffff88013d165b28 try 2
[   84.368981] wlan0: direct probe to AP ffff88013d165b28 try 3
[   84.568069] wlan0: direct probe to AP ffff88013d165b28 timed out
[   92.037062] wlan0: direct probe to AP ffff88013d165b28 try 1
[   92.236058] wlan0: direct probe to AP ffff88013d165b28 try 2
[   92.436082] wlan0: direct probe to AP ffff88013d165b28 try 3
[   92.636741] wlan0: direct probe to AP ffff88013d165b28 timed out
[  105.540798] wlan0: direct probe to AP ffff88013d165b28 try 1
[  105.740084] wlan0: direct probe to AP ffff88013d165b28 try 2
[  105.940285] wlan0: direct probe to AP ffff88013d165b28 try 3
[  106.140292] wlan0: direct probe to AP ffff88013d165b28 timed out
[  113.213029] wlan0: direct probe to AP ffff88013d165b28 try 1
[  113.412074] wlan0: direct probe to AP ffff88013d165b28 try 2
[  113.612279] wlan0: direct probe to AP ffff88013d165b28 try 3
[  113.812296] wlan0: direct probe to AP ffff88013d165b28 timed out
[  121.281504] wlan0: direct probe to AP ffff88013d165b28 try 1
[  121.480091] wlan0: direct probe to AP ffff88013d165b28 try 2
[  121.680267] wlan0: direct probe to AP ffff88013d165b28 try 3
[  121.880091] wlan0: direct probe to AP ffff88013d165b28 timed out
[  129.349334] wlan0: direct probe to AP ffff88013d165b28 try 1
[  129.548296] wlan0: direct probe to AP ffff88013d165b28 try 2
[  129.748315] wlan0: direct probe to AP ffff88013d165b28 try 3
[  129.948077] wlan0: direct probe to AP ffff88013d165b28 timed out
[  137.423349] wlan0: direct probe to AP ffff88013d165b28 try 1
[  137.620286] wlan0: direct probe to AP ffff88013d165b28 try 2
[  137.820311] wlan0: direct probe to AP ffff88013d165b28 try 3
[  138.020306] wlan0: direct probe to AP ffff88013d165b28 timed out
[  145.486118] wlan0: direct probe to AP ffff88013d165b28 try 1
[  145.684273] wlan0: direct probe to AP ffff88013d165b28 try 2
[  145.884128] wlan0: direct probe to AP ffff88013d165b28 try 3
[  146.084262] wlan0: direct probe to AP ffff88013d165b28 timed out
[  153.561166] wlan0: direct probe to AP ffff88013d165b28 try 1
[  153.561853] wlan0: direct probe to AP ffff88013d165b28 try 1
[  153.760265] wlan0: direct probe to AP ffff88013d165b28 try 2
[  153.960260] wlan0: direct probe to AP ffff88013d165b28 try 3
[  154.160266] wlan0: direct probe to AP ffff88013d165b28 timed out
[  164.012522] wlan0: direct probe to AP ffff88013d165b28 try 1
[  164.212045] wlan0: direct probe to AP ffff88013d165b28 try 2
[  164.320066] wlan0: deauthenticating by local choice (reason=3)

```

---

### Post by pytheas22 on 2009-05-21
mystrangeusername: please post the output of these commands as well so we can get a better idea of what's going wrong:
```

lshw -C Network
lspci -nn
modinfo iwlagn
uname -rm
sudo iwlist scan
```

Please also let me know the name of the network you want to connect to.

I see some interesting lines in dmesg that could explain the problem, but a bit more information will help.

---

### Post by mystrangeusername on 2009-05-21
lshw -C Network
```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:39:50:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:67:1a:95
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:c2:68:4e:c3:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M96 [Mobility Radeon HD 4650] [1002:9480]
01:00.1 Audio device [0403]: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series] [1002:aa38]
02:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
08:00.0 Memory controller [0580]: Intel Corporation Turbo Memory Controller [8086:444e] (rev 11)
0e:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

```

modinfo iwlagn
```

filename:       /lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-1.ucode
firmware:       iwlwifi-6050-2.ucode
firmware:       iwlwifi-6000-2.ucode
srcversion:     879A9D40ACFD34E461FD142
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00000085sv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001122bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001112bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001102bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211
vermagic:       2.6.28-11-generic SMP mod_unload modversions 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (uint)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```

uname -rn : techbook 2.6.28-11-generic

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:63:EE:72:1E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-10273343"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a57873004
                    Extra: Last beacon: 3260ms ago
                    IE: Unknown: 0011566F6461666F6E652D3130323733333433
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:18:39:83:04:BC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"FON_Taniverso"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048a3b0e1fb
                    Extra: Last beacon: 3452ms ago
                    IE: Unknown: 000D464F4E5F54616E69766572736F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
          Cell 03 - Address: 00:23:8E:4A:6E:AC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Alice-37859572"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fc64e4292e
                    Extra: Last beacon: 3320ms ago
                    IE: Unknown: 000E416C6963652D3337383539353732
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1F:33:02:F4:5E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MISTRAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aada4b2183
                    Extra: Last beacon: 2980ms ago
                    IE: Unknown: 00074D49535452414C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
          Cell 05 - Address: 00:1D:6A:D8:94:53
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Alice-98534542"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000209e9dd181
                    Extra: Last beacon: 2928ms ago
                    IE: Unknown: 000E416C6963652D3938353334353432
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706495420010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

pan0      Interface doesn't support scanning.

```

I executed this commands just after boot, wthout try to connect before.

The SSID of my network is Vodafone-10273343

Thanks a lot!

---

### Post by pytheas22 on 2009-05-21
Thanks for that information.  Please try disabling security on your router, then run these commands:
```

sudo iwconfig wlan0 mode managed channel 1 essid "Vodafone-10273343"
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

This should connect you to the network manually.  Does this work?  Depending on the results of this test, we'll know how to go about fixing the problem permanently.

If the commands above fail, it would be useful to see an output of:

```
dmesg | grep -e wlan -e iwl
```

after running them.

---

### Post by mystrangeusername on 2009-05-21
Also disabling security it doesn't work
```

There is already a pid file /var/run/dhclient.pid with pid 3756
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:21:6a:39:50:de
Sending on   LPF/wlan0/00:21:6a:39:50:de
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

federico@techbook:~$ dmesg | grep -e wlan -e iwl
[    9.566250] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.566250] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.566331] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.566338] iwlagn 0000:0e:00.0: setting latency timer to 64
[    9.566375] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.587226] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.587284] iwlagn 0000:0e:00.0: irq 2295 for MSI/MSI-X
[    9.672764] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.318458] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   14.548100] iwlagn 0000:0e:00.0: loaded firmware version 5.4.1.16
[   14.703122] Registered led device: iwl-phy0::radio
[   14.703147] Registered led device: iwl-phy0::assoc
[   14.703158] Registered led device: iwl-phy0::RX
[   14.703168] Registered led device: iwl-phy0::TX
[   14.730182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  253.627329] wlan0: direct probe to AP ffff88013e57bb28 try 1
[  253.824279] wlan0: direct probe to AP ffff88013e57bb28 try 2
[  253.883349] wlan0: direct probe to AP ffff88013e57bb28 try 1
[  254.080300] wlan0: direct probe to AP ffff88013e57bb28 try 2
[  254.280322] wlan0: direct probe to AP ffff88013e57bb28 try 3
[  254.480137] wlan0: direct probe to AP ffff88013e57bb28 timed out

```

---

### Post by pytheas22 on 2009-05-21
hmmm, I'm not sure why this won't work.  Here are a couple more ideas:

1. install updated firmware for the card by typing:
```

wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz
tar -xzvf iwlwifi-5000-ucode-8.24.2.12.tgz 
sudo cp iwlwifi-5000-ucode-8.24.2.12/iwlwifi-5000-2.ucode /lib/firmware/iwlwifi-5000-1.ucode
```

2. try changing your wireless router to operate on a different channel.  I see that there's another router nearby that's also on channel 1; there could be interference (not likely to help but worth a try).

3. I think you said you already recompiled the driver from source, but it might help to try again (by following the instructions in post #36).  Sometimes it happens that you compile on the wrong day, and get a bad snapshot of the code; trying again a few days later often helps.

4. if possible, it would be good to know if you can connect to other routers.  Can you bring your computer somewhere else (e.g., a café or university) and try connecting to the wireless there?

---

### Post by mystrangeusername on 2009-05-26
Hello. My dear Intel Wifi Link 5300 AGN is keeping NOT working (neither under Windows 7, btw). What I did? I changed it. And now?
It is still not working...
I updated the firware and compiled the modules by myself (new version available in respect to the one specified in post #36). The card not appears to be named wlan1 instead of wlan0. I am executing connections test on another router (that other pc can connect to).

Executing lshw -C Network just the serial is changed.

Executing modinfo iwlagn I get:

```

filename:       /lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-2.ucode
firmware:       iwlwifi-6000-2.ucode
srcversion:     2854367206201453FD23906
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00000085sv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001122bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001112bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001102bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211
vermagic:       2.6.28-11-generic SMP mod_unload modversions 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (uint)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```

note that both the firmwares iwlwifi-5000-1.ucode and iwlwifi-5000-2.ucode are present.
When I downloaded the firmware it was named iwlwifi-5000-2.ucode and
in this thread was suggested to save it as iwlwifi-5000-1.ucode. I saved it
both as *-1.ucode & *-2.ucode just because... well I am ignorant and I tried.

iwlist scan
```

wlan1     Scan completed :
          Cell 01 - Address: 00:19:3E:4C:28:0D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Alice-01370094"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000611dea188
                    Extra: Last beacon: 880ms ago
                    IE: Unknown: 000E416C6963652D3031333730303934
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1D:6A:A6:89:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Alice-78686240"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000321550581
                    Extra: Last beacon: 988ms ago
                    IE: Unknown: 000E416C6963652D3738363836323430
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD2C0050F204104A000110104400010210570001001047001011223344556677889900ABCDEF010203103C000101
          Cell 03 - Address: 00:14:BF:6F:CB:84
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"retecasa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006711749155
                    Extra: Last beacon: 4556ms ago
                    IE: Unknown: 00087265746563617361
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:1D:8B:5A:FF:C4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Alice-95208243"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f9d909183
                    Extra: Last beacon: 4692ms ago
                    IE: Unknown: 000E416C6963652D3935323038323433
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

I executed also dmesg | grep wl

```

[    9.633653] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.633655] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.633811] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.633845] iwlagn 0000:0e:00.0: setting latency timer to 64
[    9.634338] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.671567] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.671626] iwlagn 0000:0e:00.0: irq 2295 for MSI/MSI-X
[    9.714565] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.717856] udev: renamed network interface wlan0 to wlan1
[   19.280343] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   19.392680] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12
[   19.573035] Registered led device: iwl-phy0::radio
[   19.573053] Registered led device: iwl-phy0::assoc
[   19.573070] Registered led device: iwl-phy0::RX
[   19.573089] Registered led device: iwl-phy0::TX
[   19.587319] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.376745] wlan1: direct probe to AP ffff88013d106b28 try 1
[   26.576070] wlan1: direct probe to AP ffff88013d106b28 try 2
[   26.776080] wlan1: direct probe to AP ffff88013d106b28 try 3
[   26.976069] wlan1: direct probe to AP ffff88013d106b28 timed out
[  133.024399] wlan1: direct probe to AP ffff88013d106b28 try 1
[  133.224052] wlan1: direct probe to AP ffff88013d106b28 try 2
[  133.424053] wlan1: direct probe to AP ffff88013d106b28 try 3
[  133.624051] wlan1: direct probe to AP ffff88013d106b28 timed out
[  151.454546] wlan1: direct probe to AP ffff88013d106b28 try 1
[  151.652054] wlan1: direct probe to AP ffff88013d106b28 try 2
[  151.852070] wlan1: direct probe to AP ffff88013d106b28 try 3
[  152.052064] wlan1: direct probe to AP ffff88013d106b28 timed out
[  163.675501] wlan1: direct probe to AP ffff88013d106b28 try 1
[  163.872055] wlan1: direct probe to AP ffff88013d106b28 try 2
[  164.072075] wlan1: direct probe to AP ffff88013d106b28 try 3
[  164.272058] wlan1: direct probe to AP ffff88013d106b28 timed out
[  185.504881] wlan1: direct probe to AP ffff88013d106b28 try 1
[  185.704088] wlan1: direct probe to AP ffff88013d106b28 try 2
[  185.904100] wlan1: direct probe to AP ffff88013d106b28 try 3
[  186.104092] wlan1: direct probe to AP ffff88013d106b28 timed out
[  217.353936] wlan1: direct probe to AP ffff88013d106b28 try 1
[  217.552072] wlan1: direct probe to AP ffff88013d106b28 try 2
[  217.752062] wlan1: direct probe to AP ffff88013d106b28 try 3
[  217.952052] wlan1: direct probe to AP ffff88013d106b28 timed out
[  243.716133] wlan1: direct probe to AP ffff88013d106b28 try 1
[  243.916074] wlan1: direct probe to AP ffff88013d106b28 try 2
[  244.116013] wlan1: direct probe to AP ffff88013d106b28 try 3
[  244.316102] wlan1: direct probe to AP ffff88013d106b28 timed out
[  257.116434] wlan1: direct probe to AP ffff88013d106b28 try 1
[  257.316054] wlan1: direct probe to AP ffff88013d106b28 try 2
[  257.516051] wlan1: direct probe to AP ffff88013d106b28 try 3
[  257.716050] wlan1: direct probe to AP ffff88013d106b28 timed out
[  270.550983] wlan1: direct probe to AP ffff88013d106b28 try 1
[  270.749045] wlan1: direct probe to AP ffff88013d106b28 try 2
[  270.948062] wlan1: direct probe to AP ffff88013d106b28 try 3
[  271.148063] wlan1: direct probe to AP ffff88013d106b28 timed out
[  283.950804] wlan1: direct probe to AP ffff88013d106b28 try 1
[  284.148048] wlan1: direct probe to AP ffff88013d106b28 try 2
[  284.348071] wlan1: direct probe to AP ffff88013d106b28 try 3
[  284.548055] wlan1: direct probe to AP ffff88013d106b28 timed out
[  314.208233] wlan1: direct probe to AP ffff88013d106b28 try 1
[  314.409053] wlan1: direct probe to AP ffff88013d106b28 try 2
[  314.608051] wlan1: direct probe to AP ffff88013d106b28 try 3
[  314.808698] wlan1: direct probe to AP ffff88013d106b28 timed out
[  335.532601] wlan1: direct probe to AP ffff88013d106b28 try 1
[  335.732053] wlan1: direct probe to AP ffff88013d106b28 try 2
[  335.932051] wlan1: direct probe to AP ffff88013d106b28 try 3
[  336.132051] wlan1: direct probe to AP ffff88013d106b28 timed out
[  340.500027] wlan1: direct probe to AP ffff88013d106b28 try 1
[  340.696051] wlan1: direct probe to AP ffff88013d106b28 try 2
[  340.896067] wlan1: direct probe to AP ffff88013d106b28 try 3
[  341.096047] wlan1: direct probe to AP ffff88013d106b28 timed out
[  353.934950] wlan1: direct probe to AP ffff88013d106b28 try 1
[  354.132049] wlan1: direct probe to AP ffff88013d106b28 try 2
[  354.332061] wlan1: direct probe to AP ffff88013d106b28 try 3
[  354.532045] wlan1: direct probe to AP ffff88013d106b28 timed out
[  375.763060] wlan1: direct probe to AP ffff88013d106b28 try 1
[  375.960063] wlan1: direct probe to AP ffff88013d106b28 try 2
[  376.160072] wlan1: direct probe to AP ffff88013d106b28 try 3
[  376.360059] wlan1: direct probe to AP ffff88013d106b28 timed out
[  389.163355] wlan1: direct probe to AP ffff88013d106b28 try 1
[  389.360059] wlan1: direct probe to AP ffff88013d106b28 try 2
[  389.560057] wlan1: direct probe to AP ffff88013d106b28 try 3
[  389.760053] wlan1: direct probe to AP ffff88013d106b28 timed out

```

and dmesg | grep iw
```

[    9.633653] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.633655] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.633811] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.633845] iwlagn 0000:0e:00.0: setting latency timer to 64
[    9.634338] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.671567] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.671626] iwlagn 0000:0e:00.0: irq 2295 for MSI/MSI-X
[    9.714565] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.280343] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   19.392680] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12
[   19.573035] Registered led device: iwl-phy0::radio
[   19.573053] Registered led device: iwl-phy0::assoc
[   19.573070] Registered led device: iwl-phy0::RX
[   19.573089] Registered led device: iwl-phy0::TX

```

So any suggestion? What can I try (well, changing notebook is not a good advice :D )

desperately yours,
Federico

---

### Post by mystrangeusername on 2009-05-26
I also tried to connect manually using a guide ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) and I obtained this messages (maybe they are useful):

sudo wpa_supplicant -Dwext -i wlan1 -c /etc/wpa_supplicant.conf -dd
```

Initializing interface 'wlan1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     41 6c 69 63 65 2d 39 35 32 30 38 32 34 33         Alice-95208243  
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=24): [REMOVED]

pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Alice-95208243'
Initializing interface (2) 'wlan1'
Interface wlan1 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:21:6a:1f:fa:3a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan1
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Cached scan results are empty - not posting
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 825 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 414 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 371 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 0 bytes of scan results (0 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 414 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 825 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 785 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 1196 bytes of scan results (3 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:14:bf:6f:cb:84 ssid='retecasa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 825 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 30 seconds

```

In particular maybe is interesting this portion:
```

Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 825 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip WPA IE - PTK cipher mismatch
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:3e:4c:28:0d ssid='Alice-01370094' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.

```
It is skipping my AP 'Alice-95...' with the message  "skip WPA IE - PTK cipher mismatch"

---

### Post by pytheas22 on 2009-05-26
**mystrangeusername**: your device doesn't work on Windows either?  If so, there's probably a problem with the wireless card itself; this is not something we can fix under Ubuntu.  Can you try calling your PC manufacturer to ask for support?  They may need to replace your wireless card.

If I'm misunderstanding and this card *does* work on Windows, but not on Ubuntu, let me know and we can keep trying to fix it.

---

### Post by mystrangeusername on 2009-05-26
It does not work under Windows BUT I already changed my network card... and it is still not working...

Now I am trying connecting manually but I keep getting errors...
My router uses WPA-PSK AES and I configured wpa_supplicant.conf in theese way:
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="Alice-95208243"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="lu2tzfqmpztulx6a5yy78ntl"
        pairwise=CCMP TKIP
        #group=CCMP
}

I obtain:
```

federico@techbook:~$ sudo wpa_supplicant -Dwext -i wlan1 -c /etc/wpa_supplicant.conf -dd
Initializing interface 'wlan1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     41 6c 69 63 65 2d 39 35 32 30 38 32 34 33         Alice-95208243  
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=24): [REMOVED]

pairwise: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Alice-95208243'
Initializing interface (2) 'wlan1'
Interface wlan1 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:21:6a:1f:fa:3a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan1
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 466 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:6a:a6:89:20 ssid='Alice-78686240' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:6a:a6:89:20 ssid='Alice-78686240' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN]: Device or resource busy
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: disable timer tick
Scan timeout - try to get results
Received 1663 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1d:8b:5a:ff:c4 ssid='Alice-95208243'
Trying to associate with 00:1d:8b:5a:ff:c4 (SSID='Alice-95208243' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:1d:8b:5a:ff:c4 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
No keys have been configured - skip key clearing
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b19 len=16
Received 785 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:8b:5a:ff:c4 ssid='Alice-95208243' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1d:8b:5a:ff:c4 ssid='Alice-95208243'
Trying to associate with 00:1d:8b:5a:ff:c4 (SSID='Alice-95208243' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:1d:8b:5a:ff:c4 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0

```

---

### Post by pytheas22 on 2009-05-26
mystrangeusername: can you connect with encryption disabled on your router?  And can you try connecting to a different router?  If you can't connect to your router under either Windows or Ubuntu, and you don't think there's a hardware problem with your wireless card itself, then the only thing that makes sense is that your router is set up in a strange way that causes problems.  So it would be good to know if you have trouble connecting to a router somewhere else, and if you can connect with WPA disabled.

I'm not sure why your attempt to connect using wpa_supplicant is failing.  It looks like it associates and authenticates as expected, but then disassociates for some reason without really explaining why.  You could try running with the '-ddd' argument, but I'm not sure if that would increase debugging verbosity any more; I think you might already be maxed out on verbosity.

---

### Post by mystrangeusername on 2009-05-27
Maybe is it an hardware problem not related to the wireless card (i.e. the cables connecting the card to the mainboard or something else)?

I tried with two routers that are used by other computers and they work correctly.

With both of them I tried very near to the router (20-50 centimeters) so I don't think it's a problem related to interferences. With one router I tried disabling all the security, with the other I can't: I can just configure it to use WEP or WPA. 

I really have not more ideas.... probably I will have to send the whole notebook to be checked but I am pretty sure that also the manufacturer will not know what to do...

---

### Post by pytheas22 on 2009-05-27
Yes, if you can't connect to any routers at all with this computer, under any operating system, then I think it's fair to conclude there's a problem with the wireless card or some other part of the computer.

You could also just purchase a USB wireless card.  There's a [list]("https://wiki.ubuntu.com/WifiDocs/WirelessCardsSupported?action=show&redirect=HardwareSupportComponentsWirelessNetworkCards") of cards that are supposed to work well with Ubuntu.

---

### Post by svaret on 2009-06-02
Hi,

I have the same wireless card. I have downloaded, compiled and installed the driver.

However, I want to access WWAN instead of WLAN.

Do I have to enter specific data for my WWAN provider in the Ubuntu settings?

Best regards
/Lasse

My output for the command you asked for earlier are:

lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:81:02:1b:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 ip=192.168.0.5 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:09:42:6e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:98:d6:90:83:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236]
86:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 06)
86:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 25)
86:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev bb)
86:09.3 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ff)

```modinfo iwlagn
```
filename:       /lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-2.ucode
firmware:       iwlwifi-6000-2.ucode
srcversion:     2854367206201453FD23906
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00000085sv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001122bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001112bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001102bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (uint)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (uint)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```uname -rm
```
2.6.28-11-generic i686
```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Input/output error

pan0      Interface doesn't support scanning.

```

---

### Post by pytheas22 on 2009-06-02
**svaret**: are you sure you can use this card to connect to a WWAN?  I don't have personal experience with WWANs, but my impression is that you need a special wireless adapter to connect to one, since they're based on cellular networks, which operate on a whole different spectrum and protocol.

Are you positive you're using your internal wireless card to connect to the WWAN in Windows?  You don't have an external USB stick or something?  Ubuntu will support WWANs just fine if you have a WWAN-compatible device, but I've never heard of anyone connecting to one using a normal wireless card.

I could be totally wrong about this, so please enlighten me if I am.

---

### Post by svaret on 2009-06-03
pytheas22,

I do not have a USB-stick. I insert a SIM-card just where the battery is placed. So the communication is done through some hardware that acts just like a mobile phone.

Maybe you are right, that I am focusing on the wrong hardware here. The question is what hardware I should focus on. Obviously it is not working out of the box since it says "Wireless is not enabled" when I try to choose another network connection than than LAN.

Best regards

svaret

---

### Post by svaret on 2009-06-03
One problem is that Gnome-network says that "wireless is disabled" even after downloading and installing drivers according to earlier in this thread. In windows I can connect perfectly with the wireless card, both to WWAN and WLAN. I performed the steps u presented earlier in this thread where I download, compile and install the drivers.

lshw
```

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1993MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 2534MHz
          capacity: 2534MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: Mobile 4 Series Chipset MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-ide UNCLAIMED
             description: IDE interface
             product: Mobile 4 Series Chipset PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: ide cap_list
             configuration: latency=0
        *-communication:1
             description: Serial controller
             product: Mobile 4 Series Chipset AMT SOL Redirection
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=serial latency=0
        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:24:81:02:1b:9e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 ip=192.168.0.5 latency=0 module=e1000e multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Wireless WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:6a:09:42:6e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:86:09.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:86:09.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:86:09.2
                version: bb
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=ricoh-mmc latency=176 maxlatency=5 mingnt=128 module=ricoh_mmc
                resources: iomemory:b08a87860-b08a8785f
           *-generic
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 9.3
                bus info: pci@0000:86:09.3
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=yenta_cardbus latency=255 maxlatency=255 mingnt=255 module=yenta_socket
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:13:6d:20:01:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by pytheas22 on 2009-06-03
svaret: I see from your 'lshw' output that there's a device named 'Mobile 4 Series Chipset MEI Controller' that's listed as unclaimed.  I'm guessing this might be the hardware that we need to focus on in order to figure out how to get your WWAN connection working.

Do you have any other information about the name of the WWAN device?  Is there any descriptive information printed on the SIM card, or does Windows tell you the name of the device?  Do you know which company manufactures it and where you downloaded the Windows drivers from?

I also see that there are some problems with the WLAN wireless device.  I don't think these are related to the issues with the WWAN, but we can try to solve them as well.

Please post the output of the following commands so I can get a better handle on what might be wrong:
```

lspci -nn
dmesg | grep -ie iwl -e wlan -e intel
```

Also, when you connect to the WWAN in Windows, how does it work?  Do you use Windows' built-in wireless-connection manager, or do you use a special utility?  Do you have to enter a username and password?  As I said, I don't have any personal experience with WWANs, so any information you can provide on how your connection works in Windows would be helpful.

---

### Post by svaret on 2009-06-04
Hi again,

The device that takes care of WWAN is [COLOR=#4BACC6][FONT=&quot]HP un2400 EV-DO/HSDPA Mobile Broadband Module
[/FONT][/COLOR]When I conneect to WWAN in Windows I activate HP Software. Communication Centre and some other HP software which is dedicated to this specific hardware I think. I only have to enter a PIN code in order to access the WWAN, as with an ordinary mobile phone.

Best regards
/Lasse


lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236]
86:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 06)
86:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 25)
86:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev bb)
86:09.3 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ff)
```

dmesg | grep -ie iwl -e wlan -e intel
```
[    0.000000]   Intel GenuineIntel
[    0.313408] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.400803] CPU1: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    2.866426] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.866428] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.955234] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    9.290678] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.526703] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.526705] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.526796] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.526823] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.526934] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.560770] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.560823] iwlagn 0000:03:00.0: irq 2296 for MSI/MSI-X
[    9.620336] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    9.620342] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.620399] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.626245] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.309114] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   19.443754] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   19.444157] iwlagn 0000:03:00.0: Radio disabled by HW RF Kill switch
[   19.445422] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by svaret on 2009-06-04
Also, maybe my problem should be made a new thread since it is about other hardware.

---

### Post by pytheas22 on 2009-06-04
Thanks for the information about the card name.  I found [this thread]("http://ubuntuforums.org/showthread.php?t=1008200&page=1"), which explains how to make it work.  It's a little more complicated than I thought, but it should still be possible.  Basically there are four steps:

1. upgrade your kernel to 2.6.30 (apparently older kernels don't support this device)
2. compile the qcserial module against the 2.6.30 kernel
3. install the gobi-loader utility to load firmware for the device
4. use wvdial or NetworkManager to connect to your network

Although this may sound hard, it shouldn't really be that bad as long as everything works as expected.  The one thing I will warn about, however, is that updating your kernel could possibly have unexpected consequences, so please make sure you back up everything important on Ubuntu.

To get the kernel upgraded, run these commands (you will need to be connected to the Internet first):
```

wget http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb
sudo dpkg -i wireless-crda_1.7_*.deb
sudo dpkg -i linux*.deb
```

If you receive any error messages, please post them here.  If there are no errors, reboot your system, and you should be in the new kernel.  To check, post the output of the command:
```

uname -r
```

Once you get this far, we can move on to the next steps.

Also, the internal wireless card doesn't seem to be working because it's disabled using switch, according to the 'dmesg' output.  This usually means there's a button or software switch (like Function+F2) that you need to toggle in order to turn your wireless on.

---

### Post by biasquez on 2009-06-06
hi, i have kernel 2.6.29, i compiled latest compat-wireless release and in /lib/firmware i have both firmware (*.1.ucode
 and *.2.ucode). 

sudo modinfo iwlagn 

filename:       /lib/modules/2.6.29.4-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-1.ucode
firmware:       iwlwifi-6050-2.ucode
firmware:       iwlwifi-6000-2.ucode


why i can't use iwlwifi-5000-2.ucode?

---

### Post by pytheas22 on 2009-06-06
**biasquez**: I don't know enough about iwlagn to know why it doesn't want to use that firmware file.  But is there a problem with your wireless as it stands now?  What is the device ID (XXXX:XXXX) of the card?

---

### Post by biasquez on 2009-06-07
> **pytheas22 said:**
> **biasquez**: I don't know enough about iwlagn to know why it doesn't want to use that firmware file.  But is there a problem with your wireless as it stands now?  What is the device ID (XXXX:XXXX) of the card?


sometimes, network is slow and i must reset wifi connection.
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by pytheas22 on 2009-06-07
**biasquez**: there could be several different reasons that your connection becomes slow, and I think it's unlikely that the firmware is the problem.  The next time the connection becomes slow, please open a terminal, run the following commands and post the output:
```

lspci -nn
dmesg | grep -e iwl -e wlan
dmesg | tail -50
ifconfig wlan0
iwconfig wlan0
```

Also, do you notice a pattern in the behavior?  Does the connection become slow when you're downloading large files or when you visit certain websites, for example?  Or does it seem random?

---

### Post by svaret on 2009-06-07
Thanx for your quick reply. /Lasse

Installing the kernel I got this

```
sudo dpkg -i linux*.deb
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630rc4-generic                                                                                   
 *  fglrx (8.600)...                                                            fglrx (8.600): Installing module.
  Kernel headers for 2.6.30-020630rc4-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.30-020630rc4-generic or equivalent.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```> **pytheas22 said:**
> Thanks for the information about the card name.  I found [this thread]("http://ubuntuforums.org/showthread.php?t=1008200&page=1"), which explains how to make it work.  It's a little more complicated than I thought, but it should still be possible.  Basically there are four steps:

1. upgrade your kernel to 2.6.30 (apparently older kernels don't support this device)
2. compile the qcserial module against the 2.6.30 kernel
3. install the gobi-loader utility to load firmware for the device
4. use wvdial or NetworkManager to connect to your network

Although this may sound hard, it shouldn't really be that bad as long as everything works as expected.  The one thing I will warn about, however, is that updating your kernel could possibly have unexpected consequences, so please make sure you back up everything important on Ubuntu.

To get the kernel upgraded, run these commands (you will need to be connected to the Internet first):
```

wget http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb
sudo dpkg -i wireless-crda_1.7_*.deb
sudo dpkg -i linux*.deb
```If you receive any error messages, please post them here.  If there are no errors, reboot your system, and you should be in the new kernel.  To check, post the output of the command:
```

uname -r
```Once you get this far, we can move on to the next steps.

Also, the internal wireless card doesn't seem to be working because it's disabled using switch, according to the 'dmesg' output.  This usually means there's a button or software switch (like Function+F2) that you need to toggle in order to turn your wireless on.

---

### Post by pytheas22 on 2009-06-08
Sorry that didn't work.  Please try running this; it should solve the dependency:
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-headers-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb
sudo dpkg -i linux*.deb
```

This may take some trial and error, but we'll get there eventually...

---

### Post by SteveONCSU on 2009-07-08
Pytheas, you helped me a while back in this thread by getting my drivers installed correctly.  Before I was having random disconnects.  That being fixed, I still have disconnects only this time I've narrowed the cause down to trying to play a large movie across the network from my NAS.  So instead of being random, they occur when I do something.

I've run your diagnostic commands here:
> 
soverton@SteveO-Laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236]
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff)
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)
soverton@SteveO-Laptop:~$ dmesg | grep -e iwl -e wlan
[    9.486423] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.486425] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.486505] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.486513] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.486552] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    9.506489] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.506555] iwlagn 0000:03:00.0: irq 2296 for MSI/MSI-X
[    9.508408] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.109913] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   20.323369] Registered led device: iwl-phy0:radio
[   20.323382] Registered led device: iwl-phy0:assoc
[   20.323394] Registered led device: iwl-phy0:RX
[   20.323407] Registered led device: iwl-phy0:TX
[   20.977875] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.578397] wlan0: authenticate with AP 00:1c:10:0c:20:57
[   42.581228] wlan0: authenticated
[   42.581231] wlan0: associate with AP 00:1c:10:0c:20:57
[   42.586287] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=2)
[   42.586289] wlan0: associated
[   42.592451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.324596] wlan0: no IPv6 routers present
[18204.434098] wlan0: deauthenticated
[18204.434376] wlan0: deauthenticating by local choice (reason=14)
[18205.432570] wlan0: direct probe to AP 00:1c:10:0c:20:57 try 1
[18205.434959] wlan0 direct probe responded
[18205.434963] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18205.436729] wlan0: authenticated
[18205.436731] wlan0: associate with AP 00:1c:10:0c:20:57
[18205.441379] wlan0: RX ReassocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18205.441382] wlan0: AP denied association (code=12)
[18205.636533] wlan0: associate with AP 00:1c:10:0c:20:57
[18205.638881] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18205.638883] wlan0: AP denied association (code=12)
[18205.836549] wlan0: associate with AP 00:1c:10:0c:20:57
[18205.838915] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18205.838918] wlan0: AP denied association (code=12)
[18206.036551] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[18223.047573] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18223.050433] wlan0: authenticated
[18223.050437] wlan0: associate with AP 00:1c:10:0c:20:57
[18223.053279] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18223.053281] wlan0: AP denied association (code=12)
[18223.248550] wlan0: associate with AP 00:1c:10:0c:20:57
[18223.250896] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18223.250898] wlan0: AP denied association (code=12)
[18223.448124] wlan0: associate with AP 00:1c:10:0c:20:57
[18223.451549] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18223.451552] wlan0: AP denied association (code=12)
[18223.454810] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18223.454811] wlan0: AP denied association (code=12)
[18223.648103] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[18234.626280] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18234.628273] wlan0: authenticated
[18234.628275] wlan0: associate with AP 00:1c:10:0c:20:57
[18234.633870] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18234.633872] wlan0: AP denied association (code=12)
[18234.636470] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18234.636472] wlan0: AP denied association (code=12)
[18234.828058] wlan0: associate with AP 00:1c:10:0c:20:57
[18234.830432] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18234.830435] wlan0: AP denied association (code=12)
[18235.028060] wlan0: associate with AP 00:1c:10:0c:20:57
[18235.030466] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18235.030469] wlan0: AP denied association (code=12)
[18235.034102] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18235.034104] wlan0: AP denied association (code=12)
[18235.228129] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[18246.182992] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18246.185048] wlan0: authenticated
[18246.185051] wlan0: associate with AP 00:1c:10:0c:20:57
[18246.193258] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18246.193261] wlan0: AP denied association (code=12)
[18246.194212] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18246.194215] wlan0: AP denied association (code=12)
[18246.384111] wlan0: associate with AP 00:1c:10:0c:20:57
[18246.392157] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18246.392160] wlan0: AP denied association (code=12)
[18246.584609] wlan0: associate with AP 00:1c:10:0c:20:57
[18246.587014] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18246.587017] wlan0: AP denied association (code=12)
[18246.590909] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18246.590912] wlan0: AP denied association (code=12)
[18246.784111] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[18257.738815] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18257.740804] wlan0: authenticated
[18257.740807] wlan0: associate with AP 00:1c:10:0c:20:57
[18257.744201] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18257.744203] wlan0: AP denied association (code=12)
[18257.940114] wlan0: associate with AP 00:1c:10:0c:20:57
[18257.942491] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18257.942493] wlan0: AP denied association (code=12)
[18257.944924] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18257.944926] wlan0: AP denied association (code=12)
[18258.140112] wlan0: associate with AP 00:1c:10:0c:20:57
[18258.147804] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18258.147806] wlan0: AP denied association (code=12)
[18258.148796] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[18258.148799] wlan0: AP denied association (code=12)
[18258.340123] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[18269.263274] wlan0: authenticate with AP 00:1c:10:0c:20:57
[18269.269767] wlan0: authenticated
[18269.269770] wlan0: associate with AP 00:1c:10:0c:20:57
[18269.278370] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[18269.278373] wlan0: associated
[20154.193885] wlan0: deauthenticating by local choice (reason=14)
[20154.195534] wlan0: deauthenticated
[20172.073436] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20173.072106] wlan0: direct probe to AP 00:1c:10:0c:20:57 try 1
[20173.074487] wlan0 direct probe responded
[20173.074491] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20173.076284] wlan0: authenticated
[20173.076287] wlan0: associate with AP 00:1c:10:0c:20:57
[20173.078682] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20173.078684] wlan0: AP denied association (code=12)
[20173.276109] wlan0: associate with AP 00:1c:10:0c:20:57
[20173.278454] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20173.278457] wlan0: AP denied association (code=12)
[20173.476108] wlan0: associate with AP 00:1c:10:0c:20:57
[20173.478474] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20173.478477] wlan0: AP denied association (code=12)
[20173.676589] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20183.626095] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20183.626592] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20183.628760] wlan0: authenticated
[20183.628763] wlan0: associate with AP 00:1c:10:0c:20:57
[20183.631402] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20183.631405] wlan0: AP denied association (code=12)
[20183.828111] wlan0: associate with AP 00:1c:10:0c:20:57
[20183.830464] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20183.830467] wlan0: AP denied association (code=12)
[20184.028110] wlan0: associate with AP 00:1c:10:0c:20:57
[20184.030479] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20184.030481] wlan0: AP denied association (code=12)
[20184.228053] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20195.205515] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20195.207515] wlan0: authenticated
[20195.207518] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.210029] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.210031] wlan0: AP denied association (code=12)
[20195.404148] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.406549] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.406551] wlan0: AP denied association (code=12)
[20195.604111] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.606464] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.606467] wlan0: AP denied association (code=12)
[20195.804111] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20206.736938] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20206.738994] wlan0: authenticated
[20206.738997] wlan0: associate with AP 00:1c:10:0c:20:57
[20206.741395] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20206.741398] wlan0: AP denied association (code=12)
[20206.936318] wlan0: associate with AP 00:1c:10:0c:20:57
[20206.938740] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20206.938743] wlan0: AP denied association (code=12)
[20207.136109] wlan0: associate with AP 00:1c:10:0c:20:57
[20207.138480] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20207.138483] wlan0: AP denied association (code=12)
[20207.336110] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20218.290852] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20218.292868] wlan0: authenticated
[20218.292871] wlan0: associate with AP 00:1c:10:0c:20:57
[20218.295609] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[20218.295612] wlan0: associated
soverton@SteveO-Laptop:~$ dmesg | tail -50
[20173.276109] wlan0: associate with AP 00:1c:10:0c:20:57
[20173.278454] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20173.278457] wlan0: AP denied association (code=12)
[20173.476108] wlan0: associate with AP 00:1c:10:0c:20:57
[20173.478474] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20173.478477] wlan0: AP denied association (code=12)
[20173.676589] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20183.626095] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20183.626592] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20183.628760] wlan0: authenticated
[20183.628763] wlan0: associate with AP 00:1c:10:0c:20:57
[20183.631402] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20183.631405] wlan0: AP denied association (code=12)
[20183.828111] wlan0: associate with AP 00:1c:10:0c:20:57
[20183.830464] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20183.830467] wlan0: AP denied association (code=12)
[20184.028110] wlan0: associate with AP 00:1c:10:0c:20:57
[20184.030479] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20184.030481] wlan0: AP denied association (code=12)
[20184.228053] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20190.862003] CE: hpet increasing min_delta_ns to 50624 nsec
[20195.205515] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20195.207515] wlan0: authenticated
[20195.207518] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.210029] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.210031] wlan0: AP denied association (code=12)
[20195.404148] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.406549] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.406551] wlan0: AP denied association (code=12)
[20195.604111] wlan0: associate with AP 00:1c:10:0c:20:57
[20195.606464] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20195.606467] wlan0: AP denied association (code=12)
[20195.804111] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20206.736938] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20206.738994] wlan0: authenticated
[20206.738997] wlan0: associate with AP 00:1c:10:0c:20:57
[20206.741395] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20206.741398] wlan0: AP denied association (code=12)
[20206.936318] wlan0: associate with AP 00:1c:10:0c:20:57
[20206.938740] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20206.938743] wlan0: AP denied association (code=12)
[20207.136109] wlan0: associate with AP 00:1c:10:0c:20:57
[20207.138480] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[20207.138483] wlan0: AP denied association (code=12)
[20207.336110] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[20218.290852] wlan0: authenticate with AP 00:1c:10:0c:20:57
[20218.292868] wlan0: authenticated
[20218.292871] wlan0: associate with AP 00:1c:10:0c:20:57
[20218.295609] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[20218.295612] wlan0: associated
soverton@SteveO-Laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:6a:17:0d:84  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe17:d84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47456658 (47.4 MB)  TX bytes:4240623 (4.2 MB)

soverton@SteveO-Laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"stank"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:10:0C:20:57   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-28 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

soverton@SteveO-Laptop:~$ 


Can you help please?

---

### Post by pytheas22 on 2009-07-08
SteveONCSU: I think you're suffering from the bug reported [here]("https://bugs.launchpad.net/ubuntu/+bug/183619"), since you're using the iwl driver and see the same line in dmesg about ""AP denied association (code=12)."  Towards the end of the bug report (this [comment]("https://bugs.launchpad.net/ubuntu/+bug/183619/comments/27")), someone mentions that changing router speeds seems to help.  Please give this a try.

You could also try connecting with [wicd]("http://wicd.sourceforge.net") instead of NetworkManager.  I don't know if it will help, but it can't hurt.

If none of the above helps, you can try compiling the wireless driver using the latest source code by first going to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and saving the file compat-wireless-2.6.tar.bz2 to your desktop, then running these commands:
```

sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot for the new driver to take effect.

Please let me know if any of this helps; if not, we can try other things.

Also, is it only with one particular that you notice the crashes, or is it with any large file stored on your NAS?

---

### Post by SteveONCSU on 2009-07-09
Its with ANY large file.  I've only tried with movies but thats about all I can test with.

I will read the other links and post back within the next few days.

Thanks!

---

### Post by SteveONCSU on 2009-07-10
I changed to Wicd and I've set my wireless speeds to a constant 36mbps.  I'm still getting the same problem. I haven't upgraded my wireless drivers yet but I will try this later today and see what happens.

One thing I don't like about Wicd is you can't enable VPN access easily.  Any thoughts on this?

Here is the message log now, notice this error 'wlan0: deauthenticating by local choice (reason=3)':
> 
soverton@SteveO-Laptop:~$ dmesg | grep -e iwl -e wlan
[    7.278442] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    7.278444] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    7.278529] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.278537] iwlagn 0000:03:00.0: setting latency timer to 64
[    7.278570] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    7.298493] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[    7.298557] iwlagn 0000:03:00.0: irq 2296 for MSI/MSI-X
[    7.300617] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.634298] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   14.867569] Registered led device: iwl-phy0:radio
[   14.867587] Registered led device: iwl-phy0:assoc
[   14.867604] Registered led device: iwl-phy0:RX
[   14.867620] Registered led device: iwl-phy0:TX
[   14.959412] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.989084] Registered led device: iwl-phy0:radio
[   18.989100] Registered led device: iwl-phy0:assoc
[   18.989111] Registered led device: iwl-phy0:RX
[   18.989128] Registered led device: iwl-phy0:TX
[   19.009573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.264312] wlan0: authenticate with AP 00:1c:10:0c:20:57
[   19.264325] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   19.270515] wlan0: authenticated
[   19.270518] wlan0: associate with AP 00:1c:10:0c:20:57
[   19.270521] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   19.271143] wlan0: authenticate with AP 00:1c:10:0c:20:57
[   19.271148] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   19.273309] wlan0: authenticate with AP 00:1c:10:0c:20:57
[   19.273314] wlan0: authenticated
[   19.273316] wlan0: associate with AP 00:1c:10:0c:20:57
[   19.282014] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[   19.282016] wlan0: associated
[   19.312865] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.932040] wlan0: no IPv6 routers present
[  435.866221] wlan0: deauthenticating by local choice (reason=14)
[  435.869324] wlan0: deauthenticated
[  452.176089] Registered led device: iwl-phy0:radio
[  452.176518] Registered led device: iwl-phy0:assoc
[  452.176563] Registered led device: iwl-phy0:RX
[  452.176598] Registered led device: iwl-phy0:TX
[  452.204952] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  452.408544] Registered led device: iwl-phy0:radio
[  452.408984] Registered led device: iwl-phy0:assoc
[  452.409030] Registered led device: iwl-phy0:RX
[  452.409068] Registered led device: iwl-phy0:TX
[  452.585655] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  453.629255] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  453.629282] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  453.631294] wlan0: authenticated
[  453.631302] wlan0: associate with AP 00:1c:10:0c:20:57
[  453.631308] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  453.638734] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  453.639247] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  453.641231] wlan0: authenticated
[  453.641237] wlan0: associate with AP 00:1c:10:0c:20:57
[  453.643742] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  453.643747] wlan0: AP denied association (code=12)
[  453.840588] wlan0: associate with AP 00:1c:10:0c:20:57
[  453.842984] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  453.842990] wlan0: AP denied association (code=12)
[  454.040161] wlan0: associate with AP 00:1c:10:0c:20:57
[  454.042541] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  454.042546] wlan0: AP denied association (code=12)
[  454.240142] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[  463.637750] wlan0: direct probe to AP 00:1c:10:0c:20:57 try 1
[  463.640389] wlan0 direct probe responded
[  463.640396] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  463.642261] wlan0: authenticated
[  463.642267] wlan0: associate with AP 00:1c:10:0c:20:57
[  463.644629] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  463.644634] wlan0: AP denied association (code=12)
[  463.840129] wlan0: associate with AP 00:1c:10:0c:20:57
[  463.842524] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  463.842529] wlan0: AP denied association (code=12)
[  464.040127] wlan0: associate with AP 00:1c:10:0c:20:57
[  464.042615] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  464.042620] wlan0: AP denied association (code=12)
[  464.244118] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[  475.190639] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  475.193002] wlan0: authenticated
[  475.193009] wlan0: associate with AP 00:1c:10:0c:20:57
[  475.195466] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  475.195471] wlan0: AP denied association (code=12)
[  475.392140] wlan0: associate with AP 00:1c:10:0c:20:57
[  475.395909] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  475.395915] wlan0: AP denied association (code=12)
[  475.592081] wlan0: associate with AP 00:1c:10:0c:20:57
[  475.594510] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  475.594515] wlan0: AP denied association (code=12)
[  475.792158] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[  486.740772] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  486.742820] wlan0: authenticated
[  486.742826] wlan0: associate with AP 00:1c:10:0c:20:57
[  486.745435] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  486.745441] wlan0: AP denied association (code=12)
[  486.940130] wlan0: associate with AP 00:1c:10:0c:20:57
[  486.942680] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  486.942686] wlan0: AP denied association (code=12)
[  487.140141] wlan0: associate with AP 00:1c:10:0c:20:57
[  487.143599] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=12 aid=0)
[  487.143605] wlan0: AP denied association (code=12)
[  487.340161] wlan0: association with AP 00:1c:10:0c:20:57 timed out
[  497.510656] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  497.513953] wlan0: authenticated
[  497.513960] wlan0: associate with AP 00:1c:10:0c:20:57
[  497.516750] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[  497.516755] wlan0: associated
[  497.525536] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  497.820580] Registered led device: iwl-phy0:radio
[  497.821035] Registered led device: iwl-phy0:assoc
[  497.821079] Registered led device: iwl-phy0:RX
[  497.821118] Registered led device: iwl-phy0:TX
[  497.840833] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  497.864065] wlan0: deauthenticating by local choice (reason=3)
[  498.039653] Registered led device: iwl-phy0:radio
[  498.039691] Registered led device: iwl-phy0:assoc
[  498.039727] Registered led device: iwl-phy0:RX
[  498.039760] Registered led device: iwl-phy0:TX
[  498.060769] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  499.084940] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  499.086920] wlan0: authenticated
[  499.086926] wlan0: associate with AP 00:1c:10:0c:20:57
[  499.089502] wlan0: RX AssocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[  499.089508] wlan0: associated
[  499.093196] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  499.112539] wlan0: authenticate with AP 00:1c:10:0c:20:57
[  499.115673] wlan0: authenticated
[  499.115679] wlan0: associate with AP 00:1c:10:0c:20:57
[  499.118312] wlan0: RX ReassocResp from 00:1c:10:0c:20:57 (capab=0x431 status=0 aid=1)
[  499.118318] wlan0: associated
[  509.744523] wlan0: no IPv6 routers present


---

### Post by pytheas22 on 2009-07-11
SteveONCSU: it looks like the error message is different now, but I'm still not sure what's going on.  I think your best bet at this point would be to try compiling the drivers from source.  Please let me know if that helps.

---

### Post by SteveONCSU on 2009-07-12
I've upgraded the drivers and I'm still getting this error:

wlan0: AP denied association (code=12)

---

### Post by pytheas22 on 2009-07-12
Sorry it's still not working.  The only other ideas I have are:

1. try playing with your router's settings.  Changing from WPA1 to WPA2 (or vice-versa), switching to a different channel or experimenting with different modes (a vs. g vs. n) may make a difference.

2. switch to ndiswrapper instead of using the native Linux driver.  To get ndiswrapper working, I'd need to know whether you're using the 32- or 64-bit version of Ubuntu.  If you don't know, post the output of the command:
```

uname -m
```

Once we know that, it's just a matter of finding a Windows driver for your card that matches your kernel architecture and loading it into ndiswrapper.  If you have a link for the Windows driver that you use for your card, or could upload it somewhere (if it came on a CD), that would be helpful.

---

### Post by SteveONCSU on 2009-07-14
I'm running 64bit.  Is the ndiswrapper worth switching to?  Or should I hope the bug will be fixed in the future.

---

### Post by pytheas22 on 2009-07-15
I think ndiswrapper is definitely worth a try, given that none of the other approaches is working.

To get ndiswrapper running, you need a 64-bit Windows wireless driver for your card.  Unfortunately, I can't seem to find the right one.  I tried the driver for 5300 cards from [Intel's website]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3062&OSFullName=Windows*+XP+64-Bit+Edition&lang=eng&strOSs=43&submit=Go!"), but it doesn't match your PCI ID (which is 8086:4236).

If you could provide a link to the place where you downloaded the driver for your card in Windows, or upload the driver files somewhere (if they came on a CD), that would be very helpful.  If you can't do that, please let me know as much information as possible about the wireless card and your laptop model and manufacturer so I can try googling some more.

---

### Post by Truthiswithin on 2009-08-16
> **pytheas22 said:**
> **biasquez**: there could be several different reasons that your connection becomes slow, and I think it's unlikely that the firmware is the problem.  The next time the connection becomes slow, please open a terminal, run the following commands and post the output:
```

lspci -nn
dmesg | grep -e iwl -e wlan
dmesg | tail -50
ifconfig wlan0
iwconfig wlan0
```

Also, do you notice a pattern in the behavior?  Does the connection become slow when you're downloading large files or when you visit certain websites, for example?  Or does it seem random?

I have the same problem as Biasquez, and it is slow all the time.  Here are my (partial) outputs for you:

$ lspci -nn

```
07:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
```

$ dmesg | grep -e iwl

```
[ 1776.348960] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 1776.348962] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 1776.349320] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 1776.349352] iwlagn 0000:07:00.0: setting latency timer to 64
[ 1776.349401] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 1776.389786] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 1776.389854] iwlagn 0000:07:00.0: irq 29 for MSI/MSI-X
[ 1776.390174] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1776.401415] iwlagn 0000:07:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[ 1776.403962] iwlagn 0000:07:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[ 1776.403967] iwlagn 0000:07:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[ 1776.408129] iwlagn 0000:07:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[ 1776.408135] iwlagn 0000:07:00.0: loaded firmware version 8.24.2.12
``` 

Of note above is:

```
iwlagn 0000:07:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2

```

and wlan4:

```

[ 1776.577564] ADDRCONF(NETDEV_UP): wlan4: link is not ready
[ 1788.150457] wlan4: direct probe to AP 00:1e:8c:7a:53:cc (try 1)
[ 1788.152970] wlan4 direct probe responded
[ 1788.152977] wlan4: authenticate with AP 00:1e:8c:7a:53:cc (try 1)
[ 1788.155028] wlan4: authenticated
[ 1788.155065] wlan4: associate with AP 00:1e:8c:7a:53:cc (try 1)
[ 1788.157541] wlan4: RX AssocResp from 00:1e:8c:7a:53:cc (capab=0x411 status=0 aid=1)
[ 1788.157549] wlan4: associated
[ 1788.161084] ADDRCONF(NETDEV_CHANGE): wlan4: link becomes ready
[ 1799.156302] wlan4: no IPv6 routers present
[ 2394.215228] wlan4: deauthenticating by local choice (reason=3)
[ 2396.901076] Registered led device: iwl-phy0::radio
[ 2396.901119] Registered led device: iwl-phy0::assoc
[ 2396.901159] Registered led device: iwl-phy0::RX
[ 2396.901196] Registered led device: iwl-phy0::TX
[ 2396.926436] ADDRCONF(NETDEV_UP): wlan4: link is not ready
[ 2396.929038] ATL1E 0000:09:00.0: irq 30 for MSI/MSI-X
[ 2396.929549] ADDRCONF(NETDEV_UP): eth5: link is not ready
[ 2405.249592] wlan4: direct probe to AP 00:1e:8c:7a:53:cc (try 1)
[ 2405.251994] wlan4 direct probe responded
[ 2405.251998] wlan4: authenticate with AP 00:1e:8c:7a:53:cc (try 1)
[ 2405.253921] wlan4: authenticated
[ 2405.253964] wlan4: associate with AP 00:1e:8c:7a:53:cc (try 1)
[ 2405.256363] wlan4: RX AssocResp from 00:1e:8c:7a:53:cc (capab=0x411 status=0 aid=1)
[ 2405.256371] wlan4: associated
[ 2405.258531] ADDRCONF(NETDEV_CHANGE): wlan4: link becomes ready
[ 2415.873539] wlan4: no IPv6 routers present
```

$ ifconfig wlan4

```
wlan4     Link encap:Ethernet  HWaddr 00:21:6b:50:f8:12  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe50:f812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1743243 (1.7 MB)  TX bytes:195070 (195.0 KB)
```

$ iwconfig wlan4

```
wlan4     IEEE 802.11abgn  ESSID:"patrick805"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:8C:7A:53:CC   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


As I mentioned [here]("http://ubuntuforums.org/showpost.php?p=7793427&postcount=22"), I've got this problem in Ubuntu Karmic Alpha x64.  On Windows I can get 500kB/s+, and on Ubuntu, only 100+

I'm using Intel 5100 agn

Backports doesn't change anything for me, ndiswrapper doesn't seem to work (or I can't get it to).  

Router is a netgear cg814gcmr

Interestingly, using the Ethernet connection to the same router, the download speed is around 500kB/s, but the upload speed is no better.  Here's the speed test results:

wlan4:        
down (mbps) - 0.85
up (mbps)  -    0.54

eth0:
down (mbps) -          5.17
up (mbps)  -           0.54


Windows gives ~ the same results using wireless as I get with eth0 above: 5.3 down and 0.54 up.

---

### Post by Truthiswithin on 2009-08-16
Sorry, I figured it out.  What works for me is to remove linux-backports and compat-wireless.  Either/or gives me reduced speed on downloads.  Must be a bug in the compat-wireless?  Anyway, speed up to 600+ kB/s

Edit: Sorry, spoke a little too soon... it's down to 300+ kB/s now, and after a little while it goes back to 100+ kB/s.  Restarting the iwlagn module brings the speed back up, but only temporarily.  It eventually returns to 100+  What could be slowing it down?

---

### Post by SteveONCSU on 2009-08-20
The recent kernel upgrade broke my wireless again.  But going through the previous steps fixed :)

---

### Post by reel on 2009-09-02
I am having problems with the Intel 5300 as well. It is not being recognized by default with 9.04 on my EEE901. I can get it to be recognized by loading the modules from compat-wireless. However, it does not see any APs after doing that. 
uname -r
```

2.6.28-13-generic i686
```
lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1e Gigabit Ethernet Adapter [1969:1026] (rev b0)

```

lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:75:8e:0f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.147 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:cc:6b:a9:79:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Now if I do a make unload then make load with compat-wireless, I actually see something...

iwconfig
```
wlan0     IEEE 802.11abgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11abgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```
lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:75:8e:0f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.147 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:cc:6b:a9:79:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 02:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn
  *-network:2
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 02:00:00:00:01:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn
```

lspci still shows the same thing though.

Any advice? Thanks.

---

### Post by pytheas22 on 2009-09-02
reel: that's a bit bizarre.  It looks like you get two wireless interfaces after installing compat-wireless, which is strange.  You don't have two wireless cards for some reason, do you?

It's also strange that I don't see any device in your 'lspci' output that looks like a wireless card.  The hardware should be listed there even if the system is unable to bring it up.  Is there a setting in BIOS dealing with the wireless card?  Are you positive you have an Intel 5300 device?  This is an internal wireless card, not a USB stick, right?

---

### Post by reel on 2009-09-03
You are right. That is strange. I rebooted and this time it was seen. I am not sure why it wasn't seen that time. I still have the same problem though. It is definitely 5300 per the card label and not a USB stick.

Here are the relevant sections:

lspci -nn
```
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]
```

lshw -C Network
```
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
```

After manually running make unload then make load:

iwlist scan
```
wlan0     No scan results

wlan1     No scan results
```

lshw -C Network

```
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:75:8e:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e ip=192.168.1.147 latency=0 module=atl1e multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:41:a9:09:2a:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 02:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn
  *-network:2
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 02:00:00:00:01:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn
```

---

### Post by pytheas22 on 2009-09-03
reel: do you have Windows installed on this computer and does the wireless work there?  The behavior you describe sounds like it could be flaky hardware rather than a problem with the drivers in Ubuntu.  Having the card detected by 'lspci' only after certain reboots is not normal.

---

### Post by reel on 2009-09-03
> **pytheas22 said:**
> reel: do you have Windows installed on this computer and does the wireless work there?  The behavior you describe sounds like it could be flaky hardware rather than a problem with the drivers in Ubuntu.  Having the card detected by 'lspci' only after certain reboots is not normal.

I will give it a few reboots this evening to check it out. I suspect that the boot without it showing up in lspci was the exception. I typically saw it in lspci. I remember seeing it in lspci the first time I booted it up even. Thanks.

I do not have Windows installed on the computer.

---

### Post by reel on 2009-09-03
After a few reboots, I confirmed it is detected by lspci each time. I must have done something funny the first time that threw it off. So, I am stuck at the unclaimed 5300 and when I do make unload, make load with compat-wireless it brings us to the same situation I posted above.

---

### Post by reel on 2009-09-03
A bit more research has led me to believe that Intel does not support this version of the card in Linux. I have found the patch that introduced the error message. It indicates that this card is a pre-release version: [http://osdir.com/ml/linux-wireless/2009-05/msg00293.html](http://osdir.com/ml/linux-wireless/2009-05/msg00293.html). Supposedly it would work just fine in Windows though based on what I have read. Here is a bug report that is similar:
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997)

---

### Post by biasquez on 2009-09-04
for me, intel 5100 AGN works fine with kernel 2.6.30 but it doesn't work with kernel 2.6.31

to see more info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)

---

### Post by pytheas22 on 2009-09-04
> A bit more research has led me to believe that Intel does not support this version of the card in Linux. I have found the patch that introduced the error message. It indicates that this card is a pre-release version: [http://osdir.com/ml/linux-wireless/2.../msg00293.html](http://osdir.com/ml/linux-wireless/2.../msg00293.html). Supposedly it would work just fine in Windows though based on what I have read. Here is a bug report that is similar:
[http://bugzilla.intellinuxwireless.o...ug.cgi?id=1997](http://bugzilla.intellinuxwireless.o...ug.cgi?id=1997)

I helped someone a year ago in [this thread]("http://ubuntuforums.org/showthread.php?t=906865") getting your model of card (PCI ID 8086:4235) working on Ubuntu 8.04, so it should be supported.  It's possible there's been a regression and that using an older kernel, or an older snapshot of the compat-wireless source, would make things work.  As it is, I'm not sure what's going on because this dual-wlan* business is very strange, but it could be the result of a bad driver.

My advice would be to burn a live CD of Ubuntu 8.04, then follow the instructions from that thread I linked to above for getting the card working by compiling compat-wireless-old (you need the 'old' version to compile on Hardy) and downloading the iwlwifi ucode.  If it works in Hardy, that should help us figure out how to make it work in Jaunty.

---

### Post by reel on 2009-09-04
> **pytheas22 said:**
> I helped someone a year ago in [this thread]("http://ubuntuforums.org/showthread.php?t=906865") getting your model of card (PCI ID 8086:4235) working on Ubuntu 8.04, so it should be supported.  It's possible there's been a regression and that using an older kernel, or an older snapshot of the compat-wireless source, would make things work.  As it is, I'm not sure what's going on because this dual-wlan* business is very strange, but it could be the result of a bad driver.

My advice would be to burn a live CD of Ubuntu 8.04, then follow the instructions from that thread I linked to above for getting the card working by compiling compat-wireless-old (you need the 'old' version to compile on Hardy) and downloading the iwlwifi ucode.  If it works in Hardy, that should help us figure out how to make it work in Jaunty.

Unfortunately, the problem is the hardware. I am not at my computer to provide the dmesg and /var/log/messages to you but if you read that bug report I linked, mine are the same. I have exchanged emails with Reinette Chatre of Intel and she indicated that she was going to get someone internal to attempt to identify the card. The EEPROM being an old version is not a good sign though. If I edit the iwlagn driver to ignore the EEPROM check, the ucode fails because this version of the EEPROM is not supported in the Linux ucode. Reinette posted on the patch notice that they support all production hardware. This is likely a pre-release card or some sort of illegitimate copy. My inquiry to the seller has yielded no reply so far. I suspect I need to find a more legitimate seller. I have seen this card for sale from buy.com so that is where I am inclined to purchase to avoid a similar problem. Thanks for your help. Any suggestions on sellers?

---

### Post by pytheas22 on 2009-09-05
> Unfortunately, the problem is the hardware. I am not at my computer to provide the dmesg and /var/log/messages to you but if you read that bug report I linked, mine are the same. I have exchanged emails with Reinette Chatre of Intel and she indicated that she was going to get someone internal to attempt to identify the card. The EEPROM being an old version is not a good sign though. If I edit the iwlagn driver to ignore the EEPROM check, the ucode fails because this version of the EEPROM is not supported in the Linux ucode. Reinette posted on the patch notice that they support all production hardware. This is likely a pre-release card or some sort of illegitimate copy. My inquiry to the seller has yielded no reply so far. I suspect I need to find a more legitimate seller. I have seen this card for sale from buy.com so that is where I am inclined to purchase to avoid a similar problem. Thanks for your help. Any suggestions on sellers?

At least that clears up the strange behavior you were seeing.  It is weird that lspci identifies this device as the same as a other models, but that could just be a problem with lspci (or with the hardware misidentifying itself).

Unfortunately I've never bought internal wireless cards so I'm not sure where a good place to get one would be.  Hopefully the Intel people will be able to help you sort out this issue so you can get things working with your current device.

---

### Post by amouravski on 2009-09-12
Hello!

I have had trouble with the Intel WiFi Link 5300 ever since I got it. I thought I could just install drivers for it, but couldn't. Backstory: I was using the EeePC 1000 until I realized the built-in mobile adapter couldn't do WPA. I tried a half dozen solutions but it didn't work, so I bought the Intel 5300.

So, I have tried pytheas22's solution, but I am having trouble. Since the old drivers he mentioned only work up to 2.6.26 and I am running 2.6.28-15. I downloaded the most recent compat-wireless, thinking it would work, but I run into the following error at the end of the make:
```
andrei@jrisidore:~/compat-wireless-2009-09-12$ make
make -C /lib/modules/2.6.28-15-generic/build M=/home/andrei/compat-wireless-2009-09-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.o
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c: In function &#8216;b43_do_interrupt&#8217;:
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c:1888: error: &#8216;IRQ_WAKE_THREAD&#8217; undeclared (first use in this function)
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c:1888: error: (Each undeclared identifier is reported only once
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c:1888: error: for each function it appears in.)
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c: In function &#8216;b43_request_firmware&#8217;:
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c:2218: warning: format not a string literal and no format arguments
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c: In function &#8216;b43_wireless_core_start&#8217;:
/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.c:3871: error: implicit declaration of function &#8216;request_threaded_irq&#8217;
make[4]: *** [/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43/main.o] Error 1
make[3]: *** [/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless/b43] Error 2
make[2]: *** [/home/andrei/compat-wireless-2009-09-12/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/andrei/compat-wireless-2009-09-12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

```I have tried to look up the issue with IRQ_WAKE_THREAD, but only find references to Linux kernel commits and something called "genirq." I figure that I may be missing some library or other.

Currently my wireless is not working at all and would like some help. 

Thanks in advance.

---

### Post by -Riffer- on 2009-09-13
> **amouravski said:**
> Hello!

I have tried to look up the issue with IRQ_WAKE_THREAD, but only find references to Linux kernel commits and something called "genirq." I figure that I may be missing some library or other.


Hello!
 
All archives after 06.09.2009 have the same IRQ_WAKE_THREAD error, I do not know why. Maybe someone has mixed up the different kernels versions include-files.

But you could try the one from 06.09, because it is the last one that compiles for me.

Have a look here:
[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/09/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/09/)

---

### Post by reel on 2009-09-14
> **pytheas22 said:**
> At least that clears up the strange behavior you were seeing.  It is weird that lspci identifies this device as the same as a other models, but that could just be a problem with lspci (or with the hardware misidentifying itself).

Unfortunately I've never bought internal wireless cards so I'm not sure where a good place to get one would be.  Hopefully the Intel people will be able to help you sort out this issue so you can get things working with your current device.

To follow up, I ordered a new card from a legitimate seller. I received a box containing the card, driver CD, and warranty sheet. The card had a valid label. It worked instantly when I plugged it in (my previous attempts may have greased the wheels perhaps). It has better reception than my prior card that came with the laptop. I am pleased once more. Sad though that it took me 3 cards to find 1 good card. I received a defective SparkLAN card as my first one, the counterfeit Intel card, and finally this functional card. 

Be cautious when buying these cards from third parties!

---

### Post by disc0 on 2009-09-15
Hey,

I have a LG 510 with WIFI 5300 AGN too ..

My problem is because the option "enable wireless" cannot be clicked, so, I cannot configure the wireless..

I'm using ubuntu 9.04, so, Intel 5300 is alredy suported natively (I think) and
lshw -C Network

shows:
```

(...)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:2e:3a:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn


```think that the driver is already there and working (correct me if I'm wrong)

In windows, when I make the combination keys to activate/deactivate the wireless it pops a message on the screen saying that, here in ubuntu there is no message, so I don't really now if the combination is working.. For example, for turning monitor brightness up/down, sound, etc, all are working fine, so I supose that wireless would too ..


What am I doing wrong ??


**EDIT:** Ok, so right aftrer I posted here, I found in another forum (here from portugal) someone saying that the combination to turn on/off wifi(and bluetooth) in this notebook its not working in ubuntu..

The solution is boot on vista, turn wireless on there, reboot and boot on ubuntu.. I don't like this solution, it takes too much time just for a so simple thing :\ .. Can someone tell me some alternative method on how to "give power" to the wireless card directly on ubuntu ?? :\

Best regards,
João Henriques

---

### Post by -Riffer- on 2009-09-15
You may have a look into your bios settings wether there is an option to permanently power on your wlan?

---

### Post by jonlowe on 2009-09-15
Reel,
Whre did you end up getting your good card?  I've gotten a bad one also, and don't want to go thru this again.


> **reel said:**
> To follow up, I ordered a new card from a legitimate seller. I received a box containing the card, driver CD, and warranty sheet. The card had a valid label. It worked instantly when I plugged it in (my previous attempts may have greased the wheels perhaps). It has better reception than my prior card that came with the laptop. I am pleased once more. Sad though that it took me 3 cards to find 1 good card. I received a defective SparkLAN card as my first one, the counterfeit Intel card, and finally this functional card. 

Be cautious when buying these cards from third parties!

---

### Post by pytheas22 on 2009-09-15
disc0: yes, as another poster says, check your BIOS for a setting for permanently enabling the wireless.

You probably also have a button or hotkey (like function+F2) that you can use to toggle the wireless on and off.  See if that will do what you need.

It would also be useful to see the output of:

```
sudo iwlist scan
dmesg | grep -i radio

```

---

### Post by disc0 on 2009-09-15
Thanks for the tip, but I don't want a wlan permanent turned on..

The point is have it turned off and only when I need it, turn it on, saving battery life..

I said earlier that this is only being caused because the key combination to toggle on/off the wireless card in my notebook model don't work in ubuntu..

And **again**, as I asked before:
"Can someone tell me some alternative method on how to "give power" to the wireless card directly on ubuntu ?? :\"
Is there an alternative way to turn wireless card on without the key combination (for me is FN + F6) directly in ubuntu , kind of some shell command  ?? 

```

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

:~$ dmesg | grep -i radio
[   19.943080] iwlagn: Radio disabled by HW RF Kill switch


```

---

### Post by reel on 2009-09-16
> **jonlowe said:**
> Reel,
Whre did you end up getting your good card?  I've gotten a bad one also, and don't want to go thru this again.

I bought through Buy.com third party seller Beach Audio. It was cheaper than the others listed and seemed like a legitimate and accountable storefront. A quick check shows it has gone up since my order and is no longer the cheapest. Good luck with your new card.

---

### Post by theZoid on 2009-09-16
I have the intel 5300 and jaunty x64 worked out of the box.  fwiw

---

### Post by pytheas22 on 2009-09-17
> 
And again, as I asked before:
"Can someone tell me some alternative method on how to "give power" to the wireless card directly on ubuntu ?? :\"
Is there an alternative way to turn wireless card on without the key combination (for me is FN + F6) directly in ubuntu , kind of some shell command ??

On some laptops you can echo a value into a file in /sys that will turn the radio on, but the right file varies by laptop.  Try doing:
```

locate wlan | grep sys
```

and see if anything interesting shows up.

There may also be a way to make the Fn+F6 key work, which would probably be the ideal solution.  Have you tried googling for this issue?

---

### Post by disc0 on 2009-09-18
> **pytheas22 said:**
> On some laptops you can echo a value into a file in /sys that will turn the radio on, but the right file varies by laptop.  Try doing:
```

locate wlan | grep sys
```and see if anything interesting shows up.

There may also be a way to make the Fn+F6 key work, which would probably be the ideal solution.  Have you tried googling for this issue?

I tried googling but my this notebook is not owned by so much people.. Neither there is much people installing ubuntu..

Currently I'm on Vista and going sleep, tomorrow I'll give a try to see the output and post the results.. Many thanks

---

### Post by schoelli on 2009-10-08
Hi
If got a Lenovo W500 with Intel Wifi 5300 included. I installed Ubuntu 9.04 and configurated with wpa_supplicant it like it is described on: [http://wiki.ubuntuusers.de/WLAN/wpa_supplicant ]("http://wiki.ubuntuusers.de/WLAN/wpa_supplicant")

**My wpa_supplicant.conf:**
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
    ssid="XXXX"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    pairwise=CCMP TKIP
    group=TKIP
    psk=psk string translated by using wps_passphrase "SSID 63 ASCII Chars"
    }

After: **sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd **which seems to run forever without any errors.

I execute: **sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -B**

No errors.

So i dlike to get an ip using: **sudo dhclient wlan0**
There is already a pid file /var/run/dhclient.pid with pid 4340
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:6a:6e:0d:ae
Sending on   LPF/wlan0/00:21:6a:6e:0d:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[SIZE=4][SIZE=3]Someones got any idea what else i could try to get conected?[/SIZE][U][SIZE=3]

[/SIZE][/U][/SIZE][B][SIZE=4][U]More infos:

[/U][/SIZE]iwlist wlan0 scan[/B]
wlan0     Scan completed :
          Cell 01 - Address: 00:14:C1:19:EB:84
                    ESSID:"XXXX"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=77/100  Signal level:-57 dBm  Noise level=-127 dBm
                    Encryption key:eek:n
                    IE: Unknown: 000A46697368383154726565
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000121a7e52d
                    Extra: Last beacon: 4296ms ago
My Router is an:         U.S. Robotics Wireless *MAX*g ADSL Gateway

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"XXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:eek:ff   Fragment thr=2352 B
          Power Management:eek:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Do you need any more informations please let me know!
Thank you in advance for any advise!

I already tryed for hours many diffrent configurations!!:sad:

Regards,
Schoelli

---

### Post by glee on 2009-10-25
Hello, I have a recent Dell Studio 15 with a 5300 AGN card. I am trying to get this working under Ubuntu Hardy. I have read this thread and implemented many of the suggestions found here. The insight is much appreciated, but I am yet to get the card running.

I have built the updated kernel modules using both the current and 2008-09-09 versions. Build seems to progress ok under either one, make install and make unload report no serious problems that I can see. However, on running make load many modules report unknown symbols and fail to load, with obvious implications for dmesg reporting. You will note that lspci now reports several unknown hardware devices, which seems to be worse than when I started.

See below for details. Any insight appreciated. One final thing: I am running VirtualBox-3.0 with a network bridge (to allow a virtual Windows machine access to the outside world). Could this be a problem?

Thanks.


$ uname -a

```
Linux SCLS-SLN-14439 2.6.24-25-generic #1 SMP Tue Oct 20 06:49:12 UTC 2009 x86_64 GNU/Linux

```



$ lspci -nn
```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9553]
01:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa38]
04:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
09:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
09:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)


```



$ sudo lshw -C Network
```

  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:52:dd:e4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f6:b7:93
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.1 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```


$ dmesg | grep -e wlan -e iwl

```

[   34.651200] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   34.651204] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   34.652079] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   34.681699] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   34.682154] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   34.822833] lbm_iwl_cfg80211: exports duplicate symbol pm_qos_remove_requirement (owned by cfg80211)
[   34.826974] lbm_iwl_mac80211: Unknown symbol iwl_lbm_wiphy_new
[   34.827047] lbm_iwl_mac80211: Unknown symbol iwl_lbm_ieee80211_radiotap_iterator_next
[   34.827119] lbm_iwl_mac80211: Unknown symbol iwl_lbm_wiphy_register
[   34.827333] lbm_iwl_mac80211: Unknown symbol iwl_lbm___ieee80211_get_channel
[   34.827418] lbm_iwl_mac80211: Unknown symbol iwl_lbm_ieee80211_frequency_to_channel
[   34.827494] lbm_iwl_mac80211: Unknown symbol iwl_lbm_ieee80211_radiotap_iterator_init
[   34.827727] lbm_iwl_mac80211: Unknown symbol iwl_lbm_wiphy_unregister
[   34.827855] lbm_iwl_mac80211: Unknown symbol iwl_lbm_wiphy_free
[   34.828024] lbm_iwl_mac80211: Unknown symbol iwl_lbm_ieee80211_channel_to_frequency
[   34.833803] iwl4965: Unknown symbol iwl_lbm_iwl_lbm_ieee80211_wake_queues
[   34.833824] iwl4965: disagrees about version of symbol iwl_rxon_add_station
[   34.833825] iwl4965: Unknown symbol iwl_rxon_add_station
[   34.833846] iwl4965: disagrees about version of symbol iwl_scan_cancel_timeout
[   34.833848] iwl4965: Unknown symbol iwl_scan_cancel_timeout
[   34.833886] iwl4965: disagrees about version of symbol iwl_rfkill_set_hw_state
[   34.833887] iwl4965: Unknown symbol iwl_rfkill_set_hw_state
[   34.833924] iwl4965: disagrees about version of symbol iwl_send_statistics_request
[   34.833925] iwl4965: Unknown symbol iwl_send_statistics_request
[   34.833947] iwl4965: disagrees about version of symbol iwl_set_default_wep_key
[   34.833949] iwl4965: Unknown symbol iwl_set_default_wep_key
[   34.833968] iwl4965: disagrees about version of symbol iwl_scan_cancel
[   34.833969] iwl4965: Unknown symbol iwl_scan_cancel
[   34.834016] iwl4965: Unknown symbol iwl_lbm_ieee80211_unregister_hw
[   34.834035] iwl4965: disagrees about version of symbol iwl_chain_noise_calibration
[   34.834037] iwl4965: Unknown symbol iwl_chain_noise_calibration
[   34.834061] iwl4965: disagrees about version of symbol iwl_remove_dynamic_key
[   34.834062] iwl4965: Unknown symbol iwl_remove_dynamic_key
[   34.834084] iwl4965: Unknown symbol iwl_lbm_ieee80211_rate_control_unregister
[   34.834112] iwl4965: disagrees about version of symbol iwl_get_ra_sta_id
[   34.834113] iwl4965: Unknown symbol iwl_get_ra_sta_id
[   34.834141] iwl4965: disagrees about version of symbol iwl_rx_reply_compressed_ba
[   34.834143] iwl4965: Unknown symbol iwl_rx_reply_compressed_ba
[   34.834161] iwl4965: disagrees about version of symbol iwl_txq_update_write_ptr
[   34.834163] iwl4965: Unknown symbol iwl_txq_update_write_ptr
[   34.834182] iwl4965: disagrees about version of symbol iwl_rfkill_init
[   34.834183] iwl4965: Unknown symbol iwl_rfkill_init
[   34.834201] iwl4965: disagrees about version of symbol iwl_eeprom_free
[   34.834202] iwl4965: Unknown symbol iwl_eeprom_free
[   34.834240] iwl4965: disagrees about version of symbol iwl_set_rxon_channel
[   34.834241] iwl4965: Unknown symbol iwl_set_rxon_channel
[   34.834260] iwl4965: disagrees about version of symbol iwl_power_update_mode
[   34.834261] iwl4965: Unknown symbol iwl_power_update_mode
[   34.834279] iwl4965: disagrees about version of symbol iwlcore_eeprom_release_semaphore
[   34.834281] iwl4965: Unknown symbol iwlcore_eeprom_release_semaphore
[   34.834302] iwl4965: disagrees about version of symbol iwl_hw_txq_ctx_free
[   34.834303] iwl4965: Unknown symbol iwl_hw_txq_ctx_free
[   34.834340] iwl4965: disagrees about version of symbol iwl_eeprom_init
[   34.834341] iwl4965: Unknown symbol iwl_eeprom_init
[   34.834367] iwl4965: disagrees about version of symbol iwl_add_station_flags
[   34.834368] iwl4965: Unknown symbol iwl_add_station_flags
[   34.834404] iwl4965: disagrees about version of symbol iwl_radio_kill_sw_disable_radio
[   34.834406] iwl4965: Unknown symbol iwl_radio_kill_sw_disable_radio
[   34.834423] iwl4965: disagrees about version of symbol iwl_set_rxon_ht
[   34.834425] iwl4965: Unknown symbol iwl_set_rxon_ht
[   34.834457] iwl4965: Unknown symbol iwl_lbm_ieee80211_scan_completed
[   34.834486] iwl4965: Unknown symbol iwl_dbgfs_register
[   34.834515] iwl4965: Unknown symbol iwl_lbm_ieee80211_start_tx_ba_session
[   34.834532] iwl4965: disagrees about version of symbol iwl_txq_ctx_stop
[   34.834533] iwl4965: Unknown symbol iwl_txq_ctx_stop
[   34.834550] iwl4965: disagrees about version of symbol iwlcore_eeprom_acquire_semaphore
[   34.834552] iwl4965: Unknown symbol iwlcore_eeprom_acquire_semaphore
[   34.834576] iwl4965: disagrees about version of symbol iwl_init_drv
[   34.834577] iwl4965: Unknown symbol iwl_init_drv
[   34.834619] iwl4965: Unknown symbol iwl_lbm_ieee80211_beacon_get
[   34.834641] iwl4965: disagrees about version of symbol iwl_tx_cmd_complete
[   34.834642] iwl4965: Unknown symbol iwl_tx_cmd_complete
[   34.834665] iwl4965: disagrees about version of symbol iwl_rx_reply_rx_phy
[   34.834667] iwl4965: Unknown symbol iwl_rx_reply_rx_phy
[   34.834684] iwl4965: disagrees about version of symbol iwl_setup_rx_scan_handlers
[   34.834685] iwl4965: Unknown symbol iwl_setup_rx_scan_handlers
[   34.834702] iwl4965: disagrees about version of symbol iwl_send_cmd_pdu
[   34.834703] iwl4965: Unknown symbol iwl_send_cmd_pdu
[   34.834724] iwl4965: Unknown symbol iwl_lbm_iwl_lbm_ieee80211_stop_queues
[   34.834744] iwl4965: disagrees about version of symbol iwl_init_sensitivity
[   34.834745] iwl4965: Unknown symbol iwl_init_sensitivity
[   34.834769] iwl4965: disagrees about version of symbol iwl_rx_reply_rx
[   34.834770] iwl4965: Unknown symbol iwl_rx_reply_rx
[   34.834791] iwl4965: Unknown symbol iwl_lbm_ieee80211_frequency_to_channel
[   34.834808] iwl4965: disagrees about version of symbol iwl_reset_run_time_calib
[   34.834809] iwl4965: Unknown symbol iwl_reset_run_time_calib
[   34.834826] iwl4965: disagrees about version of symbol iwl_send_static_wepkey_cmd
[   34.834827] iwl4965: Unknown symbol iwl_send_static_wepkey_cmd
[   34.834849] iwl4965: Unknown symbol iwl_rf_kill
[   34.834896] iwl4965: disagrees about version of symbol iwl_clear_stations_table
[   34.834898] iwl4965: Unknown symbol iwl_clear_stations_table
[   34.834914] iwl4965: disagrees about version of symbol iwl_radio_kill_sw_enable_radio
[   34.834915] iwl4965: Unknown symbol iwl_radio_kill_sw_enable_radio
[   34.834931] iwl4965: disagrees about version of symbol iwl_uninit_drv
[   34.834932] iwl4965: Unknown symbol iwl_uninit_drv
[   34.834948] iwl4965: disagrees about version of symbol iwl_rx_missed_beacon_notif
[   34.834950] iwl4965: Unknown symbol iwl_rx_missed_beacon_notif
[   34.834990] iwl4965: disagrees about version of symbol iwl_eeprom_get_mac
[   34.834991] iwl4965: Unknown symbol iwl_eeprom_get_mac
[   34.835007] iwl4965: disagrees about version of symbol iwl_send_lq_cmd
[   34.835009] iwl4965: Unknown symbol iwl_send_lq_cmd
[   34.835030] iwl4965: Unknown symbol iwl_send_quiet
[   34.835046] iwl4965: disagrees about version of symbol iwl_rf_kill_ct_config
[   34.835047] iwl4965: Unknown symbol iwl_rf_kill_ct_config
[   34.835085] iwl4965: disagrees about version of symbol iwl_eeprom_query16
[   34.835087] iwl4965: Unknown symbol iwl_eeprom_query16
[   34.835115] iwl4965: disagrees about version of symbol iwl_rx_queue_space
[   34.835116] iwl4965: Unknown symbol iwl_rx_queue_space
[   34.835132] iwl4965: disagrees about version of symbol iwlcore_eeprom_query_addr
[   34.835133] iwl4965: Unknown symbol iwlcore_eeprom_query_addr
[   34.835164] iwl4965: disagrees about version of symbol iwl_send_add_sta
[   34.835166] iwl4965: Unknown symbol iwl_send_add_sta
[   34.835188] iwl4965: disagrees about version of symbol iwl_sensitivity_calibration
[   34.835190] iwl4965: Unknown symbol iwl_sensitivity_calibration
[   34.835207] iwl4965: disagrees about version of symbol iwl_dump_nic_error_log
[   34.835208] iwl4965: Unknown symbol iwl_dump_nic_error_log
[   34.835224] iwl4965: disagrees about version of symbol iwl_rx_agg_stop
[   34.835225] iwl4965: Unknown symbol iwl_rx_agg_stop
[   34.835243] iwl4965: disagrees about version of symbol iwl_rx_queue_free
[   34.835245] iwl4965: Unknown symbol iwl_rx_queue_free
[   34.835282] iwl4965: disagrees about version of symbol iwl_verify_ucode
[   34.835283] iwl4965: Unknown symbol iwl_verify_ucode
[   34.835311] iwl4965: disagrees about version of symbol iwl_set_tx_power
[   34.835313] iwl4965: Unknown symbol iwl_set_tx_power
[   34.835335] iwl4965: disagrees about version of symbol iwl_rx_statistics
[   34.835337] iwl4965: Unknown symbol iwl_rx_statistics
[   34.835352] iwl4965: disagrees about version of symbol iwl_setup_mac
[   34.835353] iwl4965: Unknown symbol iwl_setup_mac
[   34.835370] iwl4965: disagrees about version of symbol iwl_send_cmd
[   34.835372] iwl4965: Unknown symbol iwl_send_cmd
[   34.835396] iwl4965: disagrees about version of symbol iwl_tx_skb
[   34.835397] iwl4965: Unknown symbol iwl_tx_skb
[   34.835425] iwl4965: Unknown symbol iwl_lbm_sta_info_get
[   34.835441] iwl4965: disagrees about version of symbol iwl_tx_agg_start
[   34.835442] iwl4965: Unknown symbol iwl_tx_agg_start
[   34.835458] iwl4965: disagrees about version of symbol iwl_tx_queue_reclaim
[   34.835459] iwl4965: Unknown symbol iwl_tx_queue_reclaim
[   34.835475] iwl4965: disagrees about version of symbol iwl_eeprom_check_version
[   34.835476] iwl4965: Unknown symbol iwl_eeprom_check_version
[   34.835492] iwl4965: disagrees about version of symbol iwl_get_channel_info
[   34.835493] iwl4965: Unknown symbol iwl_get_channel_info
[   34.835543] iwl4965: disagrees about version of symbol iwl_set_hw_params
[   34.835544] iwl4965: Unknown symbol iwl_set_hw_params
[   34.835565] iwl4965: Unknown symbol iwl_dbgfs_unregister
[   34.835581] iwl4965: disagrees about version of symbol iwl_rx_replenish
[   34.835582] iwl4965: Unknown symbol iwl_rx_replenish
[   34.835598] iwl4965: disagrees about version of symbol iwl_setup_scan_deferred_work
[   34.835599] iwl4965: Unknown symbol iwl_setup_scan_deferred_work
[   34.835618] iwl4965: disagrees about version of symbol iwl_hw_nic_init
[   34.835619] iwl4965: Unknown symbol iwl_hw_nic_init
[   34.835647] iwl4965: disagrees about version of symbol iwl_hw_detect
[   34.835648] iwl4965: Unknown symbol iwl_hw_detect
[   34.835663] iwl4965: disagrees about version of symbol iwl_alloc_all
[   34.835664] iwl4965: Unknown symbol iwl_alloc_all
[   34.835680] iwl4965: disagrees about version of symbol iwl_rx_allocate
[   34.835681] iwl4965: Unknown symbol iwl_rx_allocate
[   34.835705] iwl4965: disagrees about version of symbol iwl_power_initialize
[   34.835706] iwl4965: Unknown symbol iwl_power_initialize
[   34.835729] iwl4965: disagrees about version of symbol iwl_send_cmd_sync
[   34.835730] iwl4965: Unknown symbol iwl_send_cmd_sync
[   34.835776] iwl4965: disagrees about version of symbol iwl_hwrate_to_tx_control
[   34.835777] iwl4965: Unknown symbol iwl_hwrate_to_tx_control
[   34.835798] iwl4965: Unknown symbol iwl_lbm_ieee80211_notify_mac
[   34.835827] iwl4965: Unknown symbol iwl_free_calib_results
[   34.835842] iwl4965: disagrees about version of symbol iwl_power_set_user_mode
[   34.835843] iwl4965: Unknown symbol iwl_power_set_user_mode
[   34.835859] iwl4965: disagrees about version of symbol iwl_leds_register
[   34.835860] iwl4965: Unknown symbol iwl_leds_register
[   34.835876] iwl4965: disagrees about version of symbol iwl_remove_default_wep_key
[   34.835877] iwl4965: Unknown symbol iwl_remove_default_wep_key
[   34.835899] iwl4965: disagrees about version of symbol iwl_send_cmd_pdu_async
[   34.835900] iwl4965: Unknown symbol iwl_send_cmd_pdu_async
[   34.835915] iwl4965: disagrees about version of symbol iwl_rx_queue_restock
[   34.835916] iwl4965: Unknown symbol iwl_rx_queue_restock
[   34.835932] iwl4965: disagrees about version of symbol iwl_rfkill_unregister
[   34.835933] iwl4965: Unknown symbol iwl_rfkill_unregister
[   34.835948] iwl4965: disagrees about version of symbol iwl_eeprom_query_addr
[   34.835949] iwl4965: Unknown symbol iwl_eeprom_query_addr
[   34.835965] iwl4965: disagrees about version of symbol iwl_leds_unregister
[   34.835966] iwl4965: Unknown symbol iwl_leds_unregister
[   34.835982] iwl4965: disagrees about version of symbol iwl_find_station
[   34.835984] iwl4965: Unknown symbol iwl_find_station
[   34.835999] iwl4965: disagrees about version of symbol iwl_set_dynamic_key
[   34.836000] iwl4965: Unknown symbol iwl_set_dynamic_key
[   34.836016] iwl4965: disagrees about version of symbol iwl_scan_initiate
[   34.836017] iwl4965: Unknown symbol iwl_scan_initiate
[   34.836032] iwl4965: disagrees about version of symbol iwl_sta_modify_enable_tid_tx
[   34.836034] iwl4965: Unknown symbol iwl_sta_modify_enable_tid_tx
[   34.836049] iwl4965: disagrees about version of symbol iwl_txq_check_empty
[   34.836050] iwl4965: Unknown symbol iwl_txq_check_empty
[   34.836064] iwl4965: disagrees about version of symbol iwl_reset_qos
[   34.836065] iwl4965: Unknown symbol iwl_reset_qos
[   34.836086] iwl4965: disagrees about version of symbol iwl_rx_queue_update_write_ptr
[   34.836087] iwl4965: Unknown symbol iwl_rx_queue_update_write_ptr
[   34.836104] iwl4965: disagrees about version of symbol iwl_tx_agg_stop
[   34.836105] iwl4965: Unknown symbol iwl_tx_agg_stop
[   34.836145] iwl4965: disagrees about version of symbol iwl_set_rxon_chain
[   34.836146] iwl4965: Unknown symbol iwl_set_rxon_chain
[   34.836167] iwl4965: Unknown symbol iwl_lbm_ieee80211_wake_queue
[   34.836186] iwl4965: disagrees about version of symbol iwlcore_eeprom_verify_signature
[   34.836187] iwl4965: Unknown symbol iwlcore_eeprom_verify_signature
[   34.836208] iwl4965: Unknown symbol iwl_lbm_ieee80211_free_hw
[   34.836223] iwl4965: disagrees about version of symbol iwl_rx_agg_start
[   34.836224] iwl4965: Unknown symbol iwl_rx_agg_start
[   34.836245] iwl4965: Unknown symbol iwl_lbm_ieee80211_rate_control_register
[   34.836270] iwl4965: disagrees about version of symbol iwl_dump_nic_event_log
[   34.836272] iwl4965: Unknown symbol iwl_dump_nic_event_log
[   34.836286] iwl4965: disagrees about version of symbol iwl_rxq_stop
[   34.836288] iwl4965: Unknown symbol iwl_rxq_stop
[   37.095000] Registered led device: iwl-phy0:radio
[   37.095020] Registered led device: iwl-phy0:assoc
[   37.095039] Registered led device: iwl-phy0:RX
[   37.095050] Registered led device: iwl-phy0:TX
[   37.283117] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.340591] wlan0: authenticate with AP 00:04:ed:42:06:7f
[   37.493807] wlan0: authenticate with AP 00:04:ed:42:06:7f
[   37.693474] wlan0: authenticate with AP 00:04:ed:42:06:7f
[   37.893144] wlan0: authentication with AP 00:04:ed:42:06:7f timed out

```

$ modinfo iwlagn
```

filename:       /lib/modules/2.6.24-25-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5000-1.ucode
srcversion:     76E2D7600FC00AE20CDFA41
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.24-25-generic SMP mod_unload 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```


$ modinfo iwl4965
```

filename:       /lib/modules/2.6.24-25-generic/updates/iwl4965.ko
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        2.3.5kds
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2-lbm.ucode
srcversion:     C71ED6A78005BE8FA7AA168
alias:          pci:v00008086d0000423Asv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,lbm-iwl-mac80211,lbm-iwl-cfg80211
vermagic:       2.6.24-25-generic SMP mod_unload 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)

```


$ sudo iwlist scan
```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:42:06:7F
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=99/100  Signal level:-23 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 54 Mb/s; 9 Mb/s; 18 Mb/s
                              36 Mb/s; 48 Mb/s
                    Extra:tsf=000000885484d18b
                    Extra: Last beacon: 1736ms ago
          Cell 02 - Address: 00:04:ED:42:06:7F
                    ESSID:"uplink"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=99/100  Signal level:-22 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 54 Mb/s; 9 Mb/s; 18 Mb/s
                              36 Mb/s; 48 Mb/s
                    Extra:tsf=000000885484baff
                    Extra: Last beacon: 1744ms ago

```

---

### Post by pytheas22 on 2009-10-25
glee: the symbol disagreement stuff shouldn't actually matter, because it looks like it only concerns iwl4965, not iwlagn, which is the module driving your card.  Your card appears to be up and functioning properly under iwlagn.

So I suspect this is simply an issue with the method you're using to negotiate the connection, not a driver problem.  What are you using to connect?  You might have better luck if you tried wicd instead of NetworkManager.  You can install wicd in Hardy by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Does this work better?  If not, are you sure you're within decent range of your router and there's not too much interference from other devices, etc.?

---

### Post by glee on 2009-10-28
Hi Pytheas, Thanks for the reply and the link to wicd. I have installed wicd but have not solved the problem. 

Wicd itself does not seem to allow me to add my wireless network, which leads me to suspect that things are still not quite as they should be at some deeper level in the networking config. I know that my wireless router is configured correctly because I can connect to it with several other devices (mobile phone, squeezebox), just not the laptop. 

Is it possible for me to remove (or reduce) the unknown symbol errors reported by dmesg by changing options in config.mk, or do these arise because of the older kernel? This might help me focus on the root problem instead of being distracted by (apparently unimportant) error messages.

Is there any other information I can provide which would help diagnose the issue?

Again, any insight appreciated.

---

### Post by pytheas22 on 2009-10-28
glee: what do you mean when you say wicd does not allow you to add your wireless network?  Are you unable to see any wireless networks listed in wicd's interface?  If so, go to wicd's preferences and make sure the wireless interface is set to 'wlan0', then try rescanning.  This may help.  You can clearly see wireless networks when you type 'iwlist scan', so if wicd is not seeing them, it's a problem with wicd, not your wireless driver.

As for reducing the error messages, maybe editing the source code would help, but I'm not sure; I don't know how to program.  But I also still don't think that the unknown symbol errors about iwl4965 matter.  If you want to hide them from your dmesg output, you could just type:
```

dmesg | grep -v iwl4956
```

But other than that I really don't think you should worry about them.

Also, what's the name of the network you're trying to connect to?  With that information, I can give you the commands to try connecting manually from the command line.

---

### Post by glee on 2009-10-28
Things that confuse me about this situation (taken from my initial post):

1. lspci reports 

```
04:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]

```

2. lshw reports the logical name of the wireless card as wmaster0, while iwlist scan reports it as wlan0

3. last few lines of dmesg suggest wlan0 authentication timeout

4. iwlist scan (Cell 02) shows wlan0 as having information regarding the correct, but not broadcast, ESSID "uplink". I am unsure where this has come from. I guess I must have specified it during a previous attempt to configure wireless networking through the default Gnome interface, unless this is a security hole? 

5. WICD reports "no wireless networks found" on startup. I have tried re-scanning using both wmaster0 and wlan0. Attempts to "find hidden networks" using the hidden ESSID produce the same message.

All comments welcome.

---

### Post by pytheas22 on 2009-10-29
> **glee said:**
> Things that confuse me about this situation (taken from my initial post):

1. lspci reports 

```
04:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4235]

```



This isn't anything to worry about.  "Unknown device" appears in lspci a lot, especially with newer wireless cards.
> 
2. lshw reports the logical name of the wireless card as wmaster0, while iwlist scan reports it as wlan0

This is the way it's supposed to work.  wlan0 is a virtual interface based on wmaster0.  There's a longer explanation that I'm happy to give if you want it, but the short of it is that this is not a problem.
> 
3. last few lines of dmesg suggest wlan0 authentication timeout

That means there's a problem negotiating the connection.  This rarely represents a problem with the wireless driver; more often it has to do with the wireless client not working correctly (or the router being too far away but I assume that's not the case).
> 
4. iwlist scan (Cell 02) shows wlan0 as having information regarding the correct, but not broadcast, ESSID "uplink". I am unsure where this has come from. I guess I must have specified it during a previous attempt to configure wireless networking through the default Gnome interface, unless this is a security hole?

Hidden ESSIDs aren't really very well hidden; they still come up sometimes in scans.

Are you trying to connect to this hidden network, or is it just one that's in range?  If you're trying to connect to a hidden network, that could be the problem here.  Can you connect if you broadcast the ESSID?  That would at least let us know whether the problem is the fact that it's hidden, or something else.
> 
5. WICD reports "no wireless networks found" on startup. I have tried re-scanning using both wmaster0 and wlan0. Attempts to "find hidden networks" using the hidden ESSID produce the same message.

Not sure why it's doing that, if you're positive the wireless interface is specified as wlan0 in the wicd settings (not wmaster0), and "sudo iwlist scan" consistently shows networks (don't just type "iwlist scan"; you need the sudo or it shows you networks in the cache, rather than actually performing a new scan).

Also, is there any reason you're still on Ubuntu 8.04?  As of today, that puts you three releases behind :)  There have been huge improvements to the wireless infrastructure since 8.04 and there's a good chance everything would "just work" in a more recent release.

---

### Post by glee on 2009-10-29
pytheas: all very interesting, thank you.

On 8.04 because I run a server on Hardy and decided to stick with that for the laptop, aiming to roll up at 10.04. The idea of "easier" admin running a common OS is starting to show it's weakness here :-) I may be swayed to take the laptop to 9.10 if the wireless thing doesn't resolve itself soon... BUT, it's a work machine, with a great deal of config gone into getting tools "just so" and there is some inertia to overcome in that regard before contemplating a rebuild - it would take days to get the machine productive again, and finding a window where that is feasible is not easy - I would like to explore the options under 8.04 to a reasonable extent before taking that path.

So...

I turned ESSID broadcast on, and WICD now detects my wireless network, which is a step in the right direction. 

It seems to take an inordinately long time (~1 minute) "validating authentication", and eventually reports "Connection failed: could not contact wireless access point".

I turned wireless security off temporarily and tried connecting without authentication, but received the same message.

tail /var/log/wicd/wicd.log

```

2009/10/29 17:56:57 :: Connecting to wireless network uplink
2009/10/29 17:56:58 :: Putting interface down
2009/10/29 17:57:00 :: Releasing DHCP leases...
2009/10/29 17:57:00 :: Setting false IP...
2009/10/29 17:57:00 :: Stopping wpa_supplicant
2009/10/29 17:57:00 :: Flushing the routing table...
2009/10/29 17:57:00 :: Putting interface up...
2009/10/29 17:57:00 :: Attempting to authenticate...
2009/10/29 17:57:03 :: wpa_supplicant rescan forced...
2009/10/29 17:57:41 :: wpa_supplicant authentication may have failed.
2009/10/29 17:57:41 :: Setting static IP : 192.168.1.101
2009/10/29 17:57:41 :: Setting default gateway : 192.168.1.254
2009/10/29 17:57:41 :: Verifying AP association
2009/10/29 17:57:44 :: Connection Failed: Failed to ping the access point!
2009/10/29 17:57:44 :: exiting connection thread
2009/10/29 17:57:44 :: Sending connection attempt result association_failed

```


Cheers.

---

### Post by pytheas22 on 2009-10-29
> 
On 8.04 because I run a server on Hardy and decided to stick with that for the laptop, aiming to roll up at 10.04. The idea of "easier" admin running a common OS is starting to show it's weakness here I may be swayed to take the laptop to 9.10 if the wireless thing doesn't resolve itself soon... BUT, it's a work machine, with a great deal of config gone into getting tools "just so" and there is some inertia to overcome in that regard before contemplating a rebuild - it would take days to get the machine productive again, and finding a window where that is feasible is not easy - I would like to explore the options under 8.04 to a reasonable extent before taking that path.

That makes sense.  I won't bother you to upgrade to a more recent release since you have a valid reason for being on 8.04.

From the wicd log, it looks like wicd thinks you need a static IP address with the network "uplink".  Did you tell it that?  If you're trying to use a static IP, that adds another variable to the equation that could be throwing things off.  Did you set the static IP in wicd or somewhere else?  What is contents of your /etc/network/interfaces file?

Is there any way you could try to connecting to a normal wireless network that broadcasts its ESSID and serves dynamic IP addresses via dhcp?  That would at least confirm that your computer is capable of connecting to a wireless network, and that it's just the oddities of this particular network that are posing a difficulty.

---

### Post by glee on 2009-10-30
Pytheas, 

I downloaded 9.10 today and ran the CD trial on the laptop. As you predicted, wireless networking straight out of the box. (I am in fact writing this email using wireless under that setup). 

I think that settles it. The issues under 8.04 aren't looking easy to debug, so an upgrade appears to be the path of least resistance. It's not ideal, but it will work.

I really do appreciate the help that you put in getting me to this point.

Thanks again.

---

### Post by pytheas22 on 2009-10-31
glee: glad you got it working.

---

