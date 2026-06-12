---
title: "[Consulta] Placa PCI Wireless Linksys WMP54G"
date: 2010-02-06
forum: Hardware
---

### Post by leonardomdq on 2010-02-06
Hola  a todos, queria hacerles una consulta antes de comprarme una [placa PCI Wireless Linksys WMP54G]("http://www.linksysbycisco.com/LATAM/es/products/WMP54G"). 
El tema es asi, tenia internet en mi casa y lo di de baja, mi hermana vive en el fondo y tiene speedy y pensaba compratir internet con ella, en su casa tiene un modem Zyzel P630.
Mi duda es si la placa PCI Linksys va bien con ubuntu y si tiene buena potencia.

Sldos
Leonardo

---

### Post by leonardomdq on 2010-02-08
Nadie podra aconsejarme si me conviene esta placa y/o alguna otra marca o modelo? no quiero meter la pata al comprarla...

Slds
Leonardo

---

### Post by luks911 on 2010-02-09
Exepriencia con la placa no tengo ninguna. Por lo que dice acá[0], debería funcionar. Al mismo tiempo es difícil dar un veredicto teniendo en cuenta que parece que puede venir con diversos chips. 
Lo ideal sería que la compres en algún lugar donde te la dejen probar, aunque se me ocurre que de un modo u otro tiene que andar.

[0] [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G)

---

### Post by guillermolisi on 2010-02-09
En todos los casos lo mas importante es conocer que chip se utilizo en el adaptador inalambrico ya que los drivers se hacen para el chip, no para la placa (con lo cual marca y modelo pasan a un segundo plano de referencia general).

Te paso algunos links especificos sobre el tema, en Ingles, a titulo de referencia.

[http://linuxwireless.org/](http://linuxwireless.org/)
[http://hardware4linux.info/type/114/](http://hardware4linux.info/type/114/)
[http://hardware4linux.info/type/98/](http://hardware4linux.info/type/98/)

---

### Post by leonardomdq on 2010-02-09
Muchas gracias por las respuestas, me voy a fijar bien entonses que chip va mejor y luego les comento como me fue.

Slds

---

### Post by leonardomdq on 2010-02-11
Acabo de comprar e instalar la placa PCI TP-Link mod. TL-WN651G 108M eXtended Range, instale, inicie sistema y salio andando....ningun problema. 
El chip que trae es Atheros.

Saludos

---

### Post by leonardomdq on 2010-02-12
Como les comente mas arriba conecte la placa PCI TP-Link Wireless mod. TL-WN651G 108M eXtended Range y salio andando. (Chip Atheros)
El tema es que la señal esta como maximo a 40%, no se si es por el drivers que de ubuntu o que, alguien me daria a mano para ver que puede ser? 

Desde ya muchas gracias

---

### Post by luks911 on 2010-02-12
Pasanos los resultados de los comandos

```
lspci
```

para ver cuál es el chip. 

Y de

```
sudo lshw -C Network

```
para ver qué driver/módulo está usando.

De todos modos, a veces el dato sobre la señal no es muy fiel, por lo que si no tenés problemas, si se te corta la conexión, no es para preocuparse. Además no sólo depende de tu placa wifi, sino también del router, la distancia y obstáculos.

---

### Post by leonardomdq on 2010-02-12
gracias luks por responder, aca dejo las salidas que me pediste

Ademas se corta de ves en cuando la conexion y no pasa de 40% de señal 
[FONT=monospace]
[/FONT]lspci
```

leonardo@leonardo-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
leonardo@leonardo-desktop:~$ 

```sudo lshw -C Network
```

leonardo@leonardo-desktop:~$ sudo lshw -C Network
[sudo] password for leonardo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:2a:40:65
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wmaster0
       version: 01
       serial: 00:25:86:d3:98:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.33 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcfffff
leonardo@leonardo-desktop:~$ 


```

---

### Post by luks911 on 2010-02-12
Estás usando el driver libre ath5k, incluido en el kernel. Si querés, podés probar compilando e instalando madwifi. Para eso:

1) Instalás lo necesario para compilar:
```
sudo apt-get update && sudo aptitude install build-essential linux-headers-$(uname -r)

```

2) Bajás el driver:
```
wget http://snapshots.madwifi-project.org/madwifi-trunk/madwifi-trunk-r4118-20100201.tar.gz

```
3) Lo extraés:
```
tar xzf madwifi-trunk-r4118-20100201.tar.gz
```

4) Te movés a la carpeta que se creó:
```
cd madwifi-trunk-r4118-20100201
```

5) Compilás:
```
make
```

