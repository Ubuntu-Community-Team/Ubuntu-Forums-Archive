---
title: "lost wlan0..."
date: 2009-08-19
forum: Hardware
---

### Post by fafarafa on 2009-08-19
Hi,

I've tried to get aircrack-ng showing Chipset different then "unknown"
I have a Intel 4965AGN 802.11abgn card.

what I did, is exactly:
cd ~
 tar xjf compat-wireless-2.6.30.tar.bz2
 cd compat-wireless-2.6.30
 wget [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
 patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 wget [http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch](http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch)
 patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 make -j4
 make unload
 make install
 echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options
 make load

it made my wlan0 go missing...

tried to fix it just (as root) in a newly extractec compat-wireless-2.6.30 folder:

make
make install
make unload

lspci gives me:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
################
iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
################
ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
###############
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
###############

Can anyone help me please??

---

### Post by w_1_n_d on 2009-08-19
can you connect to a wireless connection?:-k:-k

---

### Post by fafarafa on 2009-08-20
No, I cant. Because only eth0 connection remained. When I click on Network Manager icon, I dont see any wifi connections available...

---

### Post by w_1_n_d on 2009-08-20
try installing wireless compact?? mabye that will reinstall your wireless driver??

---

### Post by fafarafa on 2009-08-20
that was exactly what did cause the error in the first place...

I've installed "compat-wireless-2.6.30"
with commands:
make
make install
make unload
reboot

but before that I tried to do the same thing but with aircrack patches...

---

### Post by w_1_n_d on 2009-08-20
Maybe if you install ndiswrapper you can load your driver again??:guitar:

---

### Post by fafarafa on 2009-08-20
I've downloaded the XP drivers for 4965AGN, unziped it, found the

netw5x64.inf file and used ndiswrapper to install it

unfortunately it did not work, and it is listed as:
###################################
netw5x64 : invalid driver!
###################################

Ps. I have a 64Bit Ubuntu installed

going to look for a different driver...

---

### Post by w_1_n_d on 2009-08-20
What driver was loaded with ubuntu??

---

### Post by fafarafa on 2009-08-20
On my search I got to this page:

[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

don't know what to do with this knowledge though ;)

---

### Post by fafarafa on 2009-08-20
root@ .../compat-wireless-2009-08-19# make install
 
Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
updates/lib80211.ko
updates/adm8211.ko
updates/at76c50x-usb.ko
updates/ath5k.ko
updates/ath9k.ko
updates/b43.ko
updates/b43legacy.ko
updates/b44.ko
updates/cdc_ether.ko
updates/eeprom_93cx6.ko
updates/ipw2100.ko
updates/ipw2200.ko
updates/iwl3945.ko
updates/iwlagn.ko
updates/iwlcore.ko
updates/lib80211_crypt_ccmp.ko
updates/lib80211_crypt_tkip.ko
updates/lib80211_crypt_wep.ko
updates/libertas.ko
updates/libertas_cs.ko
updates/libertas_sdio.ko
updates/libertas_tf.ko
updates/libertas_tf_usb.ko
updates/libipw.ko
updates/mac80211_hwsim.ko
updates/mwl8k.ko
updates/p54common.ko
updates/p54pci.ko
updates/p54usb.ko
updates/rndis_host.ko
updates/rndis_wlan.ko
updates/rt2400pci.ko
updates/rt2500pci.ko
updates/rt2500usb.ko
updates/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/rt61pci.ko
updates/rt73usb.ko
updates/rtl8180.ko
updates/rtl8187.ko
updates/ssb.ko
updates/usb8xxx.ko
updates/usbnet.ko
updates/zd1211rw.ko

make -C /lib/modules/2.6.28-15-generic/build M=/home/lorcan/Desktop/compat-wireless-2009-08-19 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/usb/cdc_ether.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/usb/rndis_host.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/usb/usbnet.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/adm8211.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ath/ath.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/b43/b43.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/mwl8k.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/wl12xx/wl1251.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/wl12xx/wl1251_sdio.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/wl12xx/wl1251_spi.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/wl12xx/wl1271.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/drivers/ssb/ssb.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/mac80211/mac80211.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/rfkill/rfkill_backport.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/wireless/cfg80211.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/wireless/lib80211.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/lorcan/Desktop/compat-wireless-2009-08-19/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.28-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
volatile/ath_pci.ko
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/ath5k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/b43.ko
updates/b43legacy.ko
updates/b44.ko
updates/drivers/net/usb/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/ipw2100.ko
updates/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/iwl3945.ko
updates/iwlagn.ko
updates/drivers/net/wireless/iwlwifi/iwlcore.ko
updates/lib80211_crypt_ccmp.ko
updates/lib80211_crypt_tkip.ko
updates/lib80211_crypt_wep.ko
updates/libertas.ko
updates/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/rt2x00pci.ko
updates/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

then I do "make unload", "reboot" and nothing happens...

Kind of got stuck...

---

### Post by fafarafa on 2009-08-20
when I try to load the driver I get:

root@ ... /compat-wireless-2009-08-19# modprobe iwlagn
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: Error inserting led_class (/lib/modules/2.6.28-15-generic/kernel/drivers/leds/led-class.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-15-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-15-generic/updates/iwlagn.ko): Invalid module format

---

### Post by jalirious on 2009-09-06
I lost wlan0 as well.

Fixed it (well, got madwifi working that is) via-

[http://ubuntuforums.org/showthread.php?t=1256917](http://ubuntuforums.org/showthread.php?t=1256917)

Some other (earlier, probably inconsequential) faffing was to put in the scripts described in the wireless module of;

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

G'luck

---

