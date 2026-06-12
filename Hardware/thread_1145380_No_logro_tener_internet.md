---
title: "No logro tener internet"
date: 2009-05-01
forum: Hardware
---

### Post by FB91 on 2009-05-01
Hola! ayer instalé por primera vez Ubuntu (9.04) y uno de los problemas que se me presentaron fueron los siguientes:
[B]
1.[/B] No consigo tener internet. Mi situación es la siguiente, tengo 2 PCs una de ellas tiene internet y le pusimos un router para hacer una red entre las maquinas. Mi PC es justamente la que no tiene internet :P y nose como hacer para que lo "comparta" con la mia. La red funciona, es decir, puedo acceder a los archivos de la otra PC pero al intentar usar internet la cosa va para atrás :S

**2.** No me reconoce la tarjeta de video. No puedo cambiar la resolución de la pantalla (800x600) y no me deja activar los efectos visuales. Tengo una placa madre Asus M2N68 con una GeForce 7025 onboard, así que me bajé [estos drivers]("http://la.nvidia.com/object/linux_display_amd64_180.51_la.html") de la web de nVIDIA pero no logro instalarlos. Escribo en la terminal "sh NVIDIA-Linux-x86_64-180.51-pkg2.run" pero me sale una pantalla azul que dice "You appear to be runing an X server; please exit X before installing" y cuando le doy al OK me sale otro mensaje: "Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details"
[B][COLOR=Red]
[/COLOR][/B][CENTER]**[SIZE=2][COLOR=Red]Gracias de antemano![/COLOR][/SIZE]**
[/CENTER]

---

### Post by luks911 on 2009-05-01
> **FB91 said:**
> **2.** No me reconoce la tarjeta de video. No puedo cambiar la resolución de la pantalla (800x600) y no me deja activar los efectos visuales. Tengo una placa madre Asus M2N68 con una GeForce 7025 onboard, así que me bajé [estos drivers]("http://la.nvidia.com/object/linux_display_amd64_180.51_la.html") de la web de nVIDIA pero no logro instalarlos. Escribo en la terminal "sh NVIDIA-Linux-x86_64-180.51-pkg2.run" pero me sale una pantalla azul que dice "You appear to be runing an X server; please exit X before installing" y cuando le doy al OK me sale otro mensaje: "Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details"
[B][COLOR=Red]
[/COLOR][/B][CENTER]**[SIZE=2][COLOR=Red]Gracias de antemano![/COLOR][/SIZE]**
[/CENTER]

Sobre el problema con la red no tengo mucha idea, por el video andá a Sistema > Administración > Controladores de Hardware

Ahí te va a recomendar un driver para instalar, le das a Instalar o Habilitar y Ubuntu se encarga del resto: bajarlo e instalarlo. Si en el proceso se llega a trabar, avisá, pero antes reiniciá a ver si lo instaló. El único inconveniente es que para eso vas a necesitar internet.
Si no lográs conectarla de ningún modo, también avisá que se pueden bajar los .deb necesarios en Packages Ubuntu desde otra máquina, llevarlos a la tuya con ubuntu, e instalarlos.

---

### Post by luks911 on 2009-05-01
Sobre lo de internet, ¿tu PC debería recibir la conexión directamente del router, no?
Pon´çe acña los resultados de los siguientes comandos en consola

```
ifconfig
```

```
cat /etc/network/interfaces 
```

A ver si se me ocurre algo y si no son útiles para que quien pueda darte una mano tenga más información.

---

### Post by staar on 2009-05-01
preguntas: el router esta actuando como modem?, o la otra pc se conecta directamente a internet sola?, si es así, que sistema operativo tiene la otra pc?...

el mensaje que te aparece es porque el servidor gráfico aún esta corriendo, hace lo siguiente:

-pasate a una consola (Ctrl + Alt + F1)
-para parar el display manager, y el servidor gráfico, poné: ```
sudo /etc/init.d/gdm stop 
```
-te pide tu pass, no te asustes si no sale nada al escribir, igual lo está tomando, solo que se oculta para que nadie te lo robe :-D ;-D
-ahora si, seguí con las instrucciones de Nvidia: sh NVIDIAlalaladadadtoda la cosa...
-al terminar, poné: ```
sudo /etc/init.d/gdm start 
``` para volver a iniciar el display manager...

saludos

---

### Post by FB91 on 2009-05-01
Gracias por sus comentarios!!

