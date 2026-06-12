---
title: "intalacion de drivers para wifi usb"
date: 2010-07-20
forum: Hardware
---

### Post by andrestester on 2010-07-20
hola que tal solo para preguntar como puedo intalar controladores para una usb de wifi los controladores los tengo en disco?, cuales seran los pasos para instalar?
 
 
salu2 gracias por su ayuda.

---

### Post by Patriciologico on 2010-07-21
Andres,

 Empieza por contar que tarjeta es, cual es su chipset, que drivers son los que tienes, ayúdanos para ayudarte.

Saludos.

---

### Post by andrestester on 2010-07-22
ok gracias...
 
 
esta es :
 
[IMG]http://www.zonaimagen.es/files/31199.jpg[/IMG]
 
 
 
 
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Complies with IEEE 802.11n(draft 2.0), IEEE 802.11g, IEEE 802.11b standards[/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] 150Mbps RX PHY Rate, 150Mbps TX PHY Rate[/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] STBC Support for Extended Range [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] 20MHz/40MHz bandwidth [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] WEP 64/128, WPA/WPA2[FONT=&#23435]&#12289;[/FONT]WPA-PSK/WPA2-PSK Support [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Multiple BSSID Support [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Supports Roaming technology[/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Cisco CCX V1.0 V2.0 V3.0 Compliance [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Low Power with Advanced Power Management [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] Supports Windows 98/SE/ME,Windows 2000/XP/VISTA/ CE,[COLOR=lime]** Linux,**[/COLOR] Mac [/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=&#23435]·[/FONT] With Detachable external Antenna[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]segun soporta linux?[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]salu2.[/SIZE][/FONT]

---

### Post by Patriciologico on 2010-07-22
Ok, las caracteristicas que nos das no sirven de mucho. Sigue lo que recomienda Carlos C en **[Mi tarjeta wifi no es reconocida por Ubuntu ¿Qué hago?]("http://ubuntuforums.org/showthread.php?t=1410957")** 

Ademas, muentranos las siguientes salidas a estos comandos, con toda esa informacion recopilada podemos hacer mas.

```
lsusb
```

```
ifconfig
```

```
iwconfig
```

---

### Post by andrestester on 2010-07-23
ok trabajando en esto mas tarde subo datos.
 
salu2.
 
y gracias por responder....

---

### Post by Carlos C on 2010-07-25
Movido a Hardware.

---

### Post by andrestester on 2010-07-31
gracias por su ayuda, segui los consejos, de patrocio de las ligas que puso en su respuesta y ya quedo listos, 1000 de gracias por su ayuda.
 
ubuntu trabjando al 100% solo falta aprenden mas para no tener miedo al cambio jejejeje.
 
salu2....

---

### Post by andrestester on 2010-08-15
esta es la inf. que muestra esta es otra usb wifi .

y que mas tengo que hacer..:confused:

lsusb:

Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp.  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:02:a5:f1:73:e0   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:4368 (4.3 KB)  TX bytes:4368 (4.3 KB) 
 
wlan1     Link encap:Ethernet  HWaddr 00:a1:b0:90:3d:b0   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

iwconfig:

         lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan1     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 


salu2....

---

### Post by themasterdark on 2010-08-15
Esa otra inalambrica usb ya esta lista para usarse fijate 

wlan1 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn 

Saludos

---

### Post by andrestester on 2010-08-15
ok pero como la puedo prender???

porque no me la reconoce el sistema.


salu2.

pd: gracias por respoder.

---

### Post by themasterdark on 2010-08-15
Es que de hecho si te la reconoce porque te esta mostrando incluso que esta en modo managed y que no esta conectada a ninguna red.

Realiza en un terminal un:

```
iwlist wlan1 scanning
```

y si te muestras redes inalambricas disponibles mira ete link 

[http://bargues.info/?p=24](http://bargues.info/?p=24)

hay figura como conectarte de redes inalambricas desde terminal para que si logras conectarte estemos seguros que trabaja bien con el sistema saludos

PD: en el link usan eth1 la tuya es wlan1 segun tu ifconfig 

Saludos.!

---

### Post by andrestester on 2010-08-16
ok la probare esta tarde. gracias por responder, lo que me sorprende es que la anterior tarjeta usb que tenia no ocupe nada solo la conecte y me pidio el password y listo y esta no la detecta.
 
salu2. y gracias por su ayuda. pondre resultados.

---

