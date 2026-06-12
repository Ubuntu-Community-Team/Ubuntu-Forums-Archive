---
title: "Conectado a una red WiFi no carga paginas"
date: 2009-09-04
forum: Hardware
---

### Post by akiestudio on 2009-09-04
Despues de formatear, instalar el wcid , sigue teniendo el mismo proble, si se abre el hilo anterior o se sigue en este.

Pues eso que sigue conectado pero que no carga las paginas, tengo que desconectarme y conectarme....
Temperatura da unos 43 grados

Muchas gracias a todos

---

### Post by dollarmenunaire on 2009-09-04
¿Qué problemas tiene?

---

### Post by dollarmenunaire on 2009-09-04
¿Qué marca de tarjeta es?

comprobar la potencia de la señal

---

### Post by sergiom99 on 2009-09-04
agrega estas lineas al archivo /etc/resolv.conf a ver que pasa
> nameserver 208.67.222.222
nameserver 208.67.220.220


Despues reinicia el servicio de red:
```
$ sudo /etc/init.d/**networking** restart
```

---

### Post by guillermolisi on 2009-09-04
> **akiestudio said:**
> Despues de formatear, instalar el wcid , sigue teniendo el mismo proble, si se abre el hilo anterior o se sigue en este.

Pues eso que sigue conectado pero que no carga las paginas, tengo que desconectarme y conectarme....
Temperatura da unos 43 grados

Muchas gracias a todos
Si queres una ayuda adecuada, rapida y precisa, es necesario que seas algo mas descriptivo en tus comentarios.

Los demas carecen de toda la informacion que tenes respecto del problema.

---

### Post by akiestudio on 2009-09-04
La actualizacion del Kernel no soluciono el problema tampoco, necesito desconectarme y volverme a conectar para tener internte cada 5 minutos

Problema principal que se me desconecta internet cada 5 Minutos, el post anterior se cerro ,porque j**i eubuntu y tuve que formatear y despues de instalarlo de nuevo sigue este problema.
Soy nuevo con linux y creo que aprendere a base de c*****a muchas veces..

Una duda mas cuando instalas ubuntu cuantos kernel tienes, ¿ porque a mi me salen 4 , dos parejas iguales? y al actualizar el kernel creo que ya tengo otros 2 mas
es eso normal

Cuando hago 

sudo /etc/init.d/network restart  Comando no encontrado eso es lo que dice:
 
y con :
fran@fran:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Ahi pone la tarjeta de red

---

### Post by guillermolisi on 2009-09-04
> **akiestudio said:**
> La actualizacion del Kernel no soluciono el problema tampoco, necesito desconectarme y volverme a conectar para tener internte cada 5 minutos

Problema principal que se me desconecta internet cada 5 Minutos, el post anterior se cerro ,porque j**i eubuntu y tuve que formatear y despues de instalarlo de nuevo sigue este problema.
Soy nuevo con linux y creo que aprendere a base de c*****a muchas veces..

Una duda mas cuando instalas ubuntu cuantos kernel tienes, ¿ porque a mi me salen 4 , dos parejas iguales? y al actualizar el kernel creo que ya tengo otros 2 mas
es eso normal

Cuando hago 

sudo /etc/init.d/network restart  Comando no encontrado eso es lo que dice:
 
y con :
fran@fran:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Ahi pone la tarjeta de red

Por favor, mantenete dentro del topico del thread.

Si necesitas abrir otro por el tema de la cantidad de kernels hacelo despues de haber buscado en el foro si esa consulta ya fue respondida.

Cuida tu lenguaje. El foro es internacional y existen reglas que seguir para todo el mundo por igual. Tu participacion en el mismo implica la plena aceptacion de las mismas y se da por sentado que las conoces, con lo cual utilizar lenguaje inapropiado es una clara transgresion al CoC (Code of Conduct).

Mas informacion en los sticky threads de la pagina principal de foro argentino [http://ubuntuforums.org/forumdisplay.php?f=189](http://ubuntuforums.org/forumdisplay.php?f=189)

---

### Post by sergiom99 on 2009-09-04
1) Buscaste en el foro por tu placa wifi a ver que sale? Yo encontre un monton de cosas:
[http://ubuntuforums.org/search.php?searchid=63779597](http://ubuntuforums.org/search.php?searchid=63779597)  (**intel 3945ABG**)

2) Instalate FUCH ([http://ubuntuforums.org/showthread.php?t=1211568](http://ubuntuforums.org/showthread.php?t=1211568)) y postea aca el resultado de 'Redes' y 'Wifi'

---

### Post by sergiom99 on 2009-09-04
> **akiestudio said:**
> 
Cuando hago 

sudo /etc/init.d/network restart  Comando no encontrado eso es lo que dice
My fault. Lo correcto es 
```
 sudo /etc/init.d/networking restart
```

*De cualquier manera, cuando estas tipeando en la consola podes apretar la tecla TAB y te va autocompletando. Si a /network le apretas TAB te va a agregar el ing faltante.*

---

### Post by akiestudio on 2009-09-05
Muchas gracias por todo , procurare modificar mi lenguaje ,lo siento, y esoy buscando por todos los lados para intentar solucionarlo , pero no encuentro nada muy en claro ,seguire haciendolo , aqui te pego los resultados que me da.
Gracias
```

Escritorio:    GNOME

```


```

$ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:03:0d:87:27:df  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:30 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:1c:bf:5d:77:86  
          inet dirección:192.168.1.135  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21c:bfff:fe5d:7786/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:6541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6777 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:6372163 (6.3 MB)  TX bytes:1457860 (1.4 MB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1C-BF-5D-77-86-37-38-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```


```

$dmesg |grep eth
[    1.373417] Driver 'sd' needs updating - please use bus_type methods
[    1.373424] Driver 'sr' needs updating - please use bus_type methods
[    3.220119] eth0: RTL8101e at 0xf7c7c000, 00:03:0d:87:27:df, XID 34200000 IRQ 30
[   41.654176] r8169: eth0: link down
[   41.654346] ADDRCONF(NETDEV_UP): eth0: link is not ready

```


```

$cat /etc/network/interfaces
auto lo
iface lo inet loopback


```


```

$cat /etc/resolv.conf
nameserver 87.216.1.65
nameserver 87.216.1.66
nameserver 208.67.222.222
nameserver 208.67.220.220 

```


```

Escritorio:    GNOME

```


```

$iwconfig
wlan0     IEEE 802.11abg  ESSID:"Jazztel 2009"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1A:2B:47:7C:39   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:3532-3032-35   Security mode:open
          Power Management:off
          Link Quality=78/100  Signal level:-56 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


```

$cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   78.  -56   -127.       0      0      0      0      0        0

```


```

$lsmod |grep wlan && lsmod |grep ath && lsmod |grep ra

```


```

$cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

---

### Post by akiestudio on 2009-09-07
No encuentro la solucion por ningun lado ,nadie sabe como solucionarlo, leo muchos post , pero ninguno explica claramente como solucionarlo ... Gracias

---

