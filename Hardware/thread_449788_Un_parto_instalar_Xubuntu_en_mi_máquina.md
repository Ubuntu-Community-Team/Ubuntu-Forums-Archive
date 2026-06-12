---
title: "Un parto instalar Xubuntu en mi máquina"
date: 2007-05-20
forum: Hardware
---

### Post by curupi on 2007-05-20
Hola, aquí un nuevo más, en realidad no soy nuevo porque todavía estoy fuera del universo Linux, ayudenmé a dejar de estarlo. Tengo el windows xp en una partición NTFS de unos 23 gb, otra FAT32 para documentos de unos 6 gb y con el Partition Magic me deje libres unos 8 gb.

Me bajé el Xubuntu 6.06.1 (Dapper Drake) debido a que mi máquina tiene unos cuantos añitos. Lo bajé en sus dos versiones Desktop CD y Alternate.

La cosa es que en ambos casos booteo la máquina desde el cd y al comenzar la instalación queda todo parado, colgado, sin signos de vida, como quieran llamarle. Con el Desktop mer pone la barrita de progreso que nunca empieza crece y con el Alternate llego hasta que me pregunta idioma, país, teclado y despues de eso pasa a una pantalla azul con un renglón blanco en la parte inferior de la pantalla donde se puede escribir. En ese momento reinicio e insulto un poco.

Mi idea es dejar el Xp y probar el Xubuntu. Si veo que me gusta, chau XP.

Que puede estar pasando? LAs características de mi máquina:

Placa base :    Tipo de procesador Intel Pentium 4, 1300 MHz (13 x 100)    Nombre de la Placa Base MSI 850 Pro2 (MS-6523) (4 PCI, 1 AGP, 1 CNR, 4 RIMM, Audio)    Chipset de la Placa Base Intel Tehama i850    Memoria del Sistema 128 MB (RDRAM)    Tipo de BIOS Award Modular (08/02/01)    Puerto de comunicación Puerto de comunicaciones (COM1)    Puerto de comunicación Puerto de comunicaciones (COM2)    Puerto de comunicación Puerto de impresora (LPT1)    

