---
title: "Problemas de Instalación"
date: 2009-01-05
forum: Hardware
---

### Post by sysprog2008 on 2009-01-05
Alguien tiene idea o en algun lugar existe alguna guia rapida o tutorial que indique como corno instalar Ubuntu 8.10 en una notebook Bangho Pentium DUALCORE con 4 GB de RAM y disco SATA de 160 ??
Muchas Gracias :)

---

### Post by staar on 2009-01-05
que problema tenes exactamente?
ubuntu es extremadamente facil de instalar, supongo que te habras bajado el livecd, sino, bajalo, quemalo, inicia la notebook desde el cd (proba prenderla con el cd puesto, si te inicia ubuntu, buenisimo, sino vas a tener que ir a la bios y cambiar el orden de boot para que lea primero en la lectora de cd)
te va a aparecer un menu, selecciona la primera opcion, y te va a cargar el sistema enteramente desde el cd, **sin tocar** tu disco duro, ni windos, ni nada en tu pc...
vas a tener el sistema completamente funcional desde el cd, en el escritorio vas a encontrar un icono de instalar, es un asistente muy facil e intuitivo, y en veinte minutos vas a tener ubuntu instalado :D

otra opcion que tenes, es instalarlo mediante wubi, que te lo instala como una aplicacion de windos, es completamente funcional y en el inicio te deja elegir si queres usar windos o ubuntu, sinceramente, no probe esta forma y no se como es, pero creo que solo tenes que poner el livecd en windos y seguir el asistente...

saludos

---

### Post by guillermolisi on 2009-01-05
> **sysprog2008 said:**
> Alguien tiene idea o en algun lugar existe alguna guia rapida o tutorial que indique como corno instalar Ubuntu 8.10 en una notebook Bangho Pentium DUALCORE con 4 GB de RAM y disco SATA de 160 ??
Muchas Gracias :)

Es muy facil pero primero te aconsejo que inicies la maquina en modo Live-CD, sin instalar, asi podes comprobar que cosas son reconocidas al toque y cuales no (webcam por ejemplo).

He probado Ubuntu en varios modelos de esa marca sin mayores problemas salvo el caso de las webcams.

Para instalar, con iniciar desde el CD de Ubuntu y seguir el procedimiento en pantalla deberia salir funcionando razonablemente bien.

En todo caso, si reunis un listado de dudas y lo expones aqui te vamos ayudando "a distancia".

---

### Post by sysprog2008 on 2009-01-05
Bueno, basicamente mi padecimiento con Ubuntu (el cual no me amilana :P), se ha debido a fallas en instalaciones en equipos con distintas configuraciones.
Mi comentario se basa en que cuando queremos instalar windows en cualquier equipo, se logra sin problemas. No así con Ubuntu. Y esto me desespera porque quiero realmente utilizar Ubuntu.
Por ejemplo, he adquirido recientemente una notebook Bangho con procesador Intel DUAL CORE, 4 Gb de RAM y disco de 160 GB, el cual he particionado en 2 : una particion de 80 GB para windows y la otra parte la dejé sin particionar para instalar Ubuntu.
Resulta que arranco la notebook con el cd de Ubuntu 8.10 y, primera sorpresa, se queda tildada.
Buscando por Internet encontré que habia que bootear con modo 800x600x16, lo cual hice y voilá ! entró al programa de instalación.
Pero aquí no terminó todo. Cuando quiero que Ubuntu me instale todo automático, o sea, que cree sus propias particiones con el espacio libre que quedó en el disco (la 2da parte de 80 que yo no había particionado), me tira un error :S.
Como soy de descendencia vasca, me dije, no me va a ganar :P
Voy a hacer las particiones manualmente, con lo cual seguí todos los pasos : creé una particion tipo / de 50 gb aprox y la particion swap.
Todo iba bien hasta que reinició y, oh sorpresa, el grub no me reconoció la partición windows y quedó en un loop infinito.
Conclusión, tuve que salvar mi particion de windows con un disco de arranque del windows ejecutando en modo consola el comando FIXMBR y por lo tanto borrando el grub y así mi notebook quedó nuevamente operativa...pero con el Windows !!! :S
Como hay que hacer para que este estupendo sistema operativo GNU LINUX no provoque dolores de cabeza a cualquier usuario doméstico ?
(Aclaro que mi trabajo es de servicio técnico de PCs), por lo cual si a mí me da dolores de cabeza teniendo conocimientos medios, qué pasaría con un usuario común y corriente que está acostumbrado a agarrar un cd de windows xp o vista, lo pone y lo instala sin tener mas inconvenientes.
Además de esto me he encontrado infinidad de veces con problemas para reconocer placas wifi en notebooks, las cuales para instalarlas, casi que hay que hacer un curso en la NASA.
Por favor, tomen estos comentarios con el mayor de los respetos, puesto que como dije antes, no me quiero dar por vencido y quiero realmente utilizar y recomendar el Ubuntu, ya que estoy totalmente convencido que una vez que tenga todo funcionando, me dará mas satisfacciones que el sistema operativo conocido por todos ;)
Un gran abrazo y aprovecho la ocasión para desearles a todos los integrantes de esta lista un estupendo 2009 :)

