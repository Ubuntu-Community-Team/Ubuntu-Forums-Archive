---
title: "Como activar 2 tarjetas Ethernet?"
date: 2009-12-04
forum: Hardware
---

### Post by Brath-ga on 2009-12-04
Hola a tod@s.

Despues de buscar por los foros y no encontrar respuesta adecuada, os explico mi problema.

Tengo en el sobremesa con Ubuntu 9.10 una tarjeta de red ethernet integrada en placa, una wirelees en PCI y otra tarjeta ethernet en PCI que es con la que quiero comunicarme con el netbook en el que está instalado Ubuntu Remix 9.10

Al ejecutrar ifconfig -a, no logro ver la 2ª Ethernet!!!

xoan@pinki-fixo:~$ ifconfig -a
eth0 Link encap:Ethernet direcciónHW 00:13:8f:d0:5a:bc
Direc. inet:192.168.0.12 Difus.:192.168.0.255 Másc:255.255.255.0
Dirección inet6: fe80::213:8fff:fed0:5abc/64 Alcance:Enlace
ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST MTU:1500 Métrica:1
Paquetes RX:3531 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:3106 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:1000
Bytes RX:3778535 (3.7 MB) TX bytes:434801 (434.8 KB)
Interrupción:36 Dirección base: 0xa000

lo Link encap:Bucle local
Direc. inet:127.0.0.1 Másc:255.0.0.0
Dirección inet6: ::1/128 Alcance:Anfitrión
ACTIVO LOOPBACK FUNCIONANDO MTU:16436 Métrica:1
Paquetes RX:156 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:156 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:0
Bytes RX:14520 (14.5 KB) TX bytes:14520 (14.5 KB)

vboxnet0 Link encap:Ethernet direcciónHW 0a:00:27:00:00:00
DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:1000
Bytes RX:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet direcciónHW 00:13:f7:49:fe:fc
DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:1000
Bytes RX:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC direcciónHW 00-13-F7-49-FE-FC-00-00-00-00-00-00-00-00-00-00
[NO FLAGS] MTU:0 Métrica:1
Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:1000
Bytes RX:0 (0.0 B) TX bytes:0 (0.0 B)

Sin embargo al ejecutar lspci | grep Ethernet si la veo

xoan@pinki-fixo:~$ lspci | grep Ethernet
00:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

Por favor, indicarme que debería hacer?

---

