---
title: "Driver Tableta Genius MousePen en .deb"
date: 2009-09-12
forum: Hardware
---

### Post by juancarlospaco on 2009-09-12
**[SIZE="5"][COLOR="Sienna"]Driver Tableta Genius MousePen en .deb[/COLOR][/SIZE]**

[LIST]
[*]**Controlador para las Tabletas Genius MousePen listo para usar.**
[/LIST]

[CENTER][IMG]http://www.noblecom.biz/osc1/images/art119mousepen450.jpg[/IMG]
*(no se guien por la caja, packaging, color, etc cambia frecuentemente pero el Chipset es el mismo)*
[/CENTER]

Testeado, no requiere tocar nada, solo instalar, reiniciar y sale andando.
Ya lo agregue en la Wiki Ubuntu en Ingles.

Lo hice por que tengo una, 
y no quiero compilar y tocar archivos de configuracion cada vez que la quiero usar,
es muy popular en Argentina por que las Wacom salen demasiados Dolares.

[LIST]
[*]11,1 KiB (11392 bytes)
[*]64Kb Instalado/Descomprimido
[*]Contiene 3 Archivos de controlador y 1 Script de Auto-Configuracion
[/LIST]


```
[http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb]("http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb")
```

:P

---

### Post by GGsalas on 2009-09-15
Me parecía demasiado bueno para ser cierto.. acabo de probarlo en Ubuntu 9.04 y no funciona con mi PenTablet MousePen 8x6 Genius. 

Hace un tiempo logré instalarla cumpliendo con los pasos que se explican en la wiki de ubuntu, pero de un día para el otro (seguramente por alguna actualizacion del sistema) dejó de funcionar.

Saludos

---

### Post by Hei Ku on 2009-09-15
te la reconoce como conectada?

---

### Post by GGsalas on 2009-09-15
> **Hei Ku said:**
> te la reconoce como conectada?

La tableta enviende la luz cuando muevo el lapiz. No se como puedo averiguar si ubuntu la reconoce como conectada.

---

### Post by guillermolisi on 2009-09-15
> **GGsalas said:**
> La tableta enviende la luz cuando muevo el lapiz. No se como puedo averiguar si ubuntu la reconoce como conectada.
Si es USB con "lsusb". Si es PCI con "lspci", siempre con la tableta conectada.

---

### Post by GGsalas on 2009-09-15
> **guillermolisi said:**
> Si es USB con "lsusb". Si es PCI con "lspci", siempre con la tableta conectada.

Parece que si la detecta. ¿Que más puedo hacer?

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 006: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Gracias

---

### Post by josecuervo86 on 2009-09-15
Fijate aca [0] que parece que le encontraron la vuelta

