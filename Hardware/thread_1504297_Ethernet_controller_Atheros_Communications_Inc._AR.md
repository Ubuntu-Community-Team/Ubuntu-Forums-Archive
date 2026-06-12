---
title: "Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)"
date: 2010-06-07
forum: Hardware
---

### Post by superope on 2010-06-07
tengo un dramon tenia una tarjeta ralink  de wifi  que no me funcionaba  en ubuntu 9.10 ni en 10.04

solo en 9.04 la cosa  es que compre  una atheros   y no  me funciona  que hago!!!!

esto es lo que me sale en los comandos 
```

priss@priss-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
``````
priss@priss-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:24:29:60:68  
          Direc. inet:192.168.1.2  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21b:24ff:fe29:6068/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1289 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1156 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1209468 (1.2 MB)  TX bytes:157097 (157.0 KB)
          Interrupción:21 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:16 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:16 errores:0 perdidos:0 o
```verruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:960 (960.0 B)  TX bytes:960 (960.0 B)

```

priss@priss-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
``````

priss@priss-laptop:~$ lspci -vnn | grep Wire
priss@priss-laptop:~$ 
```

instale el driver privativo desde controladores de harware  pero no funciona

---

### Post by Carlos C on 2010-06-08
¿Tu equipo es un notebook? Si es así, ¿la tarjeta es una USB?

Saludos.

---

