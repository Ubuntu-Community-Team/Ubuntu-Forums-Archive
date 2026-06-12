---
title: "Me quede sin red!!!"
date: 2009-05-20
forum: Hardware
---

### Post by caraPintada on 2009-05-20
Buenas amigos......
Este es mi primer post, hasta el momento habia solucionado mis problemas leyendo las soluciones de otras personas.
Paso a contar: en mi laptop tengo Ubuntu y windows xp. el hecho es que me quede si red local e internet tanto con el NIC y con la placa wifi, solo con ubuntu.  La cosa es asi, cada vez que conecto reconoce la red de, hecho me da el nombre de la misma, le asigna una ip a la interfaz por DHCP; pero a la hora de buscar otro pc, o con samba o en internet no conecta, ni con los repositorios. Como lo hizo simpre hasta hace unos dias atras.  
¡¡¡¿Qué hago?!!!
Gracias ubunteros....

---

### Post by guillermolisi on 2009-05-20
> **caraPintada said:**
> Buenas amigos......
Este es mi primer post, hasta el momento habia solucionado mis problemas leyendo las soluciones de otras personas.
Paso a contar: en mi laptop tengo Ubuntu y windows xp. el hecho es que me quede si red local e internet tanto con el NIC y con la placa wifi, solo con ubuntu.  La cosa es asi, cada vez que conecto reconoce la red de, hecho me da el nombre de la misma, le asigna una ip a la interfaz por DHCP; pero a la hora de buscar otro pc, o con samba o en internet no conecta, ni con los repositorios. Como lo hizo simpre hasta hace unos dias atras.  
¡¡¡¿Qué hago?!!!
Gracias ubunteros....
Con XP te funciona todo normalmente, red cableada y wifi ?

Hiciste alguna actualizacion recientemente de Ubuntu ?

Estas usando Network Manager ?

Con Ubuntu funciono alguna vez la red y la navegacion a traves de la misma y hacia Internet ?

---

### Post by caraPintada on 2009-05-20
Si guillermolisi, con Xp funciona barbaro, va como en windows. 
Lo unico que hice fue instalar el gestor de mquinas virtuales VirtualOSe pero no funicono par lo que queria y cuando se presento este problema lo saque.
Network manager no no uso.
Andubo siempre en red con el NIC desde la instlacion y wifi unos dias despues de haberse nstalaldo con el ndiswrapper
Por las dudas el NIC es Realtek 810... y el wifi es Atheros5006G
La lapto MSI VR-610(son una joya)
Espero haber dado buena info para aclarar el problema. Gracias por la respuesta

---

### Post by Hei Ku on 2009-05-20
Podes poner el resultado de ejecutar ifconfig en una terminal?

Tambien estaría bueno el archivo /etc/network/interfaces

---

### Post by guillermolisi on 2009-05-20
> **caraPintada said:**
> Si guillermolisi, con Xp funciona barbaro, va como en windows. 
Lo unico que hice fue instalar el gestor de mquinas virtuales VirtualOSe pero no funicono par lo que queria y cuando se presento este problema lo saque.
Network manager no no uso.
Andubo siempre en red con el NIC desde la instlacion y wifi unos dias despues de haberse nstalaldo con el ndiswrapper
Por las dudas el NIC es Realtek 810... y el wifi es Atheros5006G
La lapto MSI VR-610(son una joya)
Espero haber dado buena info para aclarar el problema. Gracias por la respuesta
Estas usando 8.10 o 9.04 actualizado al dia ?

---