[0] [http://georgia.ubuntuforums.org/showthread.php?t=1151464&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1151464&page=2)

---

### Post by guillermolisi on 2009-09-15
> **GGsalas said:**
> Parece que si la detecta. ¿Que más puedo hacer?

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 006: ID 5543:0005 [COLOR=Red]UC-Logic Technology Corp. Genius MousePen 8x6[/COLOR] Tablet
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```Gracias
Ahi esta siendo reconocido a traves de una conexion USB, asi que la cosa viene por el lado del driver/modulo o su configuracion.

---

### Post by GGsalas on 2009-09-15
> **josecuervo86 said:**
> Fijate aca [0] que parece que le encontraron la vuelta

[0] [http://georgia.ubuntuforums.org/showthread.php?t=1151464&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1151464&page=2)

No hay caso.. voy muchas horas de hacer pruebas...

En el post que me recomendas dicen de instalar este programa: [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen) pero a mi no me funcionó


> Ahi esta siendo reconocido a traves de una conexion USB, asi que la cosa viene por el lado del driver/modulo o su configuracion. 

Guillermo, gracias, entiendo que el problema es el driver pero no existe un ningún tutorial que funcione. El que funcionaba al instalar ubuntu 9.04 dejó de funcionar en una de las actualizaciones del sistema

Saludos

---

### Post by guillermolisi on 2009-09-15
> **GGsalas said:**
> No hay caso.. voy muchas horas de hacer pruebas...

En el post que me recomendas dicen de instalar este programa: [https://launchpad.net/~doctormo/+archive/xorg-wizardpen]("https://launchpad.net/%7Edoctormo/+archive/xorg-wizardpen") pero a mi no me funcionó




Guillermo, gracias, entiendo que el problema es el driver pero no existe un ningún tutorial que funcione. El que funcionaba al instalar ubuntu 9.04 dejó de funcionar en una de las actualizaciones del sistema

Saludos
Y desinstalar el nuevo para instalar el viejo modulo no funcionara ? (algo asi hubo que hacer con algunas WiFi al principio de la 9.04 y que estaban funcionando con los drivers de la 8.10, y salieron a flote)

---

### Post by juancarlospaco on 2009-09-15
*mmm...* PenTablet no es lo mismo que la que yo decia, por mas que se parescan.
proba asi mira,** con la tableta conectada al USB**, ejecuta en una terminal:

**grep -i name /proc/bus/input/devices | grep ablet**

te tiene que responder:

**N: Name="UC-LOGIC Tablet WP8060U"**

que para ese chipset es la config que trae, si da otra cosa es otro modelo,
ademas acordate que lleva pilas, no es como las Wacom.
*Ha si la conectas por un hub USB a veces no anda.*

:)

---

### Post by Hei Ku on 2009-09-15
Tambien podes probar de volver a una version anterior de kernel, si con la 9.04 al principio te andaba.

---

### Post by GGsalas on 2009-09-16
> **juancarlospaco said:**
> *mmm...* PenTablet no es lo mismo que la que yo decia, por mas que se parescan.
proba asi mira,** con la tableta conectada al USB**, ejecuta en una terminal:

**grep -i name /proc/bus/input/devices | grep ablet**

te tiene que responder:

**N: Name="UC-LOGIC Tablet WP8060U"**

que para ese chipset es la config que trae, si da otra cosa es otro modelo,
ademas acordate que lleva pilas, no es como las Wacom.
*Ha si la conectas por un hub USB a veces no anda.*

:)

Juan Caros, te muestro lo que me da la línea de comandos, entiendo que está bien, a pesar de que no funciona:
```
~$ grep -i name /proc/bus/input/devices | grep ablet
N: Name="UC-LOGIC Tablet WP8060U"
```

---

### Post by GGsalas on 2009-09-16
> **guillermolisi said:**
> Y desinstalar el nuevo para instalar el viejo modulo no funcionara ? (algo asi hubo que hacer con algunas WiFi al principio de la 9.04 y que estaban funcionando con los drivers de la 8.10, y salieron a flote)

Guillermo, no sabría que moódulo desinstalar.

---

### Post by guillermolisi on 2009-09-16
> **GGsalas said:**
> Juan Caros, te muestro lo que me da la línea de comandos, entiendo que está bien, a pesar de que no funciona:
```
~$ grep -i name /proc/bus/input/devices | grep ablet
N: Name="UC-LOGIC Tablet WP8060U"
```
Por las dudas ... probaste en todos los ports USB que trae la maquina, particularmente los traseros ?

---

### Post by GGsalas on 2009-09-16
> **Hei Ku said:**
> Tambien podes probar de volver a una version anterior de kernel, si con la 9.04 al principio te andaba.

Hei Ku, ¿no es muy pobable que si intento eso deba reinstalar? :( hace poco que actualicé a Jaunty.. De todas maneras no se como volver al Kernel anterior y no recuerdo cuantas veces se actualizó.

---

### Post by Hei Ku on 2009-09-16
> **GGsalas said:**
> Hei Ku, ¿no es muy pobable que si intento eso deba reinstalar? :( hace poco que actualicé a Jaunty.. De todas maneras no se como volver al Kernel anterior y no recuerdo cuantas veces se actualizó.

Desde que actualizaste a Jaunty te dejó de funcionar? O actualizaste, te funciono un tiempo y despues dejo de andar?

Y no, no tendrías que reinstalar. Bastante gente hizo cosas parecidas cuando habia problemas con el video al principio de la 9.04.

---

### Post by guillermolisi on 2009-09-16
Hiciste una instalacion nueva o actualizaste ?

Envia la salida del comando lsmod, a ver si nos da algo mas de informacion.

---

### Post by GGsalas on 2009-09-17
> **guillermolisi said:**
> Hiciste una instalacion nueva o actualizaste ?

Envia la salida del comando lsmod, a ver si nos da algo mas de informacion.

Guillermo, hice una instalacion de cero para poder usar ext4 :D

```
gabi@gabi-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
joydev                 18496  0 
snd_ali5451            27276  3 
snd_ac97_codec        112292  1 snd_ali5451
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
hostap_pci             57360  0 
snd_seq_oss            37760  0 
hostap                113924  1 hostap_pci
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ieee80211_crypt        13444  1 hostap
pcmcia                 44748  0 
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali15x3            14724  0 
ppdev                  15620  0 
ati_agp                14988  1 
pcspkr                 10496  0 
serio_raw              13444  0 
shpchp                 40212  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
i2c_ali1535            14212  0 
agpgart                42696  2 drm,ati_agp
orinoco_pci            12928  0 
orinoco                61716  1 orinoco_pci
hermes_dld             15232  1 orinoco
hermes                 15360  3 orinoco_pci,orinoco,hermes_dld
video                  25360  0 
snd                    62756  16 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  1 snd_pcm
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
output                 11008  1 video
usbhid                 42336  0 
natsemi                35552  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Hei Ku, actualicé y al tiempo dejo de andar.

Se que no es facil el tema, estoy bastante resignado con esto. Lo bueno es que no la necesito todo el día, pero bueno, no deja de ser un problema. 
Gracias

---

### Post by Hei Ku on 2009-09-17
Volve a la version de kernel que te andaba, te acordas?

sudo apt-get install <paquete>=<version>

---

### Post by GGsalas on 2009-09-17
> **Hei Ku said:**
> Volve a la version de kernel que te andaba, te acordas?

sudo apt-get install <paquete>=<version>

por desgracia no me acuerdo. Cuando Ubuntu me pide actualizaciones de seguridad ni me fijo que es.. confío mucho en él más que en mi :D

---

### Post by pablo.s on 2009-09-17
> **GGsalas said:**
> por desgracia no me acuerdo. Cuando Ubuntu me pide actualizaciones de seguridad ni me fijo que es.. confío mucho en él más que en mi :D

Hacés perfectamente. Por fortuna
hay logs de casi todo y los de apt
se encuentran en /var/log/apt/term.log

---

### Post by Hei Ku on 2009-09-17
Si al menos te acordas la fecha aproximada, podemos ver los logs del kernel y saber cuáles versiones probar.

---

### Post by GGsalas on 2009-09-23
He vuelto a probar el .deb y veo que hay un error en la instalacion pero no puedo saber cual es. Adjunto la imágen.

---

### Post by GGsalas on 2009-09-23
No se si sirve, pero encontré que el driver tiene problemas on Xorg 1.6 [http://code.google.com/p/linuxgenius/issues/detail?id=1](http://code.google.com/p/linuxgenius/issues/detail?id=1)

Ahora probaré el driver desde Launchpad [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

---

### Post by GGsalas on 2009-09-23
:) :) ................................... :) :) 
Muchas gracias a técnicos GNU/Linux :D <www.tecnicoslinux.com.ar>

