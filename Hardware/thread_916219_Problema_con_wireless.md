---
title: "Problema con wireless"
date: 2008-09-10
forum: Hardware
---

### Post by felipemaxim on 2008-09-10
En una toshiba satellite L300 instalé ubuntu 8.04 y windows Xp. XP puede conectarse a la red inalámbrica automáticamente, pero ubuntu no puede conectarse. 
Seguí los pasos de la ayuda de ubuntu y en uno de los comandos (creo que el iwconfig) me tira "no wireless extensions" para las placas de red. 
Tampoco parecen ser el problema los controladores de la red, porque el sistema dice que está usando automáticamente los de Windows. ¿Alguna idea de qué puede estar funcionando mal?

---

### Post by felipemaxim on 2008-09-10
Postée esto en el foro de comunidad, pero me parece que este es el lugar para la pregunta:

En una toshiba satellite L300 instalé ubuntu 8.04 y windows Xp. XP puede conectarse a la red inalámbrica automáticamente, pero ubuntu no puede conectarse.
Seguí los pasos de la ayuda de ubuntu y en uno de los comandos (creo que el iwconfig) me tira "no wireless extensions" para las placas de red.
Tampoco parecen ser el problema los controladores de la red, porque el sistema dice que está usando automáticamente los de Windows. ¿Alguna idea de qué puede estar funcionando mal?

---

### Post by sergiom99 on 2008-09-10
escribi el comando lspci en una consola y postea la salida.
con eso vemos que placa tenes y podemos buscar como configurarla.
suerte.

---

### Post by luks911 on 2008-09-10
Buenas,
Lo que sucede es que Ubuntu no detecta la placa wifi. Para poder darte una mano y ver cómo hacerla andar es necesario saber qué placa es. Si lo sabés, postealo; si no, en una terminal tirá un

```
lspci
```

Eso va a devolverte el listado de los componentes conectados en puertos pci (si no me equivoco en la teoría), entre ellos el wifi. El resultado de ese comando pegalo acá y vemos. 
Creo que el comando más específico es 

```
lspci |grep Wireless
```

pero cualquiera de los dos va a servir.

Saludos

Recontra OT: el editor de la revista Maxim Argentina se llama Felipe Viñals, ¿algo que ver?

---

### Post by sergiom99 on 2008-09-10
yo te habia respondido en el otro. ademas del lspci, postea el resultado del comando:
```
sudo lshw -C network 
```

---

### Post by luks911 on 2008-09-10
> **sergiom99 said:**
> yo te habia respondido en el otro[/code]

Che, perdón. Leí este primero y no me avivé de ir a buscar el otro post que era anterior.

---

### Post by felipemaxim on 2008-09-10
******! No me imaginé que era tan famoso. Pero bueno, también debés ser lector para haberme sacado el nick. Un honor, en todo caso y gracias por responder. El resultado del comando lspci es

felipe@felipe-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

El de sudo lshw -C network es:

  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:39:11:be
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

---

### Post by luks911 on 2008-09-10
En cuanto al wifi, la línea que dice 
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
es la que te indica la placa. Es una Atheros AR5007EG (lo sé porque tengo la misma en una Compaq).
Abajo copio, pego y adapto un tutorial que dejé en Ubuntu-es y [acá]("http://ubuntuforums.org/showpost.php?p=5577447&postcount=13") dejo algo parecido y un poco más extenso hecho por faktorqm.

1) Desinstalás los drivers Madwifi que ya tengas. Para eso en Synaptics eliminá el paquete linux-restricted-modules. Esto es lo que hace que Ubuntu ya esté usando los controladores, aunque es una versión que no sirve para tu placa.

2) Instalar los paquetes para compilar, en una terminal:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

3) Bajá [este archivo]("http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz") ([http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)), es el driver. Descomprimilo donde quieras con un clik derecho y "extraer aquí". Te va a crear una carpeta con el nombre madwifi-hal-0.10.5.6-r3861-20080903.

4) En una terminal entrá a la carpeta del driver, si querés antes podés cambiarle el nombre desde nautilus (por ejemplo, ponerle madwifi) para que sea más sencillo.

```
cd /home/tu_usuario/madwifi-hal-0.10.5.6-r3861-20080903
```

5) Compilás con

```
make
```

6) Instalás con

```
sudo make install
```

En estos dos pasos dale tiempo a que terminen los procesos, que pueden tardar un par de minutos.

7) Insertás el nuevo módulo en el kernel con

```
sudo modprobe ath_pci
```

Con eso ya debería estar funcionando el wifi.

8 ) Para que se cargue el módulo en cada inicio, editás el archivo modules así

```
sudo gedit /etc/modules
```

Y agregás una línea que diga

```
ath_pci
```

Si hay otra línea que dice ath_hal, comentala, o sea que le agregás # adelante, o directamente la borrás.
Eso es todo. Ah, una aclaración, es muy probable que la luz del wifi quede naranja aún cuando esté funcionando.

Cualquier error o inconveniente, volvé a preguntar.

Un saludo

---

### Post by felipemaxim on 2008-09-11
Impresionante! Muchas gracias. :-({|= Seguimos el offtopic por el otro canal.

---

### Post by luks911 on 2008-09-11
Genial, me alegro de que haya servido.

Saludos

---

### Post by ocelotma on 2009-03-02
espero que me puedan ayudar tengo ya 2 semanas con los ojos inchados de tanto foro visto y tambien que me e dormido a las 6 am jajajaja y no e podido solucionar esto :-(

Esta es la historia

Tengo una Compaq HP nx9010

Tenia instalado windows XP y solo con el service pack 2 podia conectarme a la red inalambrica de mi casa ya que ingresaba la contraseña de la Wireless y nada.

me pasa algo similar con Ubuntu y Kubuntu ya que instale ambos por creer que seria la version, (ya se que la diferencia es solo el escritorio lo descubri hace poco), bueno instale Ubuntu y Kubuntu y el problema de Wireless sigue ya que ingreso la contraseña que es (panchitopanchon) por asi decirlo, intenta accesar a la Wireless pero no lo logra al editar la cuenta pues veo que en lugar de que la contraseña sea (panchitopanchon) me pone algo asi (65423654126534162534615234615243651243652341) la seguridad es por WAP normal no el enterprice, ademas que note que en lufgar de tener detectado el controlador Intel Pro/set lo detecta como un Broadcom43 o algo asi,

la otra es que la tarjeta AGP es una ati y Kubuntu me da la resolucion de 1024 y en windows podia poner algo mas pero no importa siempre y cuando me conecte a la inalambrica.



ya tengo un buen rato en esto y no quiero regresar a XP estoy pensando en regresar a 2000 para mas o menos igualar el performance de Kubuntu pero les soy franco me encanto Linux y no quisiera regresar al Lado obscuro de la fuerza.


Saludos y espero puedan ayudarme soy principienta en esto y quiero aprender


si alguien tiene un manual de Linux que pueda facilitarme para iniciarme en esto que esta genial se los agradeceria ya que tengo dificultades en comprender los comandos del sistema



'Linux para Mexico o Mexico para Linux Excelente opcion'

---