### Post by caraPintada on 2009-05-20
El ifconfig devolvio esto estando conectado el the0 y el wlan0
eth10     Link encap:Ethernet  direcciónHW 00:1d:92:4d:4c:19  
          inet dirección:192.168.1.105  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21d:92ff:fe4d:4c19/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:764 (764.0 B)  TX bytes:1152 (1.1 KB)
          Interrupción:220 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:4688 (4.6 KB)  TX bytes:4688 (4.6 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:15:af:62:20:e5  
          inet dirección:192.168.1.103  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::215:afff:fe62:20e5/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2013 (2.0 KB)  TX bytes:852 (852.0 B)
          Interrupción:16 Memoria:fdff0000-fe000000 

el archivo interfaces dice

auto lo
iface lo inet loopback
auto eth0 
iface eth0 inet dhcp

yo probe poner la misma linea para wlan0 pero  sirvio de nada asi que la borre

---

### Post by caraPintada on 2009-05-20
Uso 8.10...aun no actualice

---

### Post by caraPintada on 2009-05-20
Por si sirve de algo el ping por ejemplo a 192.168.1.1 me dice operacion no pemitida

---

### Post by Hei Ku on 2009-05-20
tu interfaz aparece como eth10 en el ifconfig, pero como eth0 en el archivo interfaces.

Tira un lspci y postea el resultado, para ver que placa de red tenes.

---

### Post by hictio on 2009-05-20
Con la máquina conectada a la red, con su IP asignado por DHCP, etc, etc.
Probaste de hacer un ping hacia algo fuera de tu red?
Por ejemplo, a gmail.com, ya sea usando 'ping gmail.com' o bien su dirección IP (por ejemplo, probar contra 209.85.171.83)
Podés hacer ping a tu default gateway?
Tenés setteados servidores DNS?

---

### Post by caraPintada on 2009-05-20
Si probe pero me da el mismo mensaje de error de Operacion no permitida. Tanto con ip como con URL. De hecho comence con uno fuera de mi red. Y luego con mi getway 192.168.1.1 con el broadcast 192.168.1.255.
DNS seteados no nunca eso siempre lo resolvio solo el DHCP.
Lo extraño, por lo menos para mi, es que al conectar cualquiera de la interfaces de red me asigna una IP correspondiente al dominio de red.
Aun no encuentro el problema!!!!

---

### Post by guillermolisi on 2009-05-20
> **Hei Ku said:**
> tu interfaz aparece como eth10 en el ifconfig, pero como eth0 en el archivo interfaces.

Tira un lspci y postea el resultado, para ver que placa de red tenes.
HeiKu te indico algo que podria ser parte o todo el problema. Te lo cito ariba para que vuelvas a leerlo.

---

### Post by caraPintada on 2009-05-21
Aca esta la devolucion del comando....

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

____________________________________________________________
Hoy la cara pintada mas que nunca, arriba del camion que comienza el carnaval.

---

### Post by Hei Ku on 2009-05-21
tira de vuelta un ifconfig, a ver si cambió la interfaz. Si se mantiene estable, podemos cambiar el archivo interfaces para que tome la interfaz correcta. Si no, va a requerir un poco mas de magia.

---

### Post by caraPintada on 2009-05-21
Bueno tire el ifconfig y continua el eth10
en el archivo interfaces reemplace el eth0 por eth10 y cuando reinicie el network de init.d tiro esto
emanuel@emanuel-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth10.pid with pid 8721
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth10/00:1d:92:4d:4c:19
Sending on   LPF/eth10/00:1d:92:4d:4c:19
Sending on   Socket/fallback
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth10 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Hei Ku on 2009-05-21
Rarisimo. En XP anda todo ok, no? Podes abrir un command y postear lo que te tira ipconfig /all en el XP?

Que paso cuando dejo de andar? Actualizaste el kernel o algo asi?

---

### Post by caraPintada on 2009-05-21
aca esta el ipconfig /all de xp con las dos interfaces conectadas



Configuración IP de Windows



        Nombre del host . . . . . . . . . : Ema

        Sufijo DNS principal  . . . . . . : 

        Tipo de nodo . . . . . . . . . .  : desconocido

        Enrutamiento habilitado. . . . . .: No

        Proxy WINS habilitado. . . . .    : No



Adaptador Ethernet Conexión de área local 5          :



        Estado de los medios. . . .: medios desconectados

        Descripción. . . . . . . . . . .  : Realtek RTL8139/810x Family Fast Ethernet NIC

        Dirección física. . . . . . . . . : 00-1D-92-4D-4C-19



Adaptador Ethernet Conexiones de red inalámbricas 2          :



        Sufijo de conexión específica DNS : 

        Descripción. . . . . . . . . . .  : Atheros AR5007EG Wireless Network Adapter

        Dirección física. . . . . . . . . : 00-15-AF-62-20-E5

        DHCP habilitado. . . . . . . . .  : No

        Autoconfiguración habilitada. . . : Sí

        Dirección IP. . . . . . . . . . . : 192.168.1.103

        Máscara de subred . . . . . . . . : 255.255.255.0

        Puerta de enlace predeterminada   : 192.168.1.1

        Servidor DHCP . . . . . . . . . . : 192.168.1.1

        Servidores DNS . . . . . . . . . .: 200.42.0.111

                                            200.42.97.111

                                            200.42.97.110

        Concesión obtenida . . . . . . .  : jueves, 21 de mayo de 2009 17:13:31

        Concesión expira . . . . . . . . .: viernes, 22 de mayo de 2009 17:13:31


espero que sirva

---

