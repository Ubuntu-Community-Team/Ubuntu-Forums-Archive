---
title: "problemas ubuntu 8.10 sin conexion a internet"
date: 2009-03-22
forum: Hardware
---

### Post by cesarito on 2009-03-22
***Hola a todos***
Instale ubuntu 8.10 para probarlo y aprender, hasta ahora todo parece lindo pero no tengo conexion a internet mother Asus P5SD2-VM
Intel Core 2 Duo Placa red SiS 191 Gigabit Ethernet Controller (PHY: Atheros AR8012)	PCI. no puedo conectarme servidor Arnet.Agradezco de antemano:(

---

### Post by Hei Ku on 2009-03-22
Como te conectas a Arnet? Es un modem USB o Ethernet?

Y necesitamos la salida del comando lspci, para identificar bien la placa de red.

---

### Post by cesarito on 2009-03-23
Gracias Hey Ku por contestar; me conecto con un modem dual HUAWEY Smartax MT 882 conectado a la placa de Ethernet.
El comando ispci me costo un peru pasarlo al win pero aqui esta:
00:00.0 Host bridge: Silicon Integrated Systems [SiS]  671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS]  Sis AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS]  SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS]  5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS]  USB 1.1 Controller (rev of)
00:03.1 USB Controller: Silicon Integrated Systems [SiS]  USB 1.1 Controller (rev of)
00:03.3 USB Controller: Silicon Integrated Systems [SiS]  USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display  Adapter (rev 10)  
 ESPERO ESTE BIEN GRACIAS!!!!!:o

---

### Post by hictio on 2009-03-23
Como es el setup de la red? Es decir, tenés un router entre el modem del proveedor a internet, o conectás directo de este a la máquina?
Si este es el caso, y tenés más de una máquina, tené en cuenta que tenés que apagar el modem unos minutos cuando pasás el cable de red de una máquina a otra (para que libere el MAC de la tarjeta de red, y renueve la dirección IP correctamente)

---

### Post by pablo.s on 2009-03-23
Ejecutá lo siguiente en una terminal: **sudo pppoeconf**
y seguí las instrucciones. Te va a pedir usuario y contraseña
Espero que te sirva. Saludos..

---