---

### Post by guillermolisi on 2009-01-05
> **sysprog2008 said:**
> Bueno, basicamente mi padecimiento con Ubuntu (el cual no me amilana :P), se ha debido a fallas en instalaciones en equipos con distintas configuraciones.
Mi comentario se basa en que cuando queremos instalar windows en cualquier equipo, se logra sin problemas. No así con Ubuntu. Y esto me desespera porque quiero realmente utilizar Ubuntu.
Por ejemplo, he adquirido recientemente una notebook Bangho con procesador Intel DUAL CORE, 4 Gb de RAM y disco de 160 GB, el cual he particionado en 2 : una particion de 80 GB para windows y la otra parte la dejé sin particionar para instalar Ubuntu.
Resulta que arranco la notebook con el cd de Ubuntu 8.10 y, primera sorpresa, se queda tildada.
Buscando por Internet encontré que habia que bootear con modo 800x600x16, lo cual hice y voilá ! entró al programa de instalación.
Pero aquí no terminó todo. Cuando quiero que Ubuntu me instale todo automático, o sea, que cree sus propias particiones con el espacio libre que quedó en el disco (la 2da parte de 80 que yo no había particionado), me tira un error :S.
Como soy de descendencia vasca, me dije, no me va a ganar :P
Voy a hacer las particiones manualmente, con lo cual seguí todos los pasos : creé una particion tipo / de 50 gb aprox y la particion swap.
Todo iba bien hasta que reinició y, oh sorpresa, el grub no me reconoció la partición windows y quedó en un loop infinito.
Conclusión, tuve que salvar mi particion de windows con un disco de arranque del windows ejecutando en modo consola el comando FIXMBR y por lo tanto borrando el grub y así mi notebook quedó nuevamente operativa...pero con el Windows !!! :S
Como hay que hacer para que este estupendo sistema operativo GNU LINUX no provoque dolores de cabeza a cualquier usuario doméstico ?
(Aclaro que mi trabajo es de servicio técnico de PCs), por lo cual si a mí me da dolores de cabeza teniendo conocimientos medios, qué pasaría con un usuario común y corriente que está acostumbrado a agarrar un cd de windows xp o vista, lo pone y lo instala sin tener mas inconvenientes.
Además de esto me he encontrado infinidad de veces con problemas para reconocer placas wifi en notebooks, las cuales para instalarlas, casi que hay que hacer un curso en la NASA.
Por favor, tomen estos comentarios con el mayor de los respetos, puesto que como dije antes, no me quiero dar por vencido y quiero realmente utilizar y recomendar el Ubuntu, ya que estoy totalmente convencido que una vez que tenga todo funcionando, me dará mas satisfacciones que el sistema operativo conocido por todos ;)
Un gran abrazo y aprovecho la ocasión para desearles a todos los integrantes de esta lista un estupendo 2009 :)