Explico lo que hice:

Entre tantas pruebas instalé un driver de Launchpad que se llama: "xserver-xorg-input-wizardpen" (aparentemente este era el problema)

Desde Synaptic busqué "wizardpen" y desinstalé ese y otro driver que encontré (no se en cual de las pruebas que hice lo instalé)

Por último, doble click a [http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb](http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb) reiniciar y :guitar:

Ya no quisiera tocar nada, pero si es posible desearía poder configurar los límites de la tabla porque ahora esta configurada algo chica... un tema menor, pero si se puede... desearía saber como :D

---

### Post by juancarlospaco on 2009-09-23
Viste que mi .deb andaba :)
En el Gimp los limites?, fijate que eso esta en las config del Gimp.

---

### Post by GGsalas on 2009-09-23
> **juancarlospaco said:**
> Viste que mi .deb andaba :)
En el Gimp los limites?, fijate que eso esta en las config del Gimp.

Gracias :D Funcinoa muy bien. 

Los límites: me refiero a que la esquina superior izquierda de la pantalla no está en la esquina superior izquierda de la tabla, sino un poco más al centro. Lo mismo sucede con la esquina inferior derecha ;)

Si se puede configurar, mucho mejor.

---

### Post by juancarlospaco on 2009-09-23
Mira que no es nunca exacto en estas, 
por que ese espacio en los bordes en Windows es donde estarian los Hotkeys,
pero solo andan en las Wacom esas Hotkeys, 
pero son como Hotkeys del teclado, nada del otro mundo.
*Por lo menos eso me dijeron a mi* :)

---

### Post by GGsalas on 2009-09-23
> **juancarlospaco said:**
> Mira que no es nunca exacto en estas, 
por que ese espacio en los bordes en Windows es donde estarian los Hotkeys,
pero solo andan en las Wacom esas Hotkeys, 
pero son como Hotkeys del teclado, nada del otro mundo.
*Por lo menos eso me dijeron a mi* :)

En uno de los tutoriales que hice vi que existe una forma de configurarlo, pero no quisiera modificar nada ya que ahora está funcionando. No ecesito que funcionen las Hotkeys, sólo aprovechar un poco más el tamaño de mi tabla ;)

---

### Post by kbzon_v8 on 2009-10-04
Hola que tal... estoy tratando de hacer andar mi tableta. me baje el .deb pero me tira este error: Error: Arquitectura incorrecta 'i386'

Tengo Ubuntu 9.04 - Jaunty Jackalope - x86_64 GNU/Linux y mi tableta es una Genius Pensketch 12x9.

cual puede ser el problema?

desde ya muchas gracias.

===

al parecer es porque instale el x64 y este deb es para x32 puede ser? si es asi que tendria q hacer? instalar el de 32 no? o hay algun deb con los controladores para x64?

Gracias de nuevo.

---

### Post by josecuervo86 on 2009-10-04
El problema es que el deb de juancarlos es para arquitecturas de 32 bits (i386) y vos usas 64 bits (x86_64)

---

### Post by juancarlospaco on 2009-10-06
pregunto, ...no se puede con el dpkg y el parametro **--force-architecture=**
*o yo soñe que se podia, o estoy confundiendome*

---

### Post by LisaSimpson on 2010-08-28
hola a todos,
la semana próxima me van a traer una Genius EasyPen M610 y mi ubuntu es el 9.04 de 32 bits ¿les parece que este deb funcionará? ¿o a alguien se le ocurre algo?

pregunto por las dudas, pero siempre que he instalado cosas con mi ubuntu no he tenido que configurar nada, todo le cae bien... pero en cuanto las tabletas no sé... quisiera saber por las dudas para ir preparando tiempo de configuración si hubiera que hacer algo

un abrazo a todos y gracias desde ya!!!
):P

---

