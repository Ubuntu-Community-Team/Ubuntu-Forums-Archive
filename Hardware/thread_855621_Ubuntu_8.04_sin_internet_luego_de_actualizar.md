---
title: "Ubuntu 8.04 sin internet luego de actualizar"
date: 2008-07-10
forum: Hardware
---

### Post by KameL on 2008-07-10
Hola amigos, les comento que decidí el día de ayer instalar mi primer GNU/Linux, en este caso la distro Ubuntu.
Todo marchaba bien con la versión 7.04 (la que instalé por medio del LiveCD), tenía internet (Fibertel Cablemodem) con una conexión de red manual buscando la IP desde windows. El problema es que me mandé de cabeza a actualizar a la 8.04 y de repente, sin tocar nada, me quedé sin internet. Probé mil cosas para solucionarlo, pero nada, sigo sin poder conectarme. Me parece que es problema de drivers (?) de la placa de red, o no me reconoce el modem. Recuerdo que cuando terminaba de actualizar, me decía "Eliminando paquetes obsoletos" o algo así... quizás me eliminó algo que necesitaba para conectarme. ¿alguna ayuda al respecto?

_**Algunos datos:**_
**ISP:** Fibertel (Cablemodem)
**Modem:** WebSTAR DPC2100 (Ethernet)
**Conexión:** Funcionando en WindowsXP, sin funcionar en Ubuntu 8.04.

--------------------------------------------------------------

**Datos de red (ipconfig/all desde Windows):**
Descripción______________________NVIDIA nForce Networking Controller
Dirección física_________________00-13-8F-D0-40-B5
DHCP habilitado__________________No
Autoconfiguración habilitada_____Sí
Dirección IP_____________________201.231.218.87
Mascara de Subred________________255.255.255.0
Puerta de enlace predeterminada__201.231.218.1
Servidor DHCP____________________172.20.2.12
Servidores DNS___________________200.49.130.31
_________________________________200.49.130.30
_________________________________200.49.130.34
_________________________________172.20.2.12

--------------------------------------------------------------

**Resutado sudo ifconfig:**
kamel@KameL:~$ sudo ifconfig
eth7      Link encap:Ethernet  direcciónHW 00:00:6c:c8:cc:f4  
          dirección inet6: fe80::200:6cff:fec8:ccf4/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:25217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1516126 (1.4 MB)  TX bytes:68381 (66.7 KB)
          Interrupción:220 Dirección base: 0x6000 

eth7:avahi Link encap:Ethernet  direcciónHW 00:00:6c:c8:cc:f4  
          inet dirección:169.254.11.37  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:220 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1514 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:78782 (76.9 KB)  TX bytes:78782 (76.9 KB)

--------------------------------------------------------------

**Resultado lspci:**
kamel@KameL:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


Resultado de dmesg|grep -i eth7:
kamel@KameL:~$ dmesg|grep -i eth7
[   42.643644] udev: renamed network interface eth0 to eth7
[   82.991855] eth7: no IPv6 routers present
[  225.294853] eth7: no IPv6 routers present
[  794.094988] eth7: no IPv6 routers present

--------------------------------------------------------------

**Archivo /etc/network/interfaces:**
auto lo
iface lo inet loopback


iface eth0 inet static
address 201.231.156.155
netmask 255.255.255.0
gateway 201.231.156.1

auto eth1
#iface eth1 inet dhcp


#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


auto eth0

iface eth1 inet static
address 201.231.156.155
netmask 255.255.255.0
gateway 201.231.156.1

iface eth2 inet dhcp
address 201.231.156.155
netmask 255.255.255.0
gateway 201.231.156.1

auto eth2



iface eth3 inet dhcp

auto eth3

iface eth4 inet dhcp
address 201.231.156.255
netmask 255.255.255.0
gateway 201.231.156.1

auto eth4

iface eth7 inet dhcp
address 201.231.218.87
netmask 255.255.255.0
gateway 201.231.218.1

auto eth7


--------------------------------------------------------------

Hago ping a esta dirección 200.45.191.35 y no da resultados.

---

### Post by faktorqm on 2008-07-10
me da tooooda la sensacion, de que no tenes la placa puesta en dhcp, mejor dicho, la tenes puesta pero no te lo esta tomando. Intenta desenchufar el cable, volverlo a enchufar, y probar de setear un ip cualquiera y luego volver a poner en dhcp, quiza funcione. Si en win te anda y en ubu no, descarta cualquier problema de modem/cable/fibertel. Lo de los paquetes no tiene nada que ver. Salu21

---