6) Instalás:
```
sudo make install
```

7) Editás el archvio blacklist-ath_pci.conf para evitar que se cargue el driver que estás usando y no el nuevo.
```
sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```

y lo dejás así

```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci
blacklist ath5k
```

8 ) Hacés que el nuevo driver se cargue al inicio editando el archivo modules
```
sudo gedit /etc/modules
```

y al final le agregás una línea que diga

```
ath_pci
```

9) Reiniciás. Cada vez que haya una actualización del kernel vas a tener que repetir él proceso. Si no estás confome deshacés los cambios en los archivos blacklist-ath_pci.conf y modules, y desinstalás el driver desde la carpeta donde compilaste con sudo make uninstall

---

### Post by leonardomdq on 2010-02-12
Gracias Luks lo instale, pero cuando voy a sistema -> admin -> controladores de hardware me sale para activar el controlador pero me tira un error, te dejo una captura

[[IMG]http://i.imagehost.org/t/0649/Pantallazo.jpg[/IMG]]("http://i.imagehost.org/view/0649/Pantallazo")


/var/log/jockey.log

```

2010-02-13 00:19:55,364 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8fac48c>
2010-02-13 00:19:55,365 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 00:19:55,483 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 00:19:55,488 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 00:19:55,518 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 00:19:55,520 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-13 00:19:55,522 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-13 00:19:55,533 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-13 00:19:55,534 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-13 00:19:55,535 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 00:19:57,441 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 00:19:57,442 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 00:19:57,463 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 00:19:57,463 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 00:19:57,464 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 00:19:57,469 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 00:19:57,484 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 00:19:57,484 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 00:19:57,484 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 00:19:57,490 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 00:19:57,491 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 00:19:57,491 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 00:19:57,524 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 00:19:57,525 DEBUG: Firmware for DVB cards not available
2010-02-13 00:19:57,525 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 00:19:57,530 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 00:19:57,531 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 00:19:57,546 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 00:19:57,546 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 00:19:57,582 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 00:19:57,583 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-13 00:19:57,583 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-13 00:19:57,583 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 00:19:57,600 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 00:19:57,644 DEBUG: Software modem not available
2010-02-13 00:19:57,645 DEBUG: all custom handlers loaded

```

---

### Post by luks911 on 2010-02-12
En teoría, haciendo lo que te pasé queda instalado y funcionando sin necesidad de que lo actives en controladores de hardware. ¿Cuando reiniciaste tenías wifi? ¿Qué te devuelve ahora el comando sudo lshw -C Network?

---

### Post by leonardomdq on 2010-02-12
> **luks911 said:**
> En teoría, haciendo lo que te pasé queda instalado y funcionando sin necesidad de que lo actives en controladores de hardware. ¿Cuando reiniciaste tenías wifi? ¿Qué te devuelve ahora el comando sudo lshw -C Network?
Si cuando reinicie tenia señal, de repente la señal esta en 8% y sube de golpe a 99% y asi, sube y baja permanentemente.
Tendre que configurar algo en conexiones de Red?


sudo lshw -C Network
```

leonardo@leonardo-desktop:~$ sudo lshw -C Network
[sudo] password for leonardo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:2a:40:65
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wifi0
       version: 01
       serial: 00:25:86:d3:98:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.33 latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:fdcf0000-fdcfffff
leonardo@leonardo-desktop:~$ 


```

---

### Post by luks911 on 2010-02-12
> **leonardomdq said:**
> Si cuando reinicie tenia señal, de repente la señal esta en 8% y sube de golpe a 99% y asi, sube y baja permanentemente.

sudo lshw -C Network
```

leonardo@leonardo-desktop:~$ sudo lshw -C Network
[sudo] password for leonardo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:2a:40:65
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wifi0
       version: 01
       serial: 00:25:86:d3:98:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ath_pci[/COLOR] ip=192.168.1.33 latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:fdcf0000-fdcfffff
leonardo@leonardo-desktop:~$ 


```

Ok.Lo que te marqué en rojo arriba muestra que, en efecto, estás usando el driver que compilaste. Si no te conforma el rendimiento, podés volver al anterior. Yo con otra Atheros y versiones previas del ath5k prefería Madwifi, porque no tenía cortes y permitía que funcionara el led del wifi :-P Pero eso puede variar, ya ves. Igual, insisto, lo principal es que no tengas cortes de la conexión.

---

### Post by leonardomdq on 2010-02-12
Muchas gracias Luks, me quedo con este driver por el momento no tube cortes.
Gracias por la ayuda ;)

Saludos

---

