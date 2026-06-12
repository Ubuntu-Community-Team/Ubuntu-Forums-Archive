---
title: "TP-Link usb wireless no funciona"
date: 2010-09-07
forum: Hardware
---

### Post by josecuervo86 on 2010-09-07
Hola gente! A ver si me dan una mano con este placa usb que me esta volviendo loco =). El tema es asi, me compre una placa wireless usb TP-LINK modelo TL-WN721N que tiene chip Atheros 9271. Hasta ahi todo bien. Con este tutorial [0] pude lograr que al menos me reconozca que es una placa wireless, bajandome los ultimos modulos y el firmware desde aca [1]. El problema es que hasta ahi llega. O sea, paso lo que me tira con los siguientes comandos:

**lsusb**
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 0cf3:9271 Atheros Communications, Inc.** 
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

[B]wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off[/B]

```

*Agrego el resultado de:

**lshw -C network**
```
josecuervo86@tutuka:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:90:7d:d7:cb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:d800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       bus info: firewire@1
       logical name: wlan0
       serial: 00:25:86:e6:5f:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=2.6.32-24-generic firmware=N/A multicast=yes wireless=IEEE 802.11bgn

```

La placa esta reconocida, ya le hice modprobe al modulo ath9k_htc que es el que la deberia hacer andar pero no pasa nada. No se si me estoy perdiendo de algo, por eso recurro a ustedes!

Cualquier ayuda es bienvenida! Saludos!!

[0] [http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/](http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/)
[1] [http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)

---

### Post by josecuervo86 on 2010-09-07
Bueno gente, marco como SOLVED!!!! perdón por postear sin revisar todo, pero lo que paso es que me habia olvidado lo mas básico, habilitar el network-manager que lo tenia desabilitado.
De ahora en mas paso a recomendar esta placa, es bastante sencillo de hacer andar (si tenes el network-manager habilitado!!)

Saludos!!

---