Monitor :    Tarjeta gráfica NVIDIA RIVA TNT2 Model 64 (32 MB )    Acelerador 3D nVIDIA RIVA TNT2 M64    Monitor Philips 105S5 [15" CRT] (28404102)    

Multimedia :    Tarjeta de sonido Intel 82801BA(M) ICH2 - AC'97 Audio Controller [B-4]   

Almacenamiento :    Controlador IDE Controladora de Bus Master IDE Intel(r) 82801BA    Controlador SCSI/RAID SCSI/RAID Host Controller    Controlador SCSI/RAID ST3MP28 SCSI Controller    Disquetera de 3 1/2 Unidad de disquete    Disco duro SAMSUNG SV4084H (37 GB , 5400 RPM, Ultra-ATA/100)    Lector óptico SAMSUNG CD-R/RW SW-408B (8x/8x/32x CD-RW)    Estado de los discos duros SMART OK   

Particiones :    C: (NTFS) 25242 MB (9393 MB libre)    D: (FAT32) 6670 MB (484 MB libre)    Tamaño total 31912 MB (9877 MB libre)    

Dispositivos de entrada :    Teclado Teclado estándar de 101/102 teclas o Microsoft Natural PS/2 Keyboard    Ratón Mouse compatible con HID    

Red :    Tarjeta de Red Adaptador Fast Ethernet PCI CNet PRO200 (201.231.142.145)    Modem Motorola SM56 PCI Fax Modem    

Dispositivos :    Impresora Acrobat Distiller    Impresora hp deskjet 3500 series    Controlador USB1 Intel 82801BA(M) ICH2 - USB Controller 1 [B-4]    Controlador USB1 Intel 82801BA(M) ICH2 - USB Controller 2 [B-4]    Dispositivos USB Dispositivo de interfaz humana USB    Dispositivos USB GeneLink USB Adapter

---

### Post by guillermolisi on 2007-05-20
[COLOR=Black]Lo primero que me llamo la atencion, y si no lei mal, es la poca cantidad de memoria RAM que posee tu equipo (sobretodo si lo estas haciendo funcionar con WinXP).

No se si leiste las recomendaciones para correr un LiveCD de Xubuntu y para hacer su instalacion, pero por las dudas te las paso textuales copiadas del mismo site, seccion System Requirements:[/COLOR]

**[COLOR=Blue]Minimum system requirements[/COLOR]**

 [COLOR=Blue]To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte")[RAM]("http://en.wikipedia.org/wiki/RAM").[/COLOR] 
 [COLOR=Blue]To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.[/COLOR]
 [COLOR=Blue]Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.[/COLOR]
[COLOR=Blue]

[COLOR=Black]En criollo y sintetizado: Para la version Desktop CD necesitas 192 Mb RAM minimos si queres instalar.

No vi que hubiera discriminacion entre las versiones estables respecto de estos minimos, por lo que asumo que rigen desde la 6.06 hasta la 7.04 pasando por la 6.10.

Espero haberte aclarado un poco el panorama.

Saludos
[/COLOR][/COLOR]

---

### Post by Al_maverick on 2007-05-20
Yo corro el xubuntu en PII de 128MB de RAM. Como experiencia, te cuento que el LiveCD tardaba una media hora en total para levantar, sin signos de vida por varios minutos, y no me fue posible instalarlo desde ahi, porque precisa 192MB minimo.
Para instalar me baje el alternate, y con bastante paciencia anduvo la instalacion. Ahora anda bien, y estoy posteando desde esa pc.
Cuando decis que no hace nada, cuanto tiempo esperas? Hay actividad del disco? te tenes que armar de paciencia, a mi me llevo una tarde completa.

---

### Post by curupi on 2007-05-21
Si, ya se que tengo poca RAM, por eso decidí instalar Xubuntu. El XP me anda muy lento pero cuando lo instalé fue porque no soportaba los cuelgues del ME. 

Entiendo que el Desktop CD no ande por eso pero el Alternate debería funcionar.

Saludos

---

### Post by Cows on 2007-05-21
Tu si necesitas usar algo mas bajito. Talbe fluxbuntu. fluxbuntu no necesita algo muy potente porque estabe echo para computadoras bajas. ( no tengo lo accentos en mi computadora porque yo vivo en US ).

---

### Post by Al_maverick on 2007-05-21
La cosa es que deberia funcionar. Tanto el LiveCd como el alternate, aunque lentos, deberian andar. Lo que no vas a poder hacer es instalar desde el desktop CD.

Probaste de dejarlos un rato largo? a mi tambien me parecio que estaban colgados al principio.

---

### Post by kowal on 2007-05-21
Esa placa de video es onboard? Si es así, te está sacando 32mb de RAM. De todas formas es raro que no inicie el alternate. Yo probaría con un Debian para esa maquinola.

---

### Post by lugonesjoaquin on 2007-05-21
Tambien puedes crear una particion Swap y te va a dejar instalar :D

No sé pero a mi me da la imprecion de que ya no hay tanta diferencia de consumo entre Xfce y Gnome por ejemplo.

Yo instale Debian en una PII 400mhz y 64mb de ram con Gnome y me andaba incluso mejor que Xubuntu. Obviamente le reduci algunas consolas, lo deje sin fondo de escritorio, más que nada cosas obvias para que no se trabe tanto y anda perfecto.

Ahora, si quieres volar volar... Yo le pongo Fluxbox (Que bien personalizado es espectacular) y vuela!

---

### Post by curupi on 2007-05-23
Gracias por los consejos. Ya pude instalar el Xubuntu. ¿Como? Me bajé la versión 7.04 (Feisty Fawn) Alternate y todo joya. Lo que sí veo es que anda muy lento. Más lento que el XP. Voy a considear instalar el fluxbuntu ese que me dicen. Tal vez se pueda optimizar el xubuntu, no se...
saludos.

---

### Post by valucha on 2007-05-24
[COLOR="DarkOrchid"]Fijate esto [http://www.ubuntu-es.org/node/4440](http://www.ubuntu-es.org/node/4440)
yo siempre lo hice con Ubuntu, Kubuntu y Xubuntu y funcionó.[/COLOR]

---

### Post by kbarquero on 2008-06-14
Hola:

Yo estoy llegando al punto de la desesperación, me han dejado un portátil que es una patata y le tengo que instalar ubuntu. Este no cabe, así que ahora estoy con xubuntu.

Llevo tres cds quemados con errores. ¿Sabéis algún método para que esto no ocurra? voy a probar con uno regrabable que me saldrá mejor.

Un saludo

---

### Post by andy_91 on 2008-06-14
Lo mismo que otro post, yo probaria con icewm dicen que es mas ligero que Xfce

otro muy bueno es LXDE que consume no mucho mas que un win98 y es muy bueno

te dejo algunos enlaces de distros que usan LXDE

   >  * [PUD GNU/Linux]("http://distrowatch.com/?newsid=04826"): Ubuntu-based installable live cd with LXDE
    * [TinyMe]("http://tinyme.mypclinuxos.com/"): PCLinuxOS-based tiny distro using some components of LXDE
    * [Slitaz]("http://www.slitaz.org/en/"): Extremely small live cd using most of the components of LXDE
    * [Greenie]("http://greenie.sk/"): Ubuntu-based distribution especially for slovak and czech users. Using GNOME and LXDE as DE

---

### Post by faktorqm on 2008-06-14
Yo en compus viejas probe ELive GEM y va como trompada. Deje los links para bajarlo en este mismo sub-foro, fijate. Salu2!!

---

### Post by andy_91 on 2008-06-14
bueno yo ahora tengo instalado Open GEU con gnome secion y PCMan File Maneger. Y pueden creer que la diferencia no es mucha, sin contar la comodidad y facilidad de gnome

Así que a estas alturas me quede con gnome (hay que decir que Open GEU no trae Nautilus)

pero nose si es el caso de Elive, como sea EDE es muy buena opcion

---