> **staar said:**
> preguntas: el router esta actuando como modem?, o la otra pc se conecta directamente a internet sola?, si es así, que sistema operativo tiene la otra pc?...

La otra pc se conecta a internet con el modem de Arnet (el que es medio viejo! que parece un plato volador xD) y su sistema operativo es el Windows XP

> **staar said:**
> 
el mensaje que te aparece es porque el servidor gráfico aún esta corriendo, hace lo siguiente:

-pasate a una consola (Ctrl + Alt + F1)
-para parar el display manager, y el servidor gráfico, poné: ```
sudo /etc/init.d/gdm stop 
```-te pide tu pass, no te asustes si no sale nada al escribir, igual lo está tomando, solo que se oculta para que nadie te lo robe :-D ;-D
-ahora si, seguí con las instrucciones de Nvidia: sh NVIDIAlalaladadadtoda la cosa...
-al terminar, poné: ```
sudo /etc/init.d/gdm start 
``` para volver a iniciar el display manager...

saludos

al escribir "sudo /etc/init.d/gdm stop" me dice: "No existe el fichero ó directorio" ¿estaré indicando mal la ruta?

Mientras tanto... como hago para salir de la consola que abri presionando Ctrl+Alt+F1?

Con respecto a los consejos de luks911 gracias por la ayuda! más tarde pruebo eso y te digo como me fué

---

### Post by Air23 on 2009-05-01
> **FB91 said:**
> Mientras tanto... como hago para salir de la consola que abri presionando Ctrl+Alt+F1?
Ctrl+Alt+F7

---

### Post by luks911 on 2009-05-01
> **FB91 said:**
> La otra pc se conecta a internet con el modem de Arnet (el que es medio viejo! que parece un plato volador xD) y su sistema operativo es el Windows XP

Ok, un Huawei. ¿Y tu máquina a qué se conecta? ¿A la otra PC, a un router?

> **FB91 said:**
> al escribir "sudo /etc/init.d/gdm stop" me dice: "No existe el fichero ó directorio" ¿estaré indicando mal la ruta?

Mmmmm.... la ruta está bien. ¿Estás usando Ubuntu con Gnome? A no ser que en Jaunty lo hayan cambiado...

> **FB91 said:**
> Con respecto a los consejos de luks911 gracias por la ayuda! más tarde pruebo eso y te digo como me fué

Probá con una conexión a internet y yendo a Controladores de Hardware o Synaptic, apt-gte o aptitude, bah, digo, como para aprovechar que Ubuntu hace bastante sencilla la instalación de los drivers.

---

### Post by FB91 on 2009-05-01
Mi máquina se conecta mediante la placa de red inalámbrica a un router.

Me fijé eso de la ruta... fui al administrador de archivos y busqué /etc/init.d/gdm y existe... nose que hago mal :S Lo que hice fue: Ctrl + Alt + F1, ingrese mi usuario y mi contraseña. después tecleé "sudo /etc/init.d/gdm stop" y me salió el mensaje ese de que no existe el fichero :S

---

### Post by josecuervo86 on 2009-05-01
> **FB91 said:**
> La otra pc se conecta a internet con el modem de Arnet (el que es medio viejo! que parece un plato volador xD) y su sistema operativo es el Windows XP

El alfajor del diablo!!!

---

### Post by luks911 on 2009-05-01
> **FB91 said:**
> Mi máquina se conecta mediante la placa de red inalámbrica a un router.
Ah, tu máquina tiene wifi. Ok. Ejecutá en una terminal
```
ifconfig
```
y pegá el resultado. Eso va a mostrar los dispositivos de red que detecta. Capaz que no reconoce el wifi, capaz es otra cosa.
De paso, para adelantar un paso, pega también el resultado de 
```
lspci
``` si la placa es pci, o de 
```
lsusb
``` si la placa es usb
Esos comandos listan los dipositivos conectados por pci y usb a la máquina.

> **FB91 said:**
> Me fijé eso de la ruta... fui al administrador de archivos y busqué /etc/init.d/gdm y existe... nose que hago mal :S Lo que hice fue: Ctrl + Alt + F1, ingrese mi usuario y mi contraseña. después tecleé "sudo /etc/init.d/gdm stop" y me salió el mensaje ese de que no existe el fichero :S
Si usás gnome y decís que el archivo está, entonces no entiendo nada :S

---

