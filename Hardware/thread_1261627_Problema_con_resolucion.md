---
title: "Problema con resolucion"
date: 2009-09-09
forum: Hardware
---

### Post by facurdo on 2009-09-09
Buenas!
Antes que nada soy usuario nuevo, solo 2 dias con ubuntu 9.04 en mi disco y estoy totalmente embobado con el jajajaj.
Anda todo perfecto :P con la excepcion de la resolucion que es de 800x600 cuando mi monitor soporta hasta 1024x768.

Probe modificando el archivo xorg.conf pero nada :( es mas ahora ni me detecta el monitor.

Datos:
Mother Asrock 775i65g (utilizo todos sus puertos inclusive la placa de video)
Monitor Benq v551 15 pulgadas

No se si es relevante mas datos de la pc.
Si alguno puede ayudarme con esto, se los agradeceria mucho, me esta matando la letras el tamaño de mi mano :(

Saludos!

---

### Post by guillermolisi on 2009-09-09
> **facurdo said:**
> Buenas!
Antes que nada soy usuario nuevo, solo 2 dias con ubuntu 9.04 en mi disco y estoy totalmente embobado con el jajajaj.
Anda todo perfecto :P con la excepcion de la resolucion que es de 800x600 cuando mi monitor soporta hasta 1024x768.

Probe modificando el archivo xorg.conf pero nada :( es mas ahora ni me detecta el monitor.

Datos:
Mother Asrock 775i65g (utilizo todos sus puertos inclusive la placa de video)
Monitor Benq v551 15 pulgadas

No se si es relevante mas datos de la pc.
Si alguno puede ayudarme con esto, se los agradeceria mucho, me esta matando la letras el tamaño de mi mano :(

Saludos!
Faltaria que nos digas algo fundamental: Que placa de video estas usando ?

Edit: En las caracteristicas de la placa solo figura esto:
> **Gráficos**- Gráficos 2 Integrados de Intel® Extreme
                          - DirectX 8.0
                          - Memoria compartida máximo de 96MB pero nada dice del chip que usa para video.

---

### Post by facurdo on 2009-09-09
POr lo menos hasta ahora no tengo ningun placa de video usando, solo la que esta onboard
y los unicos datos que encontre de esta son lo que vos indicastes

                      
> **Gráficos**- Gráficos 2 Integrados de Intel® Extreme
                           - DirectX 8.0
                           - Memoria compartida máximo de 96MB

---

### Post by Hei Ku on 2009-09-09
Pone lspci en una terminal y copia aca lo que te salga.

---

### Post by facurdo on 2009-09-09
> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)MIl disculpas si me piden que haga funciones basicas, soy un novato

---

### Post by facurdo on 2009-09-09
Encontre esto, tal vez sirve pero me maree un poco, (son las 4 de la matina jajaja)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/317457](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/317457)

[http://ubuntuforums.org/archive/index.php/t-1107844.html]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/317457")
en este ultimo link probe con esto pero sigue igual :(

> sudo aptitude install xserver-xorg-video-intel libdrm-intel1

---

### Post by Hei Ku on 2009-09-09
Los driver de Intel tienen un problema con el kernel de Jaunty. La solucion es actualizar a un kernel mas nuevo, pero eso depende de si te animas a hacerlo o no.

[http://ubuntuforums.org/showpost.php?p=7510004&postcount=16](http://ubuntuforums.org/showpost.php?p=7510004&postcount=16)

---

### Post by facurdo on 2009-09-09
> **Hei Ku said:**
> Los driver de Intel tienen un problema con el kernel de Jaunty. La solucion es actualizar a un kernel mas nuevo, pero eso depende de si te animas a hacerlo o no.

[http://ubuntuforums.org/showpost.php?p=7510004&postcount=16](http://ubuntuforums.org/showpost.php?p=7510004&postcount=16)

Animar me animo seguro, todo con tal de desplazar a windows de las pc en mi casa!
Me recomendas algun tip para hacer esto?

---

### Post by facurdo on 2009-09-09
Instale lo 3 paquetes .deb y nada :(

Ahora tengo asi el xorg.conf
> Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
y yo antes lo tenia modificado de esta manera
> Section "Device"
Identifier "Intel 865G"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "BenQ V551"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Controller"
Monitor "BenQ V551"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection 

---

### Post by Hei Ku on 2009-09-09
Proba con ese xorg.conf anterior, a ver qué pasa.

---

### Post by facurdo on 2009-09-09
No, no pasa nada solo sigue en 800x600 y la pantalla se ve como ondulada para adentro (seguro eso es):
> HorizSync 28-51
VertRefresh 43-60

No se si es correcto, el monitor no tiene ningun dato y en internet encuentro diferentes rangos.

---

### Post by gmunioz on 2009-09-09
Hola fac....:

Edita tu xorg.conf y déjalo asi:


Section "Device"
Identifier "Intel 865G"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "BenQ V551"
Option "DPMS"
HorizSync 30-54
VertRefresh 50-120
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Controller"
Monitor "BenQ V551"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" 
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" 
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" 
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" 
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" 
EndSubSection
EndSection

---

### Post by facurdo on 2009-09-10
gmunioz, no me sirvio :S, ya lo habia probado eso antes, lo intente esta vez con el kernel actualizado 2.6.30.
[[IMG]http://img43.imageshack.us/img43/5059/pantallazopreferenciasd.th.png[/IMG]]("http://img43.imageshack.us/i/pantallazopreferenciasd.png/")

Estube revisando internet y varios tienen este problema, pero no hay una solucion fija, algunos tienen suerte y se les soluciona con cambiar una tonteria en el xorg.conf.
Espero que halla una solucion a esto, no me quiero ver obligado a comprar una placa de video que no necesito para poder usar Linux, es un tanto ironico hacer eso :(

---

### Post by Hei Ku on 2009-09-10
Probaste correr este comando?

sudo dpkg-reconfigure -phigh xserver-xorg


En la terminal intenta encontrar el modo de mas performance para tu placa.

---

### Post by facurdo on 2009-09-10
> **Hei Ku said:**
> Probaste correr este comando?

sudo dpkg-reconfigure -phigh xserver-xorg


En la terminal intenta encontrar el modo de mas performance para tu placa.

facurdo@FUbuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for facurdo: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090910150205
:(

EStube leyendo en algunos blogs y como me dijistes antes intel tiene problemas con linux que se soluciona en la salida de Ubuntu 10.0, pero tambien se puede corregir con la actualizacion de prieba del Kernel 2.6.30 (lo tengo puesto) hablaban de PPA o algo asi, la verdad no me tome el tiempo de investigar sobre todo. 
Encontre este link en ingles, ( [http://ubuntuforums.org/showthread.php?t=1130582&highlight=low+graphics+mode](http://ubuntuforums.org/showthread.php?t=1130582&highlight=low+graphics+mode) ) te da 3 opciones para los integrados de Intel.
¿CUal me conviene?¿sirve esa guia para mi problema de resolucion?

---

### Post by Hei Ku on 2009-09-10
Yo probarìa la configuracion optima que plantean en el thread.

---

### Post by facurdo on 2009-09-10
SEGUI LOS PASOS del link en la forma b (safe/optimal)
Se me instalaron dirvers de video intel, ati, nvidia, openchrome y no recuerdo cual mas

> Configurando nvidia-173-modaliases (173.14.16-0ubuntu2) ...
Configurando nvidia-180-modaliases (185.18.14-0ubuntu1) ...
Configurando nvidia-96-modaliases (96.43.10-0ubuntu2) ...
Configurando xserver-xorg-input-synaptics (0.99.3-2ubuntu5) ...
Configurando xserver-xorg-video-radeon (1:6.12.2-0ubuntu1~xup~1) ...
Configurando xserver-xorg-video-ati (1:6.12.2-0ubuntu1~xup~1) ...
Configurando xserver-xorg-video-nv (1:2.1.13-1ubuntu1~xup~1) ...
Configurando xserver-xorg-video-openchrome (1:0.2.903+svn741-1build1) ...

Configurando xserver-xorg-video-sisusb (1:0.9.1-1build1) ...
Configurando fglrx-modaliases (2:8.620-0ubuntu3~jaunty) ...


No aparecen los de intel (el que me corresponde) por que los instale desde la forma visual que aparece automaticamente.

Pero igual sigo con la resolucion de 800x600, y el archivo xorg.conf volvio a ser como estaba de un principio, siempre que hago algo vuelve como antes. :(

---

### Post by facurdo on 2009-09-10
estoy intentando actualizar la bios de la placa de video intel pero no logro instalarla.
cuando pongo en la terminal
> sudo apt-get install 915resolution
me dice esto:
> facurdo@FUbuntu:~$ sudo apt-get install 915resolution
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete 915resolution no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
E: El paquete 915resolution no tiene candidato para su instalación


link:[http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/)   
no les paso el de [http://ubuntuguide.org](http://ubuntuguide.org) por que va ser imposible encontrar esa parte jaja

Probe por el Gestor de Paquetes Synaptic, lo busque, aparece el nombre pero no me deja aplicarlo.

La verdad ya no se, esto de Linux me tiene bastante desepcionado, ya van 3 4 dias para arrelgar la resolucion... estoy sacando mas canas que con WIndows

---

### Post by josecuervo86 on 2009-09-10
Por lo que leo aca [0] ese paquete solo estuvo disponible en dapper (6.06) y hardy (8.04), no en jaunty (9.04)

[0] [http://packages.ubuntu.com/dapper/915resolution](http://packages.ubuntu.com/dapper/915resolution)

---

### Post by facurdo on 2009-09-10
> **josecuervo86 said:**
> Por lo que leo aca [0] ese paquete solo estuvo disponible en dapper (6.06) y hardy (8.04), no en jaunty (9.04)

[0] [http://packages.ubuntu.com/dapper/915resolution](http://packages.ubuntu.com/dapper/915resolution)


OK, todas malas entonces, me decepciono totalmente este sistema operativo
gracias Hei Ku por tu ayuda desinteresada!

---

### Post by guillermolisi on 2009-09-10
> **facurdo said:**
> OK, todas malas entonces, me decepciono totalmente este sistema operativo
gracias Hei Ku por tu ayuda desinteresada!
Si estas con esa sensacion de frustracion mi mejor consejo es que pruebes otras alternativas a Ubuntu y que elijas la que mas satisfaccion te genere.

Estos problemas existen en TODOS los sistemas operativos, sin excepcion alguna.
La diferencia es que en algunas implementaciones tanto de hardware como de software (no nos olvidemos que tratamos con un sistema en el cual el factor humano lo atraviesa completamente), este tipo de cosas se resuelven antes, en forma distinta, o mas tarde, dependiendo del empeño en encontrar la solucion que le pongan los desarrolladores del hardware, los del software y quien utiliza el sistema:el usuario.

Hay cada vez mas gente satisfecha, aun con problemas pendientes de ser resueltos, con Linux y particularmente Ubuntu en todo el mundo.

Los que hemos leido y respondido en este hilo tambien hemos pasado noches de insomnio, dias de frustracion, busqueda, bronca, miles de preguntas, etc. pero algo que no hicimos fue bajar lo brazos hasta lograr el objetivo.

La ventaja del software libre es que respeta tu libertad de decidir que es mejor para vos. Usala, es tu derecho, siempre.

---

### Post by facurdo on 2009-09-10
> La ventaja del software libre es que respeta tu libertad de decidir que es mejor para vos. Usala, es tu derecho, siempre. 	

PIenso igual que vos, no voy a volver a windows voy a seguir con este sistema operativo, pero la verdad no se muy bien lo que voy a hacer ahora, necesito cambiar la resolucion urgente ya que trabajo con imagenes (todavia no probe el gimp ni los software parecidos a photoshop), por suerte tengo una mac, pero no queria que fuera a terminar asi....

---

### Post by guillermolisi on 2009-09-10
> **facurdo said:**
> PIenso igual que vos, no voy a volver a windows voy a seguir con este sistema operativo, pero la verdad no se muy bien lo que voy a hacer ahora, necesito cambiar la resolucion urgente ya que trabajo con imagenes (todavia no probe el gimp ni los software parecidos a photoshop), por suerte tengo una mac, pero no queria que fuera a terminar asi....
Entonces no te presiones mas de la cuenta. Tomalo con mas calma que la solucion llegara, tarde o temprano estara ahi.

---

### Post by facurdo on 2009-09-10
> **guillermolisi said:**
> Entonces no te presiones mas de la cuenta. Tomalo con mas calma que la solucion llegara, tarde o temprano estara ahi.

Estube leyendo que en la version Ubuntu 10, va a estar solucionado los problemas con las tarjetas integradas de intel, son muchos los que estan como yo.

[stepiuvilkas]("http://ubuntuforums.org/member.php?u=899598") me recomendo que use Ubuntu 8.10 (Intrepid) que no tenia problemas con la resolucion, voy a intentar, de ultima compro una placa de video nvidia, la mas barata y que sirva para Ubuntu 9.04 =)

---

### Post by facurdo on 2009-09-11
UNa ultima consulta antes de cerrar este Thread.
Alguno sabe que version de Ubuntu o que otro linux no tenga este problema de resolucion con INtel?

Me recomendaron Ubuntu Intrepid, tal vez alguno sepa algo con respecto a esto con KUbuntu, suse, entre otros.

sALUTES!:D

---

### Post by pablo.s on 2009-09-11
En poco mas de un mes y medio
se lanza la siguiente versión de
Ubuntu, llamada Karmic Koala.
Esta versión tiene solucionados
bastantes problemas, entre ellos
este tema de las placas Intel, que
no solo atañe a Ubuntu ya que se
trata de una transición de una 
tecnologia a otra. De todas formas
con la actualización de núcleo y la
descarga de los drivers actualizados
se soluciona.
Hace unos meses realicé la [URL="http://ubuntuforums.org/showpost.php?p=7517680&postcount=1"]traducción
de un COMO[/URL] concerniente a este 
problema. Es probable que te sea de
utilidad.

---

### Post by Hei Ku on 2009-09-11
Podes probar con una alpha de Karmic Koala, solo como prueba. Despues es cuestion de esperar mes y medio  y  ya esta.

---

### Post by facurdo on 2009-09-11
> **Hei Ku said:**
> Podes probar con una alpha de Karmic Koala, solo como prueba. Despues es cuestion de esperar mes y medio  y  ya esta.

MIentras me como el garron de ver las letras de tamaño de una manzana ahahah, no puedo quedarme de brazos cruzados.

Recien instale Ubuntu 8.10, me aparecieron nuevas resoluciones variaciones de (800x600 y 600x400) jajaja pero no la que me interesa, :(, internet anda un poco mas lento....

Me esta dando dolor de cabeza xD

---

### Post by pablo.s on 2009-09-11
Te animás a seguir unas
instrucciones que te voy a dar?
Me interesa que puedas resolver
este problema lo mas pronto
posible.

---

### Post by facurdo on 2009-09-11
> **pablo.s said:**
> Te animás a seguir unas
instrucciones que te voy a dar?
Me interesa que puedas resolver
este problema lo mas pronto
posible.

Las que sean, no tengo problema, mientras aprendo un poquito mas de este sistema operativo =)

---

### Post by pablo.s on 2009-09-11
OK. En una terminal escribí
lo siguiente:

```
gksudo gedit /etc/X11/xorg.conf
```

Se va a abrir un programa
para editar textos con la
configuración del servidor X.
En la linea que diga "Device"
reemplazá lo que tenga por esto:

```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"
```

y luego salis de la sesión y
entrá nuevamente.
Esta es la primera parte.

---

### Post by facurdo on 2009-09-11
Hecho! =)
SI queres poner mas info en un solo post no hay drama, ya me estoy acostumbrando a todo esto

---

### Post by pablo.s on 2009-09-11
Sigamos: Otra vez abrí
una terminal y escribite esto:
(si te es más comodo copias
y luego pegas con CTRL+Shift+V)

```
[COLOR=Red]sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh[/COLOR]
```

```
[COLOR=Red]**[FONT=Droid Serif, serif]sudo chmod +x /usr/local/bin/fixmtrr.sh[/FONT]**[/COLOR]
```

Avisame cuando esté hecho
asi vamos a la parte más dificil.

---

### Post by facurdo on 2009-09-11
Listo!
cuando pongo en la temrinal esto:
> **[COLOR=Red][B][FONT=Droid Serif, serif]sudo chmod +x /usr/local/bin/fixmtrr.sh[/FONT]**[/COLOR][/B]
no pasa nada, directamente vuelve a mi nombre de usuario
> facurdo@facurdo:~$ sudo chmod +x /usr/local/bin/fixmtrr.sh
facurdo@facurdo:~$ 


---

### Post by pablo.s on 2009-09-11
Es asi. Lo que hace ese comando
es cambiarle los permisos de ejecución
al script que corrige un problema.
Al terminar todo el proceso te describo 
cada paso que hiciste. Ahora sigamos
que viene la parte que sea mas dificultosa
(espero que no).

Abris terminal otra vez, copias esto:

```
[COLOR=Red]**[FONT=Droid Serif, serif]sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default[/FONT]**[/COLOR]
```

Cuando te devuelve el cursor, escribis
esto:

```
[FONT=Droid Serif, serif][SIZE=1][COLOR=Red]gksudo gedit /etc/apt/sources.list[/COLOR][/SIZE][/FONT]
```

En el editor de texto agregás abajo de
todo las dos lineas que coloco acá:

[FONT=Droid Serif, serif][SIZE=1]deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
[/SIZE][/FONT][FONT=Arial][SIZE=1][B]deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

[/B]Copialas tal cuál las pongo. Guardás el archivo
y cerrás el editor de texto.
Abrís terminal y pegas esto:

[/SIZE][/FONT]```
[COLOR=Red]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9[/COLOR]
```
```
[COLOR=Red]sudo apt-get update[/COLOR]
```

---

### Post by facurdo on 2009-09-11
CUando acutalizo con sudo apt-get update no me deja terminar

> Descargados 88,2kB en 5s (16,1kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by pablo.s on 2009-09-11
Bueno. Suele pasar. Tenés que
ejecutar en una terminal

```
dpkg --configure -a
```

para que se reconfigure el gestor
de paquetes. Avisame cuando esté
hecho.

---

### Post by facurdo on 2009-09-11
Hecho!
No puedo creer esta ayuda instantanea jajaja :D

---

### Post by pablo.s on 2009-09-11
Ok. No te emociones todavia
que el problema sigue.
El último paso es crucial. Acá
vas a cargar los drivers de Intel
y si los descarga bien, ya deberia
estar funcionando luego del
reinicio.

Abri una terminal y ejecutá:

```
[FONT=Arial][SIZE=1][COLOR=Red]sudo apt-get dist-upgrade[/COLOR][/SIZE][/FONT]
```

Ahi te tiene que decir que se van
a actualizar paquetes. Si te dice que
tiene que borrar paquetes, poné que NO.
Avisame cuando esté hecho.

---

### Post by facurdo on 2009-09-11
LIsto, ya se actualizaron los paquetes

---

### Post by pablo.s on 2009-09-11
Reiniciá la maquina y
fijate si podés cambiar
la resolución y/o habilitar
Compiz.
A la vuelta si funcionó te
cuento que hiciste.

---

### Post by facurdo on 2009-09-11
Reinicie y nada :(, parece que intel le hace la cruz a linux

---

### Post by pablo.s on 2009-09-11
Con qué programa cambiás
la resolución?

---

### Post by facurdo on 2009-09-11
NInguno, desde sistema >preferencias

AHora estoy bajando el Compiz

---

### Post by pablo.s on 2009-09-11
Probá a instalar

```
sudo apt-get install grandr
```

que es un programita para
cambiar la resolución de
pantalla.

---

### Post by facurdo on 2009-09-11
Disculpa mi ignorancia, lo instale, pero no lo encuentro en Aplicaciones :confused:
Hay alguna forma de abrir grandr por la terminal?

---

### Post by pablo.s on 2009-09-12
Si, tenés que presionar
Alt+F2 y escribir

```
grandr
```

---

### Post by facurdo on 2009-09-12
QUe dicha la mia, pero no, solo hasta 800x600, es una lastima :(
Igual te agardezco esta ayuda personal que me distes y de esta manera, te estoy muy agradecido.
OJala encuentre alguna solucion

---

### Post by facurdo on 2009-09-12
Hay un listado de drivers incluido los de intel que necesito y no puedo actualizarlos, aca te dejo el screeN.
Tiene algo que ver con mi problemita?
[[IMG]http://img143.imageshack.us/img143/2886/pantallazogestordeactua.th.png[/IMG]]("http://img143.imageshack.us/i/pantallazogestordeactua.png/")

---

### Post by Hei Ku on 2009-09-12
No, eso es porque tenes la 8.10 y tendrias que actualizar a 9.04

Me parece q las instrucciones de pablo eran para la 9.04.

---

### Post by pablo.s on 2009-09-12
No eran para 9.04. 
Eran para cualquier versión. Lo que
hacian las instrucciones eran cambiar
el seteo en xorg.conf a UXA, cargar un
script que corrige un error y actualizar
los drivers de intel por unos más
recientes.

---

### Post by facurdo on 2009-10-31
NO quiero revivir post viejos, pero acabo de instalar la tan esperada version de ubutnu 9.10, pero sigo con el mismo problema, la maxima resolucion es de 800x600, la verdad una gran tristesa hacia ubuntu :( esperaba algo mas.

---

### Post by guillermolisi on 2009-10-31
> **facurdo said:**
> NO quiero revivir post viejos, pero acabo de instalar la tan esperada version de ubutnu 9.10, pero sigo con el mismo problema, la maxima resolucion es de 800x600, la verdad una gran tristesa hacia ubuntu :( esperaba algo mas.
Por lo que decis con otras distribuciones Linux no tenes el mismo problema, es asi ?

---

### Post by facurdo on 2009-10-31
> **guillermolisi said:**
> Por lo que decis con otras distribuciones Linux no tenes el mismo problema, es asi ?

En esta pc no probe con otras distribuciones

---

### Post by guillermolisi on 2009-10-31
Releyendo todo el thread y comparando con las especificaciones que figuran en el manual del monitor, encontre que hay parametros usados oportunamente en el xorg.conf que no eran del todo correctos.

El manual dice:> 
Resolución Máx.
1024 x 768
Frecuencia Horizontal - 30-54 KHz
FrecuenciaVertical 50-120 Hz

Y esos rangos de frecuencias son los que se deberian definir en ese archivo para la resolucion maxima del monitor.

El manual, por si no lo tenes, lo encontras en [http://latam.benq.com/support/downloads/downloads.cfm?product=106&page=downloads&dtype=M](http://latam.benq.com/support/downloads/downloads.cfm?product=106&page=downloads&dtype=M)

---

### Post by facurdo on 2009-11-01
Enhorabuena la resolucion es 1024x768 despues de tantos meses esta, pero el problema persiste ¬¬ ....

No me arranca la forma visual, solo la pantalla negra como si fuera la terminal
> Ubuntu 9.10 tty1
facurdo login : 
me logueo y todo eso, pero no se que hacer desde ahi, no tengo ni la mas palida idea de como manejarme solo de una terminal en pantalla completa :(

Probe con  arrancar en Recovery Mode, nada de nada, intente arrancar con el grub anterior de Ubnutu 9.04, me pasa lo mismo, pero se ve todo gigante como antes.

Estoy perdido...

---

### Post by guillermolisi on 2009-11-01
Fijate [en este post]("http://ubuntuforums.org/showpost.php?p=8214380&postcount=8") que dan una posible solucion complementaria a lo que ya tenes avanzado.

---

### Post by facurdo on 2009-11-01
Gracias por el link, pero no me sirve de nada, desde la pantalla negra no puedo usar ni lel comando sudo getedit, menos la configuracion del archivo [B]Xorg.0.log
gracias
[/B]

---

### Post by moreback on 2009-11-01
Acá el problema es con las frecuencias del monitor. Por alguna razón el Xorg no las puede leer desde el monitor, por lo que hay que indicárselas manualmente.

Para eso se agregan las que publicó guillermolisi (que son las que indica el fabricante) en la sección Monitor de tu xorg.conf:

```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
[B]        HorizSync    30-54
        VertRefresh  50-120
[/B]EndSection
```y luego se selecciona por defecto la resolución 1024x768 en la sección Screen

```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
[B]        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes     "1024x768"
        EndSubSection
[/B]EndSection
```Marqué en negritas los cambios que habría que hacer. Si no sabes como modificarlos, publica tu /etc/X11/xorg.conf y te hacemos los cambios.

Saludos.

---

### Post by mosbel on 2009-11-01
No es por invadir post o algo, pero llegue aqui con la esperanza de encontrar una solucion, y bueno, ojala pueda que este, mi problema es algo parecido, hace apenas 3 dias instale Ubuntu 9.10, pero mi sorpresa fue que la maxima resolucion detectada es 1024x768, es la primera vez que me pasa esto ya que en cualquier version anterior a esta siempre podia acceder hasta 2 resoluciones mas, e estado buscando mucho pero no encuentro nada y por lo que e leido el xorg.conf no se encuentra en Ubuntu 9.10, leyendo algunas soluciones decia que tenia que crearlo, lo cual hice, pero siempre esta en blanco, mi tarjeta es:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by facurdo on 2009-11-01
Moreback, lo que aclarastes ya estaba echo, lo de modificar manualmente el xorg.conf el problema que ahora no quiere arrancar el modo visual

Solo carga la pantalla negra con el login y despues a la terminal, no hay nada mas que eso, esto sucedio despues de cambiarle al xorg.conf esto
> [B][B]HorizSync    30-54
        VertRefresh  50-120
[/B][/B]Aunque guillermolisi lo publico en negativo el HorizSync
> 
Frecuencia Horizontal - 30-54 KHz
FrecuenciaVertical 50-120 Hz                      Lo probe primero como vos indicabas, no pasaba nada, lo puse en negativo como indico guillermolisi y parece que funciona pero en pantalla negra (todas las letras hasta el grub se ven mucho mas chicos que anteriormente)
no hay alguna funcion para arrancar al modo visual desde la pantalla negra?

> **mosbel said:**
> No es por invadir post o algo, pero llegue aqui con la esperanza de encontrar una solucion, y bueno, ojala pueda que este, mi problema es algo parecido, hace apenas 3 dias instale Ubuntu 9.10, pero mi sorpresa fue que la maxima resolucion detectada es 1024x768, es la primera vez que me pasa esto ya que en cualquier version anterior a esta siempre podia acceder hasta 2 resoluciones mas, e estado buscando mucho pero no encuentro nada y por lo que e leido el xorg.conf no se encuentra en Ubuntu 9.10, leyendo algunas soluciones decia que tenia que crearlo, lo cual hice, pero siempre esta en blanco, mi tarjeta es:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Si por alguna casualidad logro arrancar en el modo visual te mando un mp con mi xorg.conf  =)

---

### Post by guillermolisi on 2009-11-01
> **facurdo said:**
> 
Lo probe primero como vos indicabas, no pasaba nada, lo puse en negativo como indico guillermolisi y parece que funciona pero en pantalla negra (todas las letras hasta el grub se ven mucho mas chicos que anteriormente)
no hay alguna funcion para arrancar al modo visual desde la pantalla negra?

Lo que te pase de las frecuencias fue un copy & paste literal de lo que mencionaba el manual. 

**Logicamente no hay frecuencias negativas !! (frecuencia habla de cuantas veces por unidad de tiempo algo varia entre dos valores extremos. Como seria esto negativo ?)**

---

### Post by moreback on 2009-11-01
Te da pantalla negra porque no puede iniciar el entorno gráfico, el problema debe ser que no encuentra una frecuencia apta para el monitor. Es por eso que te indiqué que había que hacer otra modificación para forzar a la resolución que quieres. ¿Intentaste hacer esto último?

---

### Post by facurdo on 2009-11-01
> **moreback said:**
> Te da pantalla negra porque no puede iniciar el entorno gráfico, el problema debe ser que no encuentra una frecuencia apta para el monitor. Es por eso que te indiqué que había que hacer otra modificación para forzar a la resolución que quieres. ¿Intentaste hacer esto último?

Ya dije que no puedo modificar el xorg.conf no me deja
arranca la pc con pantalla negra, me pide mi nomre de usuario el pass, y aparece la terminal, o como si fuera DOS en WIN, pongo sudo getedit bla bla bla xorg.conf o lo que sea, y no me deja, estoy sin manos para poder hacer algo

---

### Post by mosbel on 2009-11-01
> **facurdo said:**
> 
Si por alguna casualidad logro arrancar en el modo visual te mando un mp con mi xorg.conf  =)

Gracias, esperare :)

---

### Post by guillermolisi on 2009-11-01
> **facurdo said:**
> Ya dije que no puedo modificar el xorg.conf no me deja
arranca la pc con pantalla negra, me pide mi nomre de usuario el pass, y aparece la terminal, o como si fuera DOS en WIN, pongo sudo getedit bla bla bla xorg.conf o lo que sea, y no me deja, estoy sin manos para poder hacer algo
Que error o mensaje obtenes cuando queres editar el /etc/X11/xorg.conf en consola ?

---

### Post by mosbel on 2009-11-01
Creo que *gedit* no puede ser usado en modo texto, en lugar de eso se usa *nano*.

---

### Post by guillermolisi on 2009-11-01
> **mosbel said:**
> Creo que *gedit* no puede ser usado en modo texto, en lugar de eso se usa *nano*.
Totalmente en lo correcto. En consola se pueden usar nano, vim, vi y algun otro que ahora no recuerdo.

---

### Post by X1R1 on 2009-11-01
A ver, ya me lei todo el post para actualizarme con el problema. Si dices que las letras las notas mas pequeñas en la pantalla negra y que crees que el cambio funciona pero no puedes editar el xorg.conf porque no tienes entorno grafico, prueba lo siguiente.

> sudo startx

si ese no hace nada, entonces:

> sudo /etc/init.d/gdm start

Ese comando inicia el entorno grafico, cuando lo ejecutes ubuntu deberia intentar cargar todo el entorno grafico. Si lo que quieres es editar el xorg.conf y no tienes entorno grafico, en ves de sudo gedit, prueba con:

> sudo nano /etc/X11/xorg.conf

ojala te sirva.

Para agregarle un poco mas al tema, yo tengo un chip intel integrado tambien en my placa madre, y el problema que tenia era que los videos se cortaban y reproducian muy lento, pero segui el COMO de la configuracion de las tarjetas intel safe/optimal y despues de eso todo me funciono perfecto. Tambien con la actualizacion del karmic todos esos problemas ya bienen solucionados, asi que aqui el problema es la configuracion que tenes no el hardware.

---

### Post by facurdo on 2009-11-02
X1R1, probe con los conando que me distes 
> sudo startx                      Intenta iniciar el modo visual y me salta un error en la linea 25 en el xorg.conf, seguro es el numero negativo que le puse a los Hz horizontales (que dolobu que soyyyy jajaja), y me pide que revise el archivo xorg.0.log, lo abro pero aparece vacio :S

> sudo /etc/init.d/gdm start                       [B]Rather than invoking init scripts trought /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an Upstart job, you many also use the start(8) utility, e.g. star gdm

gdm start/running, proces 1569
[/B]
>                               sudo nano /etc/X11/xorg.conf                      Me abre el archivo xorg.conf pero esta totalmente vacio, tal vez ese sea el problema, no existe la configuracion del xorg.conf

---

### Post by guillermolisi on 2009-11-02
> **facurdo said:**
> X1R1, probe con los conando que me distes 
Intenta iniciar el modo visual y me salta un error en la linea 25 en el xorg.conf, seguro es el numero negativo que le puse a los Hz horizontales (que dolobu que soyyyy jajaja), y me pide que revise el archivo xorg.0.log, lo abro pero aparece vacio :S

 [B]Rather than invoking init scripts trought /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an Upstart job, you many also use the start(8) utility, e.g. star gdm

gdm start/running, proces 1569
[/B]
Me abre el archivo xorg.conf pero esta totalmente vacio, tal vez ese sea el problema, no existe la configuracion del xorg.conf
Genera un archivo /etc/X11/xorg.conf basico ejecutando en una consola/terminal lo siguiente:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Luego, estas usando Gnome como escritorio grafico ?

---

### Post by facurdo on 2009-11-02
> sudo dpkg-reconfigure -phigh xserver-xorg
[B]Paquete xerver-xorg no esta instalado y no hay informacion disponible

[/B]Si, uso gnome y aviso que mi configuracion del xorg.conf no es igual que al principio del thread encontre un link para solucionar el problema con los que tienen mi chipset intel
[http://www.ubuntu-es.org/?q=node/120136](http://www.ubuntu-es.org/?q=node/120136)

mi xorg.conf (Los hz horizontates y verticales dependen de cada monitor)
> Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    30-63
	VertRefresh  56-71
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1024x768"
	EndSection

Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: i: integer, f: float, bool: "True"/"False",
	### string: "String", freq: "f Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "NoAccel"            	# [bool]
	#Option     "SWcursor"           	# [bool]
	#Option     "ColorKey"           	# i
	#Option     "CacheLines"         	# i
	#Option     "Dac6Bit"            	# [bool]
	#Option     "DRI"                	# [bool]
	#Option     "NoDDC"              	# [bool]
	#Option     "ShowCache"          	# [bool]
	#Option     "XvMCSurfaces"       	# i
	#Option     "PageFlip"           	# [bool]
	Identifier  "Card0"
	Driver      "intel" #card0driver
	VendorName  "Intel Corporation"
	BoardName   "82865G Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Monitor0"
   DefaultDepth 24
   Subsection "Display"
      Depth       24
      Modes       "1024x768"
   EndSubsection
EndSection


---

### Post by guillermolisi on 2009-11-02
> **facurdo said:**
> [B]Paquete xerver-xorg no esta instalado y no hay informacion disponible

[/B]Si, uso gnome y aviso que mi configuracion del xorg.conf no es igual que al principio del thread encontre un link para solucionar el problema con los que tienen mi chipset intel
[http://www.ubuntu-es.org/?q=node/120136](http://www.ubuntu-es.org/?q=node/120136)

mi xorg.conf (Los hz horizontates y verticales dependen de cada monitor)
Y con eso quedo solucionado ?

---

### Post by facurdo on 2009-11-02
Desde que lo modifique de esa manera no, puse los valores correspondientes del monitor, y nada, hasta que copie exactamente como indicaron en este thread con ese error de un numero en negativo, desde ahi no arranca en modo visual, pero me doy cuenta que la resolucion aumento.

Si arranco con la version del kernel anterior que el de Ubuntu 9.10 todo se ve gigante como me venia pasando desde el principio, un cambio hubo de eso estoy seguro, el problema es que no puedo iniciar en la forma visual

---

### Post by guillermolisi on 2009-11-02
> **facurdo said:**
> X1R1, probe con los conando que me distes 
Intenta iniciar el modo visual y me salta un error en la linea 25 en el xorg.conf, seguro es el numero negativo que le puse a los Hz horizontales (que dolobu que soyyyy jajaja), y me pide que revise el archivo xorg.0.log, lo abro pero aparece vacio :S

 [B]Rather than invoking init scripts trought /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an Upstart job, you many also use the start(8) utility, e.g. star gdm

gdm start/running, proces 1569
[/B]
Me abre el archivo xorg.conf pero esta totalmente vacio, tal vez ese sea el problema, no existe la configuracion del xorg.conf
Hay algo que no me cierra en absoluto.

Primero decis que recibis un mensaje de error: > Intenta iniciar el modo visual y me salta un error en la linea 25 en el xorg.confY mas adelante intentas editar el mismo archivo pero decis que esta vacio. No habras tenido algun error de tipeo al querer editarlo ?

Luego, salvo que en Karmic las cosas se hayan modificado sustancialmente, deberia funcionar la linea de comando con > sudo /etc/init.d/gdm start/restart/stopTambien me llama poderosamente la atencion que de error la regeneracion del xorg.conf cuando corres > sudo dpkg-reconfigure -phigh xserver-xorg

En Karmic no hay xserver ? :)

---

### Post by facurdo on 2009-11-02
No no hay error de tipeo, lo intente otra vez, me sigue diciendo que hay un error en la linea 25, y lei mas atento,tambien indica que hay un error en el ranngo del HorizSync, estoy seguro que ese es el error, por eso no me deja arrancar en el modo visual, le puse un valor negativo como me indicaron antes (error de tipeo seguro)

Y tampoco arranca con el grub, ubuntu  9.04 siempre hacia automaticamente un buckup del xorg.conf cuando lo modificabas, si habia error usaba el buckup, parece que ahora no lo hizo.

con respecto a:
> sudo /etc/init.d/gdm start/restart/stop 			 		
[B]the script you are attempting to invoke has been converted to an Upstart job, but start/restart/stop is not supported for Upstar jobs.

Rather tan invoking init scripts through /etc/init.d, use the service ( 8 ) utility, e.g. service gdm start/restart/stop

[/B]

---

### Post by guillermolisi on 2009-11-02
Me parece que no estas leyendo detenidamente mi ultimo mensaje, por lo menos.

Si obtenes un error en linea 25 entonces no puede ser que cuando edites el mismo archivo éste este en blanco.

Para reinicar GDM, proba con ```
sudo service gdm start
``` y puede ser que tengas que probar con restart.

---

### Post by facurdo on 2009-11-02
Te estoy diciendo que me marca error en la linea 25 que el valor del HorizSync es erroneo, y no tipee nada mal, cuando abro el xorg.conf me aparece vacio, la pantalla negra con el menu de abajo

Y los comandos que me distes no hicieron nada.

En fin mas de 1 mes solucionando una tonteria de resolucion, y cada vez empeora. Bajo los brazos con Ubuntu, cierren este thread... Si veo que Knoppix funciona sin ninguno problema o Fedora que me los recomendaron sigo con linux, si no devuelta a windows, no puedo estar pendiente de un sistema operativo con problemas.

---

### Post by guillermolisi on 2009-11-02
> **facurdo said:**
> Te estoy diciendo que me marca error en la linea 25 que el valor del HorizSync es erroneo, y no tipee nada mal, cuando abro el xorg.conf me aparece vacio, la pantalla negra con el menu de abajo

Y los comandos que me distes no hicieron nada.

En fin mas de 1 mes solucionando una tonteria de resolucion, y cada vez empeora. Bajo los brazos con Ubuntu, cierren este thread... Si veo que Knoppix funciona sin ninguno problema o Fedora que me los recomendaron sigo con linux, si no devuelta a windows, no puedo estar pendiente de un sistema operativo con problemas.
Como vos quieras.

---

