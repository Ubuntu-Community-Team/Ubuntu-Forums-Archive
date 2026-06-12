---
title: "Cual es la Mac?"
date: 2009-02-06
forum: Hardware
---

### Post by gustmarti on 2009-02-06
Hola!!! Necesito si alguien me podría indicar cual es la mac addressvde mi placa wifi, porque hay varias direcciones y no se cual es ¿eth1 o pan0?

Aca les dejo el ifconfig:


 
eth0      Link encap:Ethernet  direcciónHW 00:21:70:81:e4:dd  
          inet dirección:201.213.19.206  Difusión:201.213.19.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:576  Métrica:1
          RX packets:665638 errors:22 dropped:0 overruns:0 frame:22
          TX packets:5852 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:45762381 (45.7 MB)  TX bytes:731546 (731.5 KB)
          Interrupción:17 

eth1      Link encap:Ethernet  direcciónHW 00:23:4e:75:87:19  
          dirección inet6: fe80::223:4eff:fe75:8719/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:73
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  direcciónHW be:1d:db:2d:dc:e5  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Hei Ku on 2009-02-06
La pan0 probablemente sea bluetooth.

La eth1 debe ser la wifi.
direcciónHW 00:23:4e:75:87:19 <--- esa es la MAC address

---

### Post by sherwoodinc on 2009-02-06
El campo que tenés que mirar es "direcciónHW".
Para saber cual de las dos placas es la wireless, ejecutá
```
iwconfig
``` y posteá el resultado.

EDIT:

En realidad no postees el resultado, porque puede llegar a mostrar alguna key de tu wireless (igual creo que si es WPA no muestra nada).
La interfaz wireless es la única que no dice "no wireless extensions" cuando ejecutás el "iwconfig".

---

### Post by gustmarti on 2009-02-06
Gracias!!!! Voy a probar con esa!!!!



> **Hei Ku said:**
> La pan0 probablemente sea bluetooth.

La eth1 debe ser la wifi.
direcciónHW 00:23:4e:75:87:19 <--- esa es la MAC address

---