La ultima vez que probe una notebook Bangho fue antes de Navidad.
La maquina es mas o menos como la que describis en tu primer post y use la 8.10 en modo Live, luego instale y funciono todo menos la webcam que requeria un poco mas de trabajo e investigacion.

WiFi, Ethernet, audio y aceleracion 3D para los efectos de escritorio funcionaron sin mayores inconvenientes ni trabajo adicional (salvo por los drivers propietarios y su correspondiente activacion).

Cuando hablas de Windows, te referis a XP o a Vista ?

Dual-Boot con Vista no se puede hacer porque genera conflictos con el Grub de uno y otro sistema operativo (ambos usan Grub pero Windows no respeta lo registrado por el Grub de Ubuntu).

Aclaro que las pruebas que hice en los distintos modelos de notebooks Bangho siempre fueron sobre maquinas que vinieron sin SO de fabrica y en ningun caso use dual boot, ni siquiera con XP (lo cual no invalida lo del Vista que puede ser corroborado por mas de uno en este foro).

---

### Post by sysprog2008 on 2009-01-05
entonces Guillermo, te paso el modelo exacto de mi notebook : B-54X8SS, es Dual Core, 4 GB RAM, Disco SATA 160 GB, Webcam, wifi, lector de tarjetas, etc.
Decime a ver que es lo que hice mal. Te cuento que instalé el Windows XP sin ningun problema, instalando los drivers desde el cd que me vino con la notebook (la misma venia sin sistema operativo). Lo hice creando una particion de 80 GB para XP y el resto lo dejé sin particionar para que lo hiciera automático el Ubuntu. Además de eso decime como se hacen funcionar el wifi y la webcam y el lector de tarjetas. Muchas Gracias :)

---

### Post by guillermolisi on 2009-01-05
> **sysprog2008 said:**
> entonces Guillermo, te paso el modelo exacto de mi notebook : B-54X8SS, es Dual Core, 4 GB RAM, Disco SATA 160 GB, Webcam, wifi, lector de tarjetas, etc.
Decime a ver que es lo que hice mal. Te cuento que instalé el Windows XP sin ningun problema, instalando los drivers desde el cd que me vino con la notebook (la misma venia sin sistema operativo). Lo hice creando una particion de 80 GB para XP y el resto lo dejé sin particionar para que lo hiciera automático el Ubuntu. Además de eso decime como se hacen funcionar el wifi y la webcam y el lector de tarjetas. Muchas Gracias :)
Por como planteas el particionado del disco me parece que hay un problema de procedimiento.

Cuando quieras Dual_Boot pimero tenes que instalar WinXP y luego Ubuntu porque si haces al reves el boot manager del XP sobreescribe la MBR y borra lo que puso el Grub de Linux.

Confirma, por favor, si mi apreciacion es correcta o no y despues vamos por el resto.

---

### Post by sysprog2008 on 2009-01-05
Lo hice en el sentido correcto. Primero instalé Xp y por último quise instalar el Ubuntu...

---

### Post by guillermolisi on 2009-01-06
> **sysprog2008 said:**
> Lo hice en el sentido correcto. Primero instalé Xp y por último quise instalar el Ubuntu...
Perfecto entonces (esto son los casos en que me encanta haberme equivocado).

Ahora probaria iniciando la notebook con el Live-CD para verificar que perifericos reconoce sin mas tramite y cuales no.

En mi experiencia, la antena WiFi deberia ser reconocida sin mayor trabajo por el NetworkManager via DHCP. Por lo menos deberia detectar algun SSID cercano, despues veremos si hace falta algun trabajo adicional (dependera de como esta configurado el router).

