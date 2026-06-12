---
title: "Problemas al instalar TL-WN353GD Wireless adapter"
date: 2010-02-04
forum: Hardware
---

### Post by FB91 on 2010-02-04
Estoy tratando de instalar el "Wireless PCI Adapter" que me compré modelo TL-WN353GD y no puedo hacerla andar de ninguna manera. Probé unos cuantos [tutoriales]("http://akebuntu.comyr.com/instalar-tp-link-tl-wn353gd-chip-realtek-rtl8185-en-ubuntu/") y nada...

Intenté con el ndiswrapper usando los drivers para windows que trae el CD que viene junto a la placa y no hay manera de que funcione.

Otra pregunta, cómo sé si la placa está instalada correctamente? pruebo con el comando ndiswrapper -l y me muestra como si estuviera instalado pero no me salen las conexiones wifi para conectarme

Cualquier tutorial que consigan me sirve, tengan en cuenta que estoy usando Ubuntu 9.10 la versión de [B]64bits

[/B]Ah, y si les sirve les dejo la salida de lspci y ifconfig> **fb91@fb91-desktop:~$ lsp**ci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
**fb91@fb91-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:24:8c:3f:c7:fb  
          Direc. inet:192.168.0.3  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::224:8cff:fe3f:c7fb/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2722 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2805 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1617959 (1.6 MB)  TX bytes:477566 (477.5 KB)
          Interrupción:27 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:136 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:136 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:11823 (11.8 KB)  TX bytes:11823 (11.8 KB)

---

### Post by FB91 on 2010-02-05
Intenté instalando con el ndiswrapper los drivers para VistaX64 y parece que ahora la tomó, o por lo menos ahora aparece cuando hago el comando iwconfig.
Ah, y también ahora me aparece Redes Inalámbricas cuando clickeo el icono de Conexiones de red, miren la imagen...

[IMG]http://img686.imageshack.us/img686/2551/wifiz.jpg[/IMG]

Les dejo la salida de los comandos: iwconfig, ifconfig y ndiswrapper -l

> fb91@fb91-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:24:8c:3f:c7:fb  
          Dirección inet6: fe80::224:8cff:fe3f:c7fb/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:6 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:492 (492.0 B)
          Interrupción:27 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:8 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:494 (494.0 B)  TX bytes:494 (494.0 B)

wlan1     Link encap:Ethernet  direcciónHW 00:25:86:d5:7d:8b  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW 00-25-86-D5-7D-8B-00-00-00-00-00-00-00-00-00-00  
          ACTIVO FUNCIONANDO  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

fb91@fb91-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

fb91@fb91-desktop:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8185 : driver installed
    device (10EC:8185) present (alternate driver: rtl8180)
fb91@fb91-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
Supongo que ya está casi todo listo... me debe faltar algún detalle pero nose que puede ser. Les agradezco cualquier ayuda que me den :D

EDIT: Ya funciona, simplemente reinicié y anduvo

---

