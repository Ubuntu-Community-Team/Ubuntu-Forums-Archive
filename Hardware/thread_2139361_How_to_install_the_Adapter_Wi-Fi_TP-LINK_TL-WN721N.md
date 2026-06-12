---
title: "How to install the Adapter Wi-Fi TP-LINK TL-WN721N (AR9271 0cf3 9271)"
date: 2013-04-26
forum: Hardware
---

### Post by PhenomX5 on 2013-04-26
Hi everyone!

Just bought a Wi-Fi Adapter TP-LINK TL-WN721N and am having trouble installing it on Ubuntu.


1) My sistem:

$ uname -a
Linux wfs 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 athlon i686 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


2) The hardware is recognized for the system:

$ lsusb
Bus 001 Device 004: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n


3) I tryed install with the procedure bellow:

$ sudo apt-get -y install build-essential linux-headers-generic linux-headers-`uname -r`

$ mkdir htc_9271
$ cd htc_9271

$ wget wireless.kernel.org/download/compat-wireless-2.6/compat-wireless.tar.bz2
$ tar -xvf compat-wireless.tar.bz2

$ cd compat*
$ sudo make
$ sudo make install
$ cd ..

$ wget wireless.kernel.org/download/htc_fw/1.3/htc_9271.fw
$ sudo cp htc_9271.fw /lib/firmware

$ sudo modprobe ath9k_htc


4)the module was installed:

$ modinfo ath9k_htc

filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     A75D155EBE2E5D10290B476
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp3904d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)


5) but didn't work, someone know what I have to do??

---

### Post by kurt18947 on 2013-04-26
Did you try just connecting without installing anything?  I have a Netgear WNA1100, it just connects, no added anything.  That may not be true of all AR9271 adapters, I only have experience with the one.  Some people find it necessary to disable hardware encryption on ath9k adapters.  I think mine performs better with hardware encryption disabled but it will connect with hardware encryption enabled.

---

### Post by PhenomX5 on 2013-04-26
Yes, I've tried. But there is no recognized network interface Wi-Fi, only the two Ethernet.

$ lsusb
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

$ ifconfig -a
eth0      Link encap:Ethernet  Endereço de HW 08:00:27:5f:68:7d
          inet end.: 192.168.56.2  Bcast:192.168.56.255  Masc:255.255.255.0
          endereço inet6: fe80::a00:27ff:fe5f:687d/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1239 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:816 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:174842 (174.8 KB) TX bytes:450455 (450.4 KB)

eth1      Link encap:Ethernet  Endereço de HW 08:00:27:c0:92:e9
          inet end.: 10.0.3.15  Bcast:10.0.3.255  Masc:255.255.255.0
          endereço inet6: fe80::a00:27ff:fec0:92e9/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1266 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:951 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:881741 (881.7 KB) TX bytes:74449 (74.4 KB)

lo        Link encap:Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:414 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:414 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:44321 (44.3 KB) TX bytes:44321 (44.3 KB)

---

