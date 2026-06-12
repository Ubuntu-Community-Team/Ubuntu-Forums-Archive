---
title: "problemas con router"
date: 2010-07-04
forum: Hardware
---

### Post by elissss on 2010-07-04
buenas tardes, tengo un router encore ENHWI-N3 cuando lo conecto no lo reconoce, no puedo entrar desde el navegador a la ip del router para configurarlo.
tengo este programa,
[IMG]http://www.guia-ubuntu.org/images/4/4a/Network-admin.jpg[/IMG]
solo que cuando lo abro no me aparece la pestaña de conexiones, por lo tanto no puedo hacer ninguna modificacion desde ahi...

---

### Post by Karmaloco on 2010-07-04
Hola eliss

Lo conectas vía wireless? que dispositivo de red tenés para conectarlo al router?

---

### Post by elissss on 2010-07-04
Lo conecto via LAN.
la placa de red es NVIDIA nForce Networking Controller

---

### Post by sergiom99 on 2010-07-05
conectate a la red y postea la salida de los comandos lspci y ifconfig a ver que dicen.

---

### Post by elissss on 2010-07-06
**HOLA, ME APARECIÓ ESTO**

root@eliana:~# lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)

**Y ESTO**

root@eliana:~# ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1e:90:67:8b:12  
          Direc. inet:10.0.0.3  Difus.:10.0.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21e:90ff:fe67:8b12/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:28863 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:18402 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:38244780 (38.2 MB)  TX bytes:1937213 (1.9 MB)
          Interrupción:28 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:20 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

---

### Post by guillermolisi on 2010-07-06
Te estas conectando con una IP en el bloque 10.0.0.x/255.255.255.0 asi que para entrar y configurarlo por esa misma red la IP, el router deberia estar en el mismo bloque (ej: 10.0.0.1/255.255.255.0).

> Direc. inet:10.0.0.3  Difus.:10.0.0.255  Másc:255.255.255.0Si el router esta en otro bloque IP, para administrarlo deberias configurar la placa de red para que trabaje en la misma red que el router (ej: 192.168.0.3/255.255.255.0 para la PC y 192.168.0.1/255.255.255.0 para el router).

---

### Post by elissss on 2010-07-08
hola [COLOR=Black]guillermo... no entendi mucho lo que pusiste..  en realidad no se como hacer para configurar la placa de red. 
si podrias ayudarme te lo agradeceria!! =)[/COLOR]

---

