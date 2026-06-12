---
title: "wlanX Failed to read scan data : Resource temporarily unavailable"
date: 2011-01-17
forum: Hardware
---

### Post by ramiro_md on 2011-01-17
Buenas, hace cuanto que no entro al foro. Pero ahora me es imprescindible.
Resulta que tengo un servidor casero con Ubuntu Server Maverick, por ahora esta conectado a internet mediante cable y va joya.
El otro día mi viejo compró un adaptador wireless usb TP-Link WN722N, con chipset Atheros. Por suerte el driver y el firmware del dispositivo estaban por defecto en el sistema y lo instalé sin más problemas.
El tema es que hasta anoche podía hacer un:
```
# iwlist wlan0 scan
```
sin ningún tipo de problema.
Hoy día, el tema cambió para peor.
Cuando ejecuto nuevamente **iwlist wlan0 scan** me devuelve lo siguiente (luego de estar un ratito pensando):
> wlan0     Failed to read scan data : Resource temporarily unavailable
Por suerte el sistema me reconoce el adaptador:
> 
rama@server:~$ sudo iwconfig
[sudo] password for rama: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off

Y con **ifconfig wlan0 up**, supuestamente levanta.
En google lo único claro (para mi intelecto) que encontré fue [esto]("http://sigloxxi.fcie.uam.es/maquinaciones/solucionado-iwl3945-en-ubuntu-9.04-no-muestra-las-redes"). Obviamente reemplazando el driver del artículo por el mio, y no ha funcionado.
Sin más para comentar, agradezco cualquier tipo de ayuda/sugerencia para resolver el inconveniente.

---

### Post by ramiro_md on 2011-01-17
Por motivos que no van al caso, tuve que formatear y reinstalar...y anduvo de nuevo.

---

