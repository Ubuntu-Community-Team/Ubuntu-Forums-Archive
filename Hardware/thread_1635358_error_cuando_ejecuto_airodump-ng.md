---
title: "error cuando ejecuto airodump-ng"
date: 2010-12-01
forum: Hardware
---

### Post by cristiaan3003 on 2010-12-01
cuando ejecuto el comando tengo este problemas que detalloa abajo. que me recomeindan que haga en kubuntu 10.10?? 
root@CvzKubuntu:/home/cristiaan3003# airmon-ng start eth1


Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

root@CvzKubuntu:/home/cristiaan3003# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

root@CvzKubuntu:/home/cristiaan3003# 

IMPORTANTE : no pongo mon0 en airodumpo xq en ep paso que coloco irmon-ng start eth1 no me crea mon0. les coloco la salida de ifconfig despues de ejecutar el start para que vean:
root@CvzKubuntu:/home/cristiaan3003# ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:11:22:33:44:55  
          ACTIVO DIFUSIÓN  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:45 Dirección base: 0xc000 

eth1      Link encap:Ethernet  direcciónHW 1c:65:95:20:5a:40  
          Direc. inet:192.168.1.101  Difus.:255.255.255.255  Másc:255.255.255.0
          ACTIVO DIFUSIÓN FUNCIONANDO  MTU:1500  Métrica:1
          Paquetes RX:1292 errores:0 perdidos:0 overruns:0 frame:3881
          Paquetes TX:1365 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1213692 (1.2 MB)  TX bytes:272014 (272.0 KB)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          ACTIVO DEPURACIÓN BUCLE FUNCIONANDO PROMISCUO ALLMULTI  MTU:16436  Métrica:1
          Paquetes RX:175 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:175 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:14312 (14.3 KB)  TX bytes:14312 (14.3 KB)

lspci la reconoce como :
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

para instalarla segui los pasos que decia en el siguiente link : [http://www.taringa.net/posts/linux/8076795/_Ubuntu_-Bradcom-BCM4313-y-Aircrack-_funciona_.html](http://www.taringa.net/posts/linux/8076795/_Ubuntu_-Bradcom-BCM4313-y-Aircrack-_funciona_.html)l

---

### Post by jorgito on 2010-12-13
Hola, 

En lugar de usar airmon-ng start .....

Usa 

iw dev wlan0 interface add mon0 type monitor

Cambiando o eth1 en lugar de wlan0, como parece ser tu caso.

Saludos,

---