### Post by cesarito on 2009-03-23
Gracias hictio y pablo.s por sus sugerencias y respondo:
tengo el modem antes nombrado conectado directo a la placa de red, por ende directo a la maquina, con inicio dual de win xp y ubuntu, en win me conecto bien, de echo estoy buscando ayuda x el win, pero ubuntu no me conecta.En cuanto a **sudo pppoeconf**me dice que no estoy conectado, sepan que conozco casi nada de linux pero busco mucho x la red y trato de aplicar lo que leo, espero algien le encuentre la vuelta al tema:(

---

### Post by EnriqueK on 2009-03-24
Es probable que sea problemas de driver que aún no es soportado por Intrpid, tuve un caso similar con Ubuntu 8.04 que no podía conectar a Internet, pero al probar con la versión 8.10, funcionó perfectamente, el equipo también consta de una mobo ASUS , pero si no querés esperar a la nueva versión que saldrá pronto, fijate si en el CD de drivers que viene con la mobo  figuran drivers para LAN en Linux, de ser así vas a tener que compilar y para ello vas a tener que instalar el metapaquete "build essential" y para ello vas a tener que habilitar el repositorio del disco de instalación, tarea tal vez algo complicada para un novato, pero averiguando en google vas apoder hacerlo sin problemas.

---

### Post by cesarito on 2009-03-24
Gracias Enriquek si es asi me veo mal, veremos q pasa salu2

---

### Post by cesarito on 2009-03-26
Y como actualizo sin internet en ubuntu se puede bajar con win? cuando sale le nueva version? gracias:confused:

---

### Post by EnriqueK on 2009-03-26
Si estás usando Intrepid 64 bits ( a ver que te sale si ponés en terminal **uname -a**), te puedo pasar un archivo .tar para que puedas clonar los índices de repositorios mediante el uso de un pequeño Script que también te lo puedo subir a Rapidshare . Luego, con los índices en tu equipo puedes actualizar e instalar todo lo que quieras usando Synaptic con el que podrás generar un Script de decargas de paquetes que podrás usar en win para efectuarlas. 
La nueva versión de Ubuntu saldrá por el 20 de Abril.

---

### Post by cesarito on 2009-03-26
Otra vez gracias Enriquek por tu interes, mi Ubuntu es de 32 bits no entiendo tu propuesta pero me interesa todo lo q sea aprender Linux, asi que me diras como bajo esos script (no se que son) pero en interenet hay mucha informacion,es cuestion de buscarla,¿esto me serviria para solucionar mi problema? pues me gusto el Ubuntu y no quisiera esperar para actualizarlo, saludos:P

---

### Post by EnriqueK on 2009-03-27
Si tenés a alguien conocido que use tu misma versión de Ubuntu, podrías pedirle que corra en su instalación el siguiente Script que se crea abriendo por ejemplo gedit y copiar el siguiete texto y lo guardas con el nombre de **origen.sh**

```
#!/bin/sh

sudo apt-get update
cd /tmp
sudo tar -cvf lists.tar /var/lib/apt/lists
sudo tar -cvf sourceslistd.tar /etc/apt/sources.list.d
sudo tar -cvf sourceslist.tar /etc/apt/sources.list
```

Al correr este Script se crean en la carpeta temporal del sistema /tmp copias en formato .tar sin comprimir de las carpetas y archivo necesarios para clonar los índices de repositorios. Si no encuestras a ningún conocido, podés correr el Live CD de instalación en otro equipo que pueda reconocer la conexión a internet creas mediante Synaptic la lista de repositorios o elige el método que quieras para generar los índices de repositorios en el Live CD y cuando termines aplicas el Script puesto arriba y seguidamente copias en por ejemplo un pendrive los archivos .tar que generó la ejecución del Script.
Una vez te encuentras con el equipo sin conexión a internet copias al directorio /tmp los archivos .tar creados anteriormente y ejecuta este otro Script que lo creasa previamente según lo exlicado antes 
```
#!/bin/sh
sudo rm -Rf '/etc/apt/sources.list.d' '/etc/apt/sources.list'
sudo rm -Rf '/var/lib/apt/lists'
cd /tmp
sudo tar -xvf lists.tar --directory /
sudo tar -xvf sourceslistd.tar --directory /
sudo tar -xvf sourceslist.tar --directory /
sudo apt-get update
```

Este Script tiene sus peligros al usarlo por que si no encuentra los archivos .tar dentro de su directorio /tmp , no va a poder poner los archivos clonados del otro equipo , por esta razón a este Script que llamaremos **destino.sh **, solo lo debes ejecutar en el equipo que no tiene internet.
Finalmente para ejecutar cualquiera de estos Script, abre terminal, pones **sh** dejas un espacio y **arrastras al terminal el Script que quieras ejecutar** --> Enter y ya.
Lo que queda es usar Synaptic para instalar paquetes de actualizaciones y programas, pero esa explicación la dejaría para mas adelante, por que aunque es simple, se hace un poco largo de detallar en palabras y además lo realmente crítio es el clonar los índices de repositorios, todo lo demás es simple y rutinario.

---

### Post by faktorqm on 2009-03-27
Hola, si te reconoce la placa de red, (postea el comando "ifconfig" sin comillas) directamente pone en modo router el modem de adsl que tenes (que se puede) y listo el pollo, que el tipo se conecte automaticamente, eso seguro te soluciona el problema. Saludos!

---

### Post by cesarito on 2009-03-28
gracias faktorqm x tu ayuda pero no entiendo mas nada se me ha hecho un lio como sabras soy nuevo en linux, el comando ipconfig no me da nada, si pudiras darme mas detalles te agradeceria mucho saludos
:confused:

---

### Post by Hei Ku on 2009-03-28
iFconfig, no ipconfig como en el otro.

```

ifconfig


```

---

### Post by cesarito on 2009-04-01
Gracias Hey Ku aqui esta el ifconfig:
eth0

Link encap:Ethernet direccionHW 00:23:54:ba:f9:46
ARRIBA DIFUSION MULTICAST MTU:1500 Metrica:1
RX packets:1 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000
RX bytes:60 (60 B) TX bytes:0 (0.0 B)
Interrupcion:19 Direccion base: 0xdead

lo

Link encap:B ucle local
inet deireccion:127.0.0.1 Mascara:255.0.0.0
ARRIBA LOOPBACK CORRIENDO MTU:16436 mETRICA:1
RX packets:246 errors:0 dropped:0 overruns:0 frame:0
TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:0
RX bytes:15488 (15.4 KB) TX bytes:15488 (15.4 KB)

espero este bien y sirva saludos

---

### Post by cesarito on 2009-04-11
Y? al fin y al cabo nadie sabe de esto?:confused:

---

### Post by Hei Ku on 2009-04-11
La placa de red te la reconoce. Con poner tu modem en modo router deberia salir andando solita.

---

### Post by cesarito on 2009-04-12
Gracias hey Ku me podra decir alguien :p:pcomo hago para ponerlo en red?

---

### Post by cesarito on 2009-04-13
Perdon error mio pregunto como lo pongo como router;)?

---

### Post by EnriqueK on 2009-04-14
Si te reconoce la tarjeta de red, no implica necesariamente que tenga instalado el driver, a mi me pasó lo mismo con otra ASUS , no pude instalar Hardy por que no podía conectarme a Inet, pero al intentar con Intrepid,funcionó perfectamente la conexión.
Probá con actuañizar el kernel siguiendo lo que indica este thread
 [http://ubuntuforums.org/showthread.php?t=1124579](http://ubuntuforums.org/showthread.php?t=1124579)
Sino esperá uno 10 días y vas a poder descargar la versión 9.04
Si después de haber probado con lo anterior no funciona, te recomiendo cambiar de distro, probá con fedora que al parecer ASUS y Red Hat hacen buenas migas.

---

### Post by cesarito on 2009-04-19
Ohh shet](*,) segun sugerencia de EnriqueK. instale fedora 10 y PEOR nohay entorno grafico ni red, lei x alli que las placas sis no andan en linux por exclusividad con microsoft.esperare el nuevo ubuntu e intentare por ultima vez pero estoy decepcionado , pues dicen que linux es lo mejor hasta ahora solo problemas Y QUIERO APRENDER LINUX DESDE LINUX!!! asi que si el nuevo ubuntu no me anda buscare AL CHAPULIN COLORADO, GRACIAS AMIGOS POR SU AYUDA

---