### Post by KameL on 2008-07-10
> **faktorqm said:**
> me da tooooda la sensacion, de que no tenes la placa puesta en dhcp, mejor dicho, la tenes puesta pero no te lo esta tomando. Intenta desenchufar el cable, volverlo a enchufar, y probar de setear un ip cualquiera y luego volver a poner en dhcp, quiza funcione. Si en win te anda y en ubu no, descarta cualquier problema de modem/cable/fibertel. Lo de los paquetes no tiene nada que ver. Salu21

Ya probé eso y no funciona :(

---

### Post by santiagoward2000 on 2008-07-10
> **KameL said:**
> Ya probé eso y no funciona :(

¿Probaste si anda en Windows? Para ver si no es un problema de Fiber.

---

### Post by KameL on 2008-07-10
En windows si tengo internet, configurado para que recupere datos como IP y DNS's automáticamente (DHCP). El problema es con Ubuntu.

---

### Post by faktorqm on 2008-07-10
A un amigo mio le pasaba lo mismo con fibertel, pero sólo cuando se pasaba de win a lin o viceversa. Cada vez que cambiaba de SO tenia que apagar y volver a prender el modem. 

Otra cosa que se me ocurre es que tengas los dns's mal puestos, fijate de llamar a fibertel o buscar las direcciones dns's de ellos y dejalas fijas en el ubuntu, de manera de tener solo la ip dinamica, y los dns estaticos. Eso quiza funcione. Salu2!!

---

### Post by sergiom99 on 2008-07-10
Te dejo mis DNS de Fiber.

200.49.130.29 
200.49.130.28  

pregunta a validar con alguien con mas idea: esta bien que tenga tantas ethx en el /etc/network/interfaces ??
Si limpia todo eso, se vuelve a generar?

---

### Post by KameL on 2008-07-11
Listo... me cansé. Ahora mismo estoy descargando la última versión del LiveCD para reinstalar todo y no tener que actualizar manualmente. Al parecer el problema ocurrió durante la instalación, por un corte de la conexión. Quizás eso causó este y otros errores que tengo en Ubuntu.
Gracias a todos por la ayuda.
Ya me van a ver de nuevo preguntando :lolflag:

---

### Post by KameL on 2008-07-17
Pues les comento que descargué la última versión (8.04.1) desde el sitio oficial, lo quemé, lo instalé, y nada... sigue con el mismo problema :mad:
Al parecer, esta versión de Ubuntu no me reconoce el modem, por lo que no me tira conexión.
¿Alguien se actualizó y sabe como solucionar este problema que me está poniendo ya de mal humor?

---

### Post by faktorqm on 2008-07-17
A ver, no te tiene que "reconocer" el modem, por que es un dispositivo ethernet mas, ese no es el objetivo que perseguimos. El modem anda, el cable anda y la placa de red anda por que te anda en windows. Sólo te quedan 2 opciones, que es, o que fibertel no soporta "linux" (no es tan descabellado como lo lees... sino preguntale a beuno) o que tenes mal configurado el Ubuntu. Yo me inclino mas por la segunda, que se yo, una vez que se agote bueno, llama a fibertel y reclama! Salu2!

---

### Post by FlyerDie on 2008-07-17
Porque tenes tantas interfaces de red declaradas?? :confused:
Siempre tuviste eth7?
Otra de las cosas que me llama poderosamente la atencion es que si estamos hablando de la misma maquina, tengas diferentes MAC Address en window$ que en Linux :-k, ya que la MAC es la direccion FISICA del dispositivo de red y no una direccion logica a la cual puedas cambiar alegremente (la MAC la podes cambiar desde el BIOS de la maquina siendo una integrada NVIDIA, pero no viene al caso).

Viendo un poco mas en profundidad:

```
Resultado de dmesg|grep -i eth7:
kamel@KameL:~$ dmesg|grep -i eth7
[ 42.643644] udev: renamed network interface eth0 to eth7
[ 82.991855] eth7: no IPv6 routers present
[ 225.294853] eth7: no IPv6 routers present
[ 794.094988] eth7: no IPv6 routers present
```
Tenes levantado IPv6? sacalo...tambien saca todas las interfaces escepto eth0, empeza por ahcer limpieza de cosas que estan demas, y a eth0 ponela en auto, porque tenes un lindo berenjenal que en una parte le decis que este estatica....:popcorn:

---

### Post by KameL on 2008-07-17
> **faktorqm said:**
> A ver, no te tiene que "reconocer" el modem, por que es un dispositivo ethernet mas, ese no es el objetivo que perseguimos. El modem anda, el cable anda y la placa de red anda por que te anda en windows. Sólo te quedan 2 opciones, que es, o que fibertel no soporta "linux" (no es tan descabellado como lo lees... sino preguntale a beuno) o que tenes mal configurado el Ubuntu. Yo me inclino mas por la segunda, que se yo, una vez que se agote bueno, llama a fibertel y reclama! Salu2!
Hoy voy a llamar y preguntar, de paso les digo que me pasen las DNS.
Con respecto a la configuración de Ubuntu, ¿qué es lo que tendría que configurar? ¿cómo se hace? Yo no toqué absolutamente nada, hice una instalación limpia desde 0 con el LiveCD oficial. Apenas terminó de instalarse, probé si tenía internet, y no. Lo único que toqué son las configuraciones de red para ver si podía arreglarlo, pero tampoco funciona.

PD: El problema no creo que sea Fibertel vs. Ubuntu, ya que con la versión 7.04 tenía internet.

---

### Post by FlyerDie on 2008-07-17
descarta totalmente el tema de que "Fibertel no soporte linux"..el modem que tenes y los que siempre tuvo fibertel (com21, motorola, webstar,etc) siempre fueron compatibles con cualquier cosa ya que son un dispositivo de red SIN DRIVERS...es lo mismo que te digan que un switch/hub/router no sea compatible con un sistema operativo X... 

Chequea el tema de porque tenes tantos dispositivos de red (eth) levantados, saca todos menos el eth0 y deja el archivo interfaces


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

OBVIAMENTE luego de hacer esto tambien resetea el modem por las dudas (desenchufa conta hasta 10 y volve a enchufar la energia)

Y explicame el tema de las MAC porque la verdad no se si estas con 2 maquinas o con una...y porque tenes dos MACs distintas...

---

### Post by KameL on 2008-07-17
> **FlyerDie said:**
> descarta totalmente el tema de que "Fibertel no soporte linux"..el modem que tenes y los que siempre tuvo fibertel (com21, motorola, webstar,etc) siempre fueron compatibles con cualquier cosa ya que son un dispositivo de red SIN DRIVERS...es lo mismo que te digan que un switch/hub/router no sea compatible con un sistema operativo X... 

Chequea el tema de porque tenes tantos dispositivos de red (eth) levantados, saca todos menos el eth0 y deja el archivo interfaces


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

OBVIAMENTE luego de hacer esto tambien resetea el modem por las dudas (desenchufa conta hasta 10 y volve a enchufar la energia)

Y explicame el tema de las MAC porque la verdad no se si estas con 2 maquinas o con una...y porque tenes dos MACs distintas...

Es una sola PC conectada directamente al cablemodem con conexión por ethernet. Cada vez que hacía algo de configuración de red, o reiniciaba la PC, me cambiaba el número de eth, por eso tenía tantas. Ahora que reinstalé Ubuntu me aparece directamente eth7.
Editando el archivo interfaces, poniendole eth0, ¿debería quedar fijo este número?

---

### Post by FlyerDie on 2008-07-17
> **KameL said:**
> Es una sola PC conectada directamente al cablemodem con conexión por ethernet. Cada vez que hacía algo de configuración de red, o reiniciaba la PC, me cambiaba el número de eth, por eso tenía tantas. Ahora que reinstalé Ubuntu me aparece directamente eth7.
Editando el archivo interfaces, poniendole eth0, ¿debería quedar fijo este número?

Lo ideal es que si tenes solo una interfaz, tengas solo una declarada, asi no te genera desorden a la hora de chequear configuracion ;)
hace lo que te comente, de editar el archivo de interface y dejar solo eth0 con las lineas que te pase, el resto volalo.

---

### Post by faktorqm on 2008-07-18
Lo de las MAC's, segun tengo entendido, es asi, en la mayoria de los chipsets de hoy, le podes poner la que vos queres. De hecho, cuando vos mandas un paquete tira tu mac origen en el encabezado, pero vos le podes setear lo que queres, por defecto, tiene la del fabricante, pero si vos le especificas otra que vos quieras por software (que a su vez actua sobre el chipset) mandas el paquete con esa nueva MAC. Lo unico que cada vez que lo haces tenes que desenchufar el cable de red y volverlo a enchufar y ya. Hay un programa para que se llama "macchanger" que lo hace.

```

faktorqm@the-edge:~$ aptitude search macchanger
p   macchanger                      - utility for manipulating the MAC address o
p   macchanger-gtk                  - a GTK+ interface for GNU/MACchanger       
faktorqm@the-edge:~$

```

Salu2!!

---

### Post by KameL on 2008-07-18
Bueno, aún no probé lo que mencionaron en el post nº15 y 16, pero acabo de comunicarme con Fibertel y me dieron los DNS, los cuales son:
200.49.130.20 ~ 200.49.130.34
-Todo el rango desde el .20 hasta el .34.
-Todos los pares son primarios, los impares son secundarios.

¿ayuda de algo este dato?

---

### Post by FlyerDie on 2008-07-18
no...para nada...:lol: pero para tener en cuenta por si se me joden los DNSs de Ciudad.
hace lo que te pasamos antes, no pierdas mas el tiempo con los DNSs ;)

