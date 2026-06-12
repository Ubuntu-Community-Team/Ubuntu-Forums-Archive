---
title: "Notebook BGH Argentina"
date: 2009-07-30
forum: Hardware
---

### Post by lucky_luke on 2009-07-30
Hola acabo de comprar una notebook BGH e-nova modelo ex-4325 con las siguientes caracteristicas:
* Pantalla de 14.1” TFT LCD WXGA GLARE
* WebCam Incorporada 1,3Mp
* Procesador Intel Core 2 Duo 5800
* Disco de 250 GB
* Memoria 2 GB
* DVD+/-RW (Dual Layer)
* Video SIS M672 MIRAGE 3 (256 MB)
* Realtek ALC662 @ SIS High Definition
* Modem 56kbps V.90/92
* Placa de red 10/100 Mbps
* WiFi 802.11 b/g
* 4 USB CRT
* Multilector de memoria 4 en 1 (Memory Stick,
* MS Pro, Multi Media Card, Secure Digital)
* Dimensiones 34,3 x 24,5 x 3,4
* Peso 2.7 Kg
* AC 100-240Volt, 50-60 Hz, 65W 20Voltage
* Bateria 6 celdas 4400 mAh

Habrá alguien que tenga una máquina similar? La Sis Mirage 3 es un verdadero problema para usar con Linux pero más o menos fui resolviendo algunos problemas usando Linux Mint Gloria 7 (64 bits). A lo que no le encuentro la vuelta es al wifi. Detecta la placa pero no puedo conectar a internet. Entiendo que esta máquina es bastante parecida a un modelo de notebook Olivetti que tienen muchas personas, quizás podríamos intercambiar data entre nosotros...
Gracias, saludos

---

### Post by luks911 on 2009-07-30
¿Tenés sólo problemas con el wifi? Contá qué hiciste hasta ahora y pasanos el resultado del comando
```
lspci
```
así vemos qué placa es y qué se puede hacer.

---

### Post by guillermolisi on 2009-07-30
Y por las dudas, tambien el resultado del lsusb

---

### Post by lucky_luke on 2009-07-31
del comando lspci me devuelve:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Y del otro: 
lucky@Tuxie ~ $ lsusb

Bus 001 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd Camera
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Por las dudas agrego:
lucky@Tuxie ~ $ ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:03:0d:a9:71:b8  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:19 Dirección base: 0xdead 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

lucky@Tuxie ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Gracias!

---

### Post by luks911 on 2009-07-31
Acá[0] Preguntan por el mismo problema. La placa es detectada, se conecta al router pero no hay conexión a internet.
Hay un par de bugs y dos posibles soluciones, para ambas tenés que conectarte a internet por cable.
1) Abrís una terminal y ejecutás:
```
sudo aptitude update
sudo aptitude install linux-backports-modules-jaunty
```
Después reiniciá y probá si se conecta. Eso debe instalar nuevos módulos para tu wifi.

2) Abrís una terminal:
```
sudo aptitude install wicd
```
Reiniciás y probás la conexión. Eso instala wicd en lugar del Network Manager.

[0] [https://answers.launchpad.net/ubuntu/+source/network-manager/+question/69449](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/69449)

---

### Post by guillermolisi on 2009-07-31
Hay un thread que habla sobre una Olibook que pareceria ser similar a tu maquina.

El thread es largo pero creo que vale la pena leerlo de punta a punta.
Basicamente resolvieron problemas de video y de wifi.

[http://ubuntuforums.org/showthread.php?t=660167&highlight=RTL8187B](http://ubuntuforums.org/showthread.php?t=660167&highlight=RTL8187B)

---

### Post by lucky_luke on 2009-08-03
Bueno, actualicé los módulos e instalé Wicd. Pero nada cambia, quizá no sepa configurar el Wicd, por ejemplo cuando conecto por cable dice que la interfaz que usa es Eth0. Pero en la configuración para interfaz inalámbrica del wicd no figura ninguna...

---

### Post by guillermolisi on 2009-08-03
El thread que te recomende leer no ayudo en nada ?

---

### Post by lucky_luke on 2009-08-05
> **guillermolisi said:**
> El thread que te recomende leer no ayudo en nada ?

Sí Guillermo gracias. Lo que ocurre es que ese thread ya me lo conozco, me fue muy útil para resolver varios problemas pero no me sirvió para el wifi, por eso prefiero ir probando paso a paso lo que me sugieren aquí y que pensemos entre todos en función de lo que específicamente va pasando en mi máquina. 
Saludos cordiales,

---

### Post by luks911 on 2009-08-05
A ver. Luego de los cambios que hiciste, andá a una terminal y volvé a ejecutar
```
iwconfig
```
y además
```
iwlist scan
```
Pegá los resultados acá.
Lo primero para ver si sigue habiendo como antes un dispositivo de red inalámbrica y lo segundo te muestra las redes detectadas.

Ah, por lo que veo en el link que te había pasado, quienes dicen solucionarlo lo hicieron sólo instalando linux-backports, sin necesidad de wicd, ¿probaste si funcionaba así?

---