El lector de tarjetas es un dispositivo USB mas, asi que no deberian presentarse inconvenientes pero con la prueba del Live-CD vas a lograr un panorama mas preciso.

Con la maquina iniciada con el CD, abri una consola y obtene la salidas de los comandos lspci y lsusb para verlas en un proximo mensaje tuyo, asi tambien vamos a tener una idea clara de como reconoce el hardware.

---

### Post by sysprog2008 on 2009-01-06
Agarrate Catalina que ahí vamos :
lspci:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
03:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
03:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
03:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
ubuntu@ubuntu:~$ 

lsusb
ubuntu@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:5606 ALi Corp. 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$

---

### Post by sysprog2008 on 2009-01-07
Guille querido. Te cuento que como soy cabezadura, logré instalar el Ubuntu. Pero te cuento algunos inconvenientes que tengo.
Por empezar no logro una resolución de mas de 800x600. La placa de video es SIS tal cual te mandé en el mensaje anterior.
Además de eso, encontré que siempre tengo que modificar el grub a mano para que bootee, caso contrario se queda la pantalla negra y nunca arranca. Lo que hago es editar el grub en el momento de arrancar, presionando la tecla e y poniendo en la linea de kernel agregandole al final los comandos noacpi y nolacpi. De ese modo ubuntu arranca. O sea. Por ahora tengo 2 problemas. Como poder modificar de una vez el grub para no tener que poner siempre a mano esas sentencias, y el tema de la placa de video. Para mas adelante seguiremos con la webcam ;)
Un abrazo.

---

### Post by Hei Ku on 2009-01-07
Para modificar el boot, tenés que modificar el archivo /boot/grub.menu.lst

```

sudo gedit /boot/grub/menu.lst

```

Despues tenes que buscar la linea que dice defoptions y agregarle la opcion noapic y nolapic

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash noapic nolapic