---

### Post by dieterxp on 2008-10-11
[FONT="Verdana"][SIZE="2"]Se que el post es viejo, pero si seguis con el mismo problema es porque bajo windows tenes declarada una macaddr distinta a la que tenes bajo linux, en algun momento debiste haber cambiado la mac en windows porque ubuntu por defecto te toma la de la placa fisica.

Por los datos que pasaste, 00 13 8F D0 40 B5 es la direccion fisica que tenes configurada bajo windows, entonces tenes que hacer esto en una ventana de terminal:
```
[B]sudo ifconfig eth7 down
sudo ifconfig eth7 hw ether 00:13:8F:D0:40:B5
sudo ifconfig eth7 up[/B]
```

Si con esto te funciona bien para dejar el cambio como permanente para cada vez que reinicies la pc tenes que abrir la ventana de terminal y poner lo siguiente:
```
**sudo gedit /etc/init.d/bootmisc.sh**
```

y al final del archivo agregale:
```
[B]##Cambio permanente de macaddr para eth7
ifconfig eth7 down
ifconfig eth7 hw ether 00:13:8F:D0:40:B5
ifconfig eth7 up[/B][/SIZE][/FONT]
```

---

### Post by sebastianabate on 2008-10-12
¿Puede ser que hayas estado probando con otras placas de red? ¿O cambiando la placa que tenés de ranura? Porque me parece muy raro que tengas la placa configurada como eth7.
 
