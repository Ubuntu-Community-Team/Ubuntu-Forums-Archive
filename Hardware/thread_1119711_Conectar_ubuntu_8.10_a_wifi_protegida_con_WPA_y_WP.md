---
title: "Conectar ubuntu 8.10 a wifi protegida con WPA y WPA2 Personal"
date: 2009-04-08
forum: Hardware
---

### Post by GGsalas on 2009-04-08
Hola, con mi laptop (Presario 2500) pude conectarme a varias wifi abiertas (sin contraseña). Pero ahora necesito conectarme a una WIFI protegida con  "WPA y WPA2 Personal". He probado ubuntu 8.04 y funciona, pero en Ubuntu 8.10 (el que uso) no. 

En "editar las conexiones" puedo elegir la opción "wpa y wpa2 personal", pero no conecta. Cuando hago click en la conexión que detecta, crea una nueva conexión y no me da la opción de "wpa y wpa2 personal".

Gracias.

---

### Post by Hei Ku on 2009-04-09
Podes probar con el Wifi Radar, o el Wicd, que son buenos programas para manejar la conexion de wifi.

---

### Post by GGsalas on 2009-04-11
> **Hei Ku said:**
> Podes probar con el Wifi Radar, o el Wicd, que son buenos programas para manejar la conexion de wifi.

Gracias. Sucede que ahora estoy en La Plata y no poseo conexión donde vivo, sólo puedo conectarme en la facu y en algún café que encuentre.

Probé de instalar Wicd y me pide que borre el programa de Gnome que maneja las wifi. No me animo a hacer eso porque sino me quedo sin internet :P

Es una lástima, porque debe ser un error tonto, ya que en Ubuntu 8.04 funcionaba bién.

Saludos

---

### Post by Hei Ku on 2009-04-11
El Wicd te pide desinstalar el networkmanager, porque lo reemplaza.
Y no te quedas sin internet, porque la configuracion la pasa a manejar el wicd.

---

### Post by hictio on 2009-04-12
Es raro, en mi caso, me pasaba exactamente lo opuesto.
Con 8.04 no me podía conectar, pero desde que me pasé a 8.10 no tuve más problemas.
Misma laptop, misma red, mismos datos de conexión.

En 8.04 probé con wicd, etc, etc, etc, y nada funcionó.
(Si, la instalación del wicd te desinstala el Network Manager, pero después lo podés volver a instalar sin problemas, si desinstalás el wicd, claro :D )

---

### Post by GGsalas on 2009-05-24
No hay caso, instalé Wicd pero tampoco me puedo conectar. También probé con el liveCD de ubuntu 9 y Kubuntu 9 pero no conecta. Sólo puedo conectarme a redes sin protección, es decir que no requieren contraseña.

Gracias

---

### Post by guillermolisi on 2009-05-24
> **GGsalas said:**
> No hay caso, instalé Wicd pero tampoco me puedo conectar. También probé con el liveCD de ubuntu 9 y Kubuntu 9 pero no conecta. Sólo puedo conectarme a redes sin protección, es decir que no requieren contraseña.

Gracias
Y como es el contenido del /etc/network/interfaces actual ?

---

### Post by sergiom99 on 2009-05-24
Gabriel, cuando pase a Kubuntu JJ se me complico un poco y anduve buscando.
Basicamente, a mi me muestra lo mismo, solo WPA y en casa tengo WPA2+TKIP. Pero funciona igual.
Lo que vi, es que tiene algo que ver con el "anillo de claves" o algo parecido que no recuerdo el nombre ahora pero que trae Gnome. Si el network manager puede escribir la contraseña en el Key-ring, se conecta sin problemas. Sino puede accederlo, no se conecta.
(yo siempre busco en googlubuntu.com que busca en los foros y demas recursos de Ubuntu. Pegale una busqueda por ahi)

---

### Post by GGsalas on 2009-05-24
> **guillermolisi said:**
> Y como es el contenido del /etc/network/interfaces actual ?

Guillermo, me acabo de fijar y dice lo siguiente:
```

auto lo
iface lo inet loopback
```

Aviso que ahora estoy conectado en un café que tiene WIFI sin protección.

---

### Post by GGsalas on 2009-05-24
> **sergiom99 said:**
> 
Lo que vi, es que tiene algo que ver con el "anillo de claves" o algo parecido que no recuerdo el nombre ahora pero que trae Gnome. Si el network manager puede escribir la contraseña en el Key-ring, se conecta sin problemas. Sino puede accederlo, no se conecta.

Sergio, en algún momemnto no recuerdo que prueba hice y me pareció lo mismo. Sucede que estoy realmente perdido, a pesar de haber buscado bastante en internet. Igual ahora estoy usando Googlubuntu ;)

---

### Post by guillermolisi on 2009-05-24
> **GGsalas said:**
> Guillermo, me acabo de fijar y dice lo siguiente:
```

auto lo
iface lo inet loopback
```Aviso que ahora estoy conectado en un café que tiene WIFI sin protección.
O sea que estas usando un administrador de redes tipo NM, Wicd o similar ?
Porque si no es asi, me llama mucho la atencion que solamente tengas declarada la interface de localhost loopback.

---

### Post by GGsalas on 2009-05-24
> **guillermolisi said:**
> O sea que estas usando un administrador de redes tipo NM, Wicd o similar ?
Porque si no es asi, me llama mucho la atencion que solamente tengas declarada la interface de localhost loopback.

Antes usé el programa de gnome para conectarme, ahora instalé Wicd, que es el que actualmente estoy usando. 

Hoy probé con el liveCD de ubuntu 9 y kubuntu 9 y tampoco pude.

---

### Post by GGsalas on 2009-05-27
Disculpas. He encontrado en muchos lugares problemas similares pero ninguna solución, o al menos ninguna que pueda entender, sólo pude instalar Wicd y sigo sin poder conectarme (mi computadora es compaq Presario 2500).

Hice una nueva prueba: para una misma conexión para la cual no me puedo conectar, desde otra computadora con Ubuntu 8.04 y Ubuntu 9.04 (laptop Dell) si pude.

Es evidente que el problema no es de los programas sino de alguna configuración de mi máquina o algo relacionado con mi hardware ¿podrá ser?

Gracias

---

### Post by Mister X on 2009-05-27
Yo me pude conectar a una WPA2 en 8.10 siguiendo el siguiente post:


[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

cualquier cosa preguntá

---

### Post by GGsalas on 2009-05-27
> **Mister X said:**
> Yo me pude conectar a una WPA2 en 8.10 siguiendo el siguiente post:


[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

cualquier cosa preguntá

Gracias, pero los pasos que indica no sólo son muy complejos, sino que a pesar que necesito conectarme con wifi protegidas, en este momento no puedo arriesgarme a equivocarme y perder la posibilidad de conectarme a wifi sin protección.

Estabe viendo que en [esta consulta en Launchpad]("https://answers.launchpad.net/ubuntu/+question/47474") se describe exáctamente mi problema pero no se llega a ninguna solución :P

---

### Post by GGsalas on 2009-05-28
Creo que el problema es la incompatibiidad de la targeta de wifi d mi computadora con las claves WPA (o al menos eso es lo que entendí)

Al escribir ```
$ lspci
``` en la consola aparece esto:
```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
gabi@gabi-laptop:~$ 
gabi@gabi-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

Busque en internet por mi targeta de wifi que creo que es esta ( Intersil Corporation Prism 2.5 Wavelan chipset) y encontré en [este BUG en Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243838")

---