### Post by staar on 2009-05-01
no, me acabo de fijar y en jaunty no cambio, fijate si escribiste bien la ruta, porque es esa, si estas usando kubuntu, tendrias que cambiar gdm por kdm (creo, no estoy del todo seguro que kdm este en la misma ruta)...

saludos

---

### Post by staar on 2009-05-01
ooops

---

### Post by FB91 on 2009-05-01
Hice lo que me dijo luk911... aquí les pego los resultados:

**fb91@FB91:~$ ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:24:8c:3f:c7:fb  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:252 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:516 (516.0 B)  TX bytes:516 (516.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:08:54:92:2d:23  
          inet dirección:192.168.1.100  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::208:54ff:fe92:2d23/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:11557 (11.5 KB)  TX bytes:6652 (6.6 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-08-54-92-2D-23-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[B]
fb91@FB91:~$ lspci[/B]
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
00:0d.0 VGA compatible controller: nVidia Corporation Device 03d6 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
**fb91@FB91:~$ lsusb**
Bus 001 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by luks911 on 2009-05-01
> **FB91 said:**
> Hice lo que me dijo luk911... aquí les pego los resultados:

**fb91@FB91:~$ ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:24:8c:3f:c7:fb  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:252 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:516 (516.0 B)  TX bytes:516 (516.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:08:54:92:2d:23  
          inet dirección:192.168.1.100  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::208:54ff:fe92:2d23/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:11557 (11.5 KB)  TX bytes:6652 (6.6 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-08-54-92-2D-23-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Ok, el wifi es detectado. Es el dispositivo wlan0. Ahora, que alguien me corrija si me equivoco pero me parece que hasta ya tenés una ip (192.168.1.100) dentro de la red. ¿El ícono de redes te muestra conectado? ¿Si querés navegar te da algún mensaje de error? ¿Qué pasa si mandas un ping? Por ejemplo:

```
ping www.google.com
```

El ping lo cortás con Ctrl+c

---

### Post by staar on 2009-05-01
pregunta: estás compartiendo el internet desde la pc con windos? en ese caso tendrias que configurar la red inalámbrica para tener ip estática y los mismos dns que la otra máquina...

saludos

---

### Post by FB91 on 2009-05-01
Ya pude hacer eso de desactivar el gnome !!! me habia equivocado yo !! tipié mal ](*,)](*,)](*,) y ya me reconoció la tarjeta de video!! la resolución 800x600 ya me estaba volviendo LOCO :lolflag:

Ahora lo único que falta es la conexión a internet!

En la terminal escribí "ping www.google.com" y no pasó nada.... lo tuve que detener con el Ctrl.+C.

Mozilla Firefox al intentar abrir google.com me dice que verifique mi configuración de red y servidores DNS. También pregunta si mi computadora o red está protegida por un firewall o proxy


Gracias por la ayuda!!!!!!

---

### Post by luks911 on 2009-05-01
La conexión es así?: el huawei se conecta a internet, de ahí al router y de ahí la máquina con win y la otra con ubuntu (también conectada al router)


Si es así, se me hace que hay que configurar el router, tal vez los dns. O configurar la conexión en ubuntu manualmente con los mismos datos que la de Win (máscara de red, dns).

---

### Post by Mauro22 on 2009-05-01
Para descartas los DNS como dijo luks911

pone en el navegador

[http://64.233.161.99/](http://64.233.161.99/)


Deberia llevarte a Google, si no va es algo mas que los DNS (Puerta de enlace, ip en rango, etc)

---

### Post by FB91 on 2009-05-02
> **Mauro22 said:**
> Para descartas los DNS como dijo luks911

pone en el navegador

[http://64.233.161.99/](http://64.233.161.99/)


Deberia llevarte a Google, si no va es algo mas que los DNS (Puerta de enlace, ip en rango, etc)

Poniendo [http://64.233.161.99/](http://64.233.161.99/) en el navegador no aparece nada!

Voy a seguir buscando info de este tema...

---

### Post by faktorqm on 2009-05-04
Hola, un thread muy desordenado para leer...

Posteá:

- la configuracion que tenes en windows (ip, mascara, puerta de enlace, DNS, etc) y que tipo de conexion tenes (wi-fi, cable, etc).

- los comandos:

```
ifconfig
```
y
```
cat /etc/resolv.conf
```

- la configuracion fisica de la red, es decir, viene del telefono al modem, luego al windows, del windows al router? o desde el modem al router y de ahi se conectan las dos pc's? 

Explica bien eso y lo solucionamos de toque salu2!

---

### Post by faktorqm on 2009-05-04
me olvide de algo:

> **luks911 said:**
> ¿Qué pasa si mandas un ping? Por ejemplo:

```
ping www.google.com
```

El ping lo cortás con Ctrl+c

El comando para hacer un ping "clasico" (de 4 pruebas) es

```
ping -c 4 <algo>
```

para mas info, "man ping". salu2!

---

### Post by FB91 on 2009-05-04
Tengo arnet con el modem viejo (el redondito), o sea q esta conectado a la compu por el usb.
Tengo 3 maquinas: esta desde donde te escribo, que tiene la coneccion a internet; otra que va conectada al access point mediante un cable; y la nueva que iria con la placa inalambrica.
La red anda bien en las 3 maquinas ejecutando windows, las ips son 192.168.1.1 para el linksys, .2 para esta maquina q es donde tengo internet, y .3 y .4 para las otras. En mis sitios red puedo ver todas las pc.
La configuracion fisica seria: de la pc pricipal (la q tiene la conexion a internet) a un puerto ethernet del access point, la otra maquina tambien a otro de los puertos ethernet, y la pc nueva iria por wireless.
El problema es q no consigo compartir la conexion a internet ni siquiera en windows. Probe con el proxy de analogx pero parece no funcionar (?) y eso q configure el navegador de internet con la ip de la pc principal y el puerto correspondiente... Me falta configurar algo???
Espero q me respondan, gracias!

---

### Post by luks911 on 2009-05-04
Para despejar una duda, aunque el que sabe más de esto es faktorqm: ¿sólo tenés internet en la máquina conectada directamente al modem, pero no en las otras dos conectadas al linksys?
Si es así el problema está en la PC que recibe la conexión de parte del modem o en el linksys.

---

### Post by FB91 on 2009-05-04
> **luks911 said:**
> Para despejar una duda, aunque el que sabe más de esto es faktorqm: ¿sólo tenés internet en la máquina conectada directamente al modem, pero no en las otras dos conectadas al linksys?
Si es así el problema está en la PC que recibe la conexión de parte del modem o en el linksys.

Si, tengo internet solamente en la maquina q tiene el modem conectado, en las otras no

---

### Post by faktorqm on 2009-05-05
Bueno, aclarado el panorama, ya creo que puedo identificar el error. A pesar de que desde el punto de vista practico hiciste toda la red bien y bajo la misma subred, te fallo la parte teorica. El linksys, es un switch o es un router? lo mas probable es que sea un router, o como minimo, la parte del wireless es un router. 

Para empezar, lo que deberías hacer es lo siguiente: 

- Compartir la conexión en la computadora que tiene el modem usb a través de ethernet y conectar UNA sola compu para ver si comparte internet bien o no.

Esto es, en la placa de red de la que tiene internet no toques nada, (deberias tener la direccion 192.168.1.2 segun lo que pusiste).

Ahora, agarra otra compu y mediante un cable cruzado conectala a que tiene internet. Entonces a esta le configuras la direccion 192.168.1.1 y en la puerta de enlace pones 192.168.1.2 (la otra pc) y en los dns quiza debas hacerlo tambien, eso depende de como compartas la conexión desde la pc que tiene internet).

Cuando tengas internet en las dos computadoras con esta configuracion, entonces ya diste un buen paso adelante. Ahora saca el cruzado de la pc que no comparte internet y enchufaselo a la boca WAN del router linksys. Entras a la configuracion web y le configuras la parte de WAN como ip fija (si es necesario, si no no) y luego a la parte de LAN la configuras como otra red, que puede ser tranquilamente 192.168.2.1 (puse 2 para no marearte, puede ser cualquier cosa entre 2 y 254) y la compu que usaste primero para probar la conexión ahora la tenes que conectar al router con un cable derecho y ponerle la direccion 192.168.2.2, mascara 255.255.255.0 y puerta de enlace, 192.168.2.1 (ip de la boca lan del router). (ojo con los DNS, pone como dns 192.168.2.1)
Ahora, si eso te anda, estamos bien encaminados. Para la wireless se pueden hacer 2 cosas:

- armar otra red mas (estilo 192.168.3.<algo>)
- usar a la parte wifi del router como access point (como switch)

Yo recomiendo usar otra red mas, pero es bastante mas dificil de implementar, y depende del modelo del router. Si tenes el wrt54g como el resto de los mortales :P avisa y vemos como seguimos.

Si algo no te anda, detalla lo mas posible el problema y que hiciste y que pasó. Salu2!

---

### Post by FB91 on 2009-05-06
Ya puedo tener internet... pero usando windows xp. Mi hermano lo pudo configurar... nose muy bien que hizo pero la cosa es que, por lo menos en windows, funciona internet.

Ahora mi pregunta es... como configuro para tener conexion a internet desde Ubuntu? es decir, en esta pc desde donde les escribo ahora tengo el xp y ubuntu instalados, el problema es que no lo se configurar desde ubuntu :S

Consejos?

---

### Post by Hei Ku on 2009-05-06
Que tal si posteas la configuracion que tenes en XP?

En una ventana de DOS pone:

ipconfig /all

---

### Post by FB91 on 2009-05-06
El resultado de ipconfig /all fue este:

> Configuración IP de Windows
nombre del host............................:ESTUDIO
sufijo DNS principal.......................:
tipo de nodo.................................:desconocido
enrutamiento IP habilitado.............:si
proxy WINS habilitado...................:no

Adaptador Ethernet Conexión de área local
sufijo de conexión específica DNS...:
descripción...................................:NIC Fast Ethernet PCI Familia RTL8139 de Realtek
dirección específica.......................:00-08-54-A5-38-DD
DHCP habilitado............................:no
dirección IP..................................:192.168.0.1
máscara de subred.......................:255.255.255.0
puerta de enlace predeterminado:

---

### Post by Hei Ku on 2009-05-06
Faltan los datos de DNS y de la puerta de enlace predeterminada (gateway). Lo de los DNS lo zafamos, pero el gateway es imprescindible.

---

### Post by FB91 on 2009-05-06
> **Hei Ku said:**
> Faltan los datos de DNS y de la puerta de enlace predeterminada (gateway). Lo de los DNS lo zafamos, pero el gateway es imprescindible.

Y como cosigo los datos del gateway? lo que copié es lo que me tiró la máquina al escribir
ipconfig /all

---

### Post by Hei Ku on 2009-05-06
No decia nada al final de: "puerta de enlace predeterminado: " ???

---

### Post by FB91 on 2009-05-06
lo hice de nuevo y ahora si me dijo eso de la puerta de enlace...

```
Puerta de enlace predeterminada...........:190.138.167.246
Servidores DNS....................................:200.45.191.35
                                                   200.45.48.233
```

---

### Post by Hei Ku on 2009-05-06
Postea todo completo de vuelta, porque esa puerta de enlace no cierra con la IP y mascara de subred que pusiste anteriormente.

---

### Post by FB91 on 2009-05-06
> Configuración IP de Windows
nombre del host............................:ESTUDIO
sufijo DNS principal.......................:
tipo de nodo.................................:desconocido
enrutamiento IP habilitado.............:si
proxy WINS habilitado...................:no

Adaptador Ethernet Conexión de área local
sufijo de conexión específica DNS...:
descripción...................................:NIC Fast Ethernet PCI Familia RTL8139 de Realtek
dirección específica.......................:00-08-54-A5-38-DD
DHCP habilitado............................:no
dirección IP..................................:192.168.0.1
máscara de subred.......................:255.255.255.0
puerta de enlace predeterminado:

Adaptador PPP Highway - Conexión ADSL
sufijo de conexión específica DNS:
descripción...................................:WAN(ppp/slip)Interface
dirección física..............................:00-53-45-00-00-00
DHCP Habilitado............................: No
dirección IP...................................:190.138.167.246
máscara de subred........................:255.255.255.255
puerta de enlace predeterminada....:190.138.167.246
servidores DNS.............................:200.45.191.35
200.45.48.233

Ya que estoy te hago una pregunta, tengo ip dinámica... eso cambiaría en algo la manera en que lo tengo que configurar??? capaz que es media (o muy) boba la pregunta pero es la primera vez que hago esto xD

Gracias por la ayuda!! :P

---

### Post by Hei Ku on 2009-05-06
el problema no es si es ip dinamica o estatica, sino el tipo de conexion. Eso que tenes ahi es una conexion ADSL, que se configura distinto a una conexion de red normal. Pense que la maquina con ADSL era otra.

Qué modem tenes, y como esta conectado a tu PC, por USB?

---