Hacé esto, primero hacé un backup de los archivos que vas a modificar
 
```
 
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persisten-net.rules.orig
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
sudo cp /etc/resolv.conf /etc/resolv.conf.orig

```
 
Después desenchufá el modem de fibertel por 30 segundos y volvelo a enchufar **(NO DEJES DE HACER ESTO)**
 
Ahora editá el archivo /etc/udev/rules.d/70-persistent-net.rules y comentá todas las líneas que tenga.
 
```
 gksudo gedit /etc/udev/rules.d/70-persisten-net.rules
```
 
En mi máquina el archivo está así
 
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.
# PCI device 0x13f0:0x0200 (sundance)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:08:54:31:f2:4c", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:8c:a5:77:13", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```
 
Y tendría que quedar así
 
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.
# PCI device 0x13f0:0x0200 (sundance)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:08:54:31:f2:4c", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8168 (r8169)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:8c:a5:77:13", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```
 
después editá el archivo /etc/network/interfaces
 
```
gksudo /etc/network/interfaces
```
 
para que quede así
 
```
 auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp
```
 
y por último modificá el archivo /etc/resolv.conf
 
```
gksudo /etc/resolv.conf
```
 
y borrá todo lo que tenga adentro (que quede vacío).
 
Ahora reiniciá la máquina y verificá con un ifconfig que tengas una ip pública asignada (la IP tiene que empezar con cualquier número que no sea 169.)
 
Después verificá que el archivo /etc/resolv.conf contenga varias entradas (seguro que va a tener dos o tres líneas con los DNS's de Fibertel)
 
```
cat /etc/resolv.conf
```
 
y ahora sí probá haciendo un ping a [www.yahoo.com.ar]("http://www.yahoo.com.ar") para ver si todo funciona.

---

### Post by ramiro_md on 2008-10-13
Gente, tengo un problema similar. En estos momentos escribo desde Debian porque en Ubuntu no me anda más internet. A eso de las 2 y pico de la tarde de hoy (lunes 13 de octubre) me quede sin internet en Ubuntu.
Al principio dije "malditos, flash se cayo ¬¬", pero cuando reinicie en Debian e internet anda dije "mmm..que extraño :P". Cuestión, nunca configure internet en Ubuntu, siempre conecte el cable de red y andaba. Me dirijí a la config de red y me fijé la opción de conexión cableada (uso cablemodem y un router) y en las propiedades estaba en "modo itinerante", lo cambié por dhcp y seguía sin andar..reinicié el sistema e igual no andaba. Volví a la opción "modo itinerante" y nada...no sé mucho sobre esto de redes.
Ahora leyendo en este thread me dieron la idea del DNS.Asique lo voy a probar.
SI sirve de ayuda, en estos días estuve jugando con firestarter, pero ayer creo lo desinsitale...al principio pensé que habían quedado algunas reglas en iptables jodiendo, pero como me pude conectar en una ocasión lo descarté.
Bueno espero solucionarlo con lo de la DNS, caos contrario volveré por estos pagos a ver el thread.
Un saludo.

edito: desde el livecd si tengo internet

---

### Post by ramiro_md on 2008-10-13
La idea de los DNS no funcionó:(

---