```

Grabas, cerras y ya esta.

Por lo de tu placa de video, te recomiendo abrir una discusion aparte, porque eso va a llevar mas tiempo. Postea tu archivo /etc/X11/xorg.conf para ver qué driver estas usando ahora.

---

### Post by sysprog2008 on 2009-01-08
Pero Guille, no era que habias instalado el Ubuntu en varios notebooks Bangho ?? No tienen la misma placa de video ?

---

### Post by Hei Ku on 2009-01-08
En general, incluso entre notebooks del mismo modelo, los componentes internos varian bastante.

---

### Post by guillermolisi on 2009-01-09
> **sysprog2008 said:**
> Pero Guille, no era que habias instalado el Ubuntu en varios notebooks Bangho ?? No tienen la misma placa de video ?
No, no todos los modelos de notebooks Bangho tienen la misma placa de video, ni la misma interface de red, ni el mismo chipset, ni el mismo WiFi, etc.

En los modelos que probe la placa de video siempre fue nVidia.

---

### Post by guillermolisi on 2009-01-09
> **sysprog2008 said:**
> Guille querido. Te cuento que como soy cabezadura, logré instalar el Ubuntu. Pero te cuento algunos inconvenientes que tengo.
Por empezar no logro una resolución de mas de 800x600. La placa de video es SIS tal cual te mandé en el mensaje anterior.
Además de eso, encontré que siempre tengo que modificar el grub a mano para que bootee, caso contrario se queda la pantalla negra y nunca arranca. Lo que hago es editar el grub en el momento de arrancar, presionando la tecla e y poniendo en la linea de kernel agregandole al final los comandos noacpi y nolacpi. De ese modo ubuntu arranca. O sea. Por ahora tengo 2 problemas. Como poder modificar de una vez el grub para no tener que poner siempre a mano esas sentencias, y el tema de la placa de video. Para mas adelante seguiremos con la webcam ;)
Un abrazo.
En un mensaje anterior te sugiero iniciar la note en modo Live-CD (desde el CD pero sin instalar nada).

De esta forma vas a poder comprobar hasta que resolucion maxima de video toma automaticamente el servidor X11 para esa placa que usa tu maquina.

Inclusive, si esa placa posee aceleracion grafica vas a ver que los efectos de animacion basicos se activan solos.

---

### Post by sysprog2008 on 2009-01-10
Estimados amigos :
Les cuento que me estoy haciendo un experto en Ubuntu. JAJAJAJA (Mentira!)
No, en serio, estoy buscando información de todos lados, mas que nada porque soy un cabezadura, y a veces eso tiene sus beneficios.
Gracias al aporte de Guille pude editar el grub para no tener que cambiar siempre a mano el arranque. Y con respecto a la placa de video, encontré el siguiente link :
[http://www.ubuntu-es.org/index.php?q=node/88362#comment-301952](http://www.ubuntu-es.org/index.php?q=node/88362#comment-301952)

el cual hice al pie de la letra. O sea, edité el archivo xorg.conf

Grata fue mi sorpresa cuando descubrí que de esta manera, o sea, editando un archivo de texto, se puede hacer cualquier cosa :P

Lo único que no me funciona es la primer resolucion, la de 1280x800 pero sí funciona perfectamente la de 1280x768, lo cual es un logro inmenso, puesto que al principio no pasaba de 800x600.
Desde ya agradezco a todos los que me aguantan (especialmente a Guille ;) ) que pierde tiempo en este novato. Y quedo a la espera de nuevos consejos para llegar a la maxima resolución.
Y ya que estamos (porque ahora me pongo exquisito) como habilitar el compiz. JAJAJAJA

---

### Post by guillermolisi on 2009-01-10
> **sysprog2008 said:**
> Estimados amigos :
Les cuento que me estoy haciendo un experto en Ubuntu. JAJAJAJA (Mentira!)
No, en serio, estoy buscando información de todos lados, mas que nada porque soy un cabezadura, y a veces eso tiene sus beneficios.
Gracias al aporte de Guille pude editar el grub para no tener que cambiar siempre a mano el arranque. Y con respecto a la placa de video, encontré el siguiente link :
[http://www.ubuntu-es.org/index.php?q=node/88362#comment-301952](http://www.ubuntu-es.org/index.php?q=node/88362#comment-301952)

el cual hice al pie de la letra. O sea, edité el archivo xorg.conf

Grata fue mi sorpresa cuando descubrí que de esta manera, o sea, editando un archivo de texto, se puede hacer cualquier cosa :P

Lo único que no me funciona es la primer resolucion, la de 1280x800 pero sí funciona perfectamente la de 1280x768, lo cual es un logro inmenso, puesto que al principio no pasaba de 800x600.
Desde ya agradezco a todos los que me aguantan (especialmente a Guille ;) ) que pierde tiempo en este novato. Y quedo a la espera de nuevos consejos para llegar a la maxima resolución.
Y ya que estamos (porque ahora me pongo exquisito) como habilitar el compiz. JAJAJAJA
Un comentario solo para aclarar.

El tip sobre Grub y el enlace lo envio Hei Ku, no yo (con lo cual se merece una medallita a mi entender dados tus comentarios :) )

Sobre no aflojar o ser cabezadura, es un tema de actitud y supremacia humana por sobre la tecnologia (tal vez para evitar el paradigma de Terminator o para tender a el :) ).

Muchas cosas en Linux son, en general, mas simples de lo que mucha gente se imagina. Lo que "cuesta" saber es donde tocar pero eso, como todo aprendizaje en esta vida, se hace al andar.

Sobre el tema Compiz hay cantidad de threads al respecto en este foro. Mi recomendacion es que busques con la funcion Search dentro del Foro de Argentina y si no logras algo util abras otro hilo especifico del tema (asi, quienes experimenten tus mismas dudas y problemas puedan tambien aprovechar el conocimiento volcado en las soluciones de los mismos y tema por tema, sino es una bolsa de gatos inservible).

---

