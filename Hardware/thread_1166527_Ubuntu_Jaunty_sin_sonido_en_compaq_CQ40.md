---
title: "Ubuntu Jaunty sin sonido en compaq CQ40"
date: 2009-05-21
forum: Hardware
---

### Post by victor maldonado on 2009-05-21
Hola a todos:
 bueno escribo por que instale en mi notebook ( compaq CQ40-305LA) la version 9.04 y al terminar la instalacion me di cuenta no que tenia sonido alguno, llegue aca siguien el antiguo foro por que habia un tema como el mismo problema pero aparecia solucion, no entiendo mucho de computadores asi que les pido ayuda urgente para solucionar mi problema por favor otra cosa segui todos lo pasos del tema del foro antiguo y no logre solucion agrego esto si sirve de algo:
lsb_release -cs
jaunty

lscpi | grep -i audio
00:1b.o Audio device: intel corportion 828001I (ICH9 Family) HD audio controller

Aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 3: INTEL HDMI [INTEL HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
vitto@vitto-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

vitto@vitto-laptop:~$ lsmod| grep snd
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

de ante mano muchas gracias

---

### Post by Carlos C on 2009-05-21
Tienes que editar el archivo alsa-base. Para eso escribe en el terminal:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```Luego añade la siguiente linea:
```
options snd-hda-intel enable_msi=1
```Después reinicia y ve si tienes audio.

Saludos.

PD1: esta solución la saqué de acá:

[http://ubuntuforums.org/showthread.php?t=912896&highlight=ich9+no+sound&page=3](http://ubuntuforums.org/showthread.php?t=912896&highlight=ich9+no+sound&page=3)

PD2: Por favor recuerda escribir títulos que sean más explicativos. "Sin sonido" no dice mucho, recuerda pensar en quienes tengan tu mismo problema y puedan estar buscando una solución. Cuando tengas dudas por favor mira las normas [acá]("http://ubuntuforums.org/showthread.php?t=1162750").

---

### Post by victor maldonado on 2009-05-21
carlos: muchas gracias pero al insertar el priimer codigo en la consola me parece:
itto@vitto-laptop:~$ lsb_release -cs
jaunty
vitto@vitto-laptop:~$ jaunty
bash: jaunty: orden no encontrada
vitto@vitto-laptop:~$ 
vitto@vitto-laptop:~$ lscpi | grep -i audio
bash: lscpi: orden no encontrada
vitto@vitto-laptop:~$ 00:1b.o Audio device: intel corportion 828001I (ICH9 Family) HD audio controller
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 
vitto@vitto-laptop:~$ Aplay -l
bash: Aplay: orden no encontrada
vitto@vitto-laptop:~$ **** Lista de PLAYBACK Dispositivos Hardware ****
bash: datos de : orden no encontrada
vitto@vitto-laptop:~$ tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
bash: tarjeta: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivos: 0/1
bash: Subdispositivos:: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivo #0: subdevice #0
bash: Subdispositivo: orden no encontrada
vitto@vitto-laptop:~$ tarjeta 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
bash: tarjeta: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivos: 1/1
bash: Subdispositivos:: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivo #0: subdevice #0
bash: Subdispositivo: orden no encontrada
vitto@vitto-laptop:~$ tarjeta 0: Intel [HDA Intel], dispositivo 3: INTEL HDMI [INTEL HDMI]
bash: tarjeta: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivos: 1/1
bash: Subdispositivos:: orden no encontrada
vitto@vitto-laptop:~$   Subdispositivo #0: subdevice #0
bash: Subdispositivo: orden no encontrada
vitto@vitto-laptop:~$ vitto@vitto-laptop:~$ lspci
bash: vitto@vitto-laptop:~$: orden no encontrada
vitto@vitto-laptop:~$ 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
bash: error de sintaxis cerca de token no esperado `('
vitto@vitto-laptop:~$ 05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
bash: 05:00.0: orden no encontrada
vitto@vitto-laptop:~$ 05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
bash: 05:00.2: orden no encontrada
vitto@vitto-laptop:~$ 05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
bash: 05:00.3: orden no encontrada
vitto@vitto-laptop:~$ 05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
bash: 05:00.4: orden no encontrada
vitto@vitto-laptop:~$ 
vitto@vitto-laptop:~$ vitto@vitto-laptop:~$ lsmod| grep snd
bash: vitto@vitto-laptop:~$: orden no encontrada
vitto@vitto-laptop:~$ snd_hda_intel         435636  5 
bash: snd_hda_intel: orden no encontrada
vitto@vitto-laptop:~$ snd_pcm_oss            46336  0 
bash: snd_pcm_oss: orden no encontrada
vitto@vitto-laptop:~$ snd_mixer_oss          22656  1 snd_pcm_oss
bash: snd_mixer_oss: orden no encontrada
vitto@vitto-laptop:~$ snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
bash: snd_pcm: orden no encontrada
vitto@vitto-laptop:~$ snd_seq_dummy          10756  0 
bash: snd_seq_dummy: orden no encontrada
vitto@vitto-laptop:~$ snd_seq_oss            37760  0 
bash: snd_seq_oss: orden no encontrada
vitto@vitto-laptop:~$ snd_seq_midi           14336  0 
bash: snd_seq_midi: orden no encontrada
vitto@vitto-laptop:~$ snd_rawmidi            29696  1 snd_seq_midi
bash: snd_rawmidi: orden no encontrada
vitto@vitto-laptop:~$ snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
bash: snd_seq_midi_event: orden no encontrada
vitto@vitto-laptop:~$ snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bash: snd_seq: orden no encontrada
vitto@vitto-laptop:~$ snd_timer              29704  3 snd_pcm,snd_seq
bash: snd_timer: orden no encontrada
vitto@vitto-laptop:~$ snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bash: snd_seq_device: orden no encontrada
vitto@vitto-laptop:~$ snd                    62628  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
El programa «snd» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install snd-gtk
bash: snd: orden no encontrada
vitto@vitto-laptop:~$ soundcore              15200  1 snd
bash: soundcore: orden no encontrada
vitto@vitto-laptop:~$ snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
bash: snd_page_alloc: orden no encontrada

y al ingresar el segundo codigo me aparece:

vitto@vitto-laptop:~$ options snd-hda-intel enable_msi=1
bash: options: orden no encontrada
lo reinicie y sigue sin sonido..
agradesco de antemano a los sabios que me puedan ayudar..

Atte

victor

---

### Post by Carlos C on 2009-05-21
Mi error, perdón, escribí mal el primer comando, el que te permite editar el archivo. Ya lo edité, así que ahora debiera estar bien. trata nuevamente con el comando corregido.

---

### Post by moreback on 2009-05-21
No es por nada pero el usuario ejecutó la salida a los comandos que él mismo posteó jojo :lolflag:

¿Es idea mía o están tratando de usar la salida HDMI?

---

### Post by Carlos C on 2009-05-21
> **moreback said:**
> No es por nada pero el usuario ejecutó la salida a los comandos que él mismo posteó jojo :lolflag:

¿Es idea mía o están tratando de usar la salida HDMI?
Es verdad, ahora que lo miro bien tienes toda la razón. De todas maneras con el comando que había escrito antes no iba a poder arreglarlo. Ahora debiera funcionar.

---

### Post by victor maldonado on 2009-05-21
carlos:

primero que todo pido disculpas por no definir bien el problema, ademas como menciones denante no se mucho de computadores, en lo posibleles pido que me den la ayuda o censejos de forma muy pedagogica jeje osea paso apaso donde poner y como poner los comandos por otro lado hice lo que me dijiste y el problema persiste.... :( que puedo hace???

---

### Post by Carlos C on 2009-05-21
> **victor maldonado said:**
> carlos:

primero que todo pido disculpas por no definir bien el problema, ademas como menciones denante no se mucho de computadores, en lo posibleles pido que me den la ayuda o censejos de forma muy pedagogica jeje osea paso apaso donde poner y como poner los comandos por otro lado hice lo que me dijiste y el problema persiste.... :( que puedo hace???
¿exactamente qué fue lo que hiciste? ¿Se abrió el editor de texto? ¿Había información en el texto o el archivo se veía vacío? ¿Añadiste la línea que te puse al final del texto?

---

### Post by victor maldonado on 2009-05-21
al introducir el codigo dado se abri el editor de texto y justamente habia codigos ahi me fui al final y debajo de la ultima linea introduje el codigo dado para poner ahi y luego reinicie

---

### Post by Carlos C on 2009-05-21
Ve a Sistema-->Preferencias-->Sonido. Prueba con los test que ahí salen y las diferentes opciones, veamos si logras escuchar algo, porque, hasta donde entiendo, esa es la forma de arreglar el problema de audio con los compaq cq40.
Saludos.

---

### Post by victor maldonado on 2009-05-21
ya he probado eso y no esucho nada, lo otro todos los dispositivos que estan ahi estan con el hadware o controlador HDA intel STAC92xx digital (ALSA) eso esta bien??

---

### Post by victor maldonado on 2009-05-22
Estimados: instale de nuevo ubuntu y segui los pasos que me dio carlos y ahora tengo sonido, pero solamente con audifonos los parlantes del note no funcionan creo que eso debe mas facil de solucionar que lo anterior (eso espero) seria mucho pedir que me ayudaran nuevamente por favor,
Atte

victor

---

### Post by Carlos C on 2009-05-22
> **victor maldonado said:**
> Estimados: pero solamente con audifonos los parlantes del note no funcionan
victor, tienes que poner cuidado con tu redacción porque no te entiendo. Por eso las comas y puntos importan. ¿Qué pasa con los audífonos?

---

### Post by victor maldonado on 2009-05-22
ok carlos en teoria segun entiendo las comas son para separar las ideas y/o dar tiempos en un texto, lo que te decia es que instale de nuevo ubuntu segui los pasos que me diste anteriormente y ahora tengo sonido pero solamente por audifonos, los altavoces no funcionan  probe el volumen y anda bien que debo hacer ahora?:D

---

### Post by felipeleven on 2009-05-22
> **victor maldonado said:**
> ok carlos en teoria segun entiendo las comas son para separar las ideas y/o dar tiempos en un texto, lo que te decia es que instale de nuevo ubuntu segui los pasos que me diste anteriormente y ahora tengo sonido pero solamente por audifonos, los altavoces no funcionan  probe el volumen y anda bien que debo hacer ahora?:D

Hola:
¿Has probado modificando los controles del volumen?

En el panel de gnome en el icono de sonido has click segundario en el botón de volumen y elige "Abrir control de volumen". Ahí se abrirá una ventana con los controles de volumen y te diran si estan activados o no, como a la vez sale un boton que dice "preferencias" donde se puede agregar controles adicionales.
Verifica la cantidad de volumen que hay como si estan activados o no, ya que en Jaunty en mi caso tenia que aumentar el volumen para escuchar.

Saludos

---

### Post by victor maldonado on 2009-05-23
Hola primero que todo gracias por la respuesta, pero lamentablemente ya lo probe los controles de volumen y no hay caso no logo hacer funcionar los altavoces del note, y otra cosa que no lo queria mencionar para no abusar es que la camara integraday el microfono integrado no los renococe y el control de volumen  activo el mic y cierro vuelvo a abrir y aparece bloqueado tendran relacion con el altavoz? bueno seguire buscando que puedo hacer con los altavoces y con la cam.

doy las gracias las personas que me han ayudado hasta ahora.

atte

victor.

---

### Post by moreback on 2009-05-24
> **victor maldonado said:**
> ya he probado eso y no esucho nada, lo otro todos los dispositivos que estan ahi estan con el hadware o controlador HDA intel STAC92xx digital (ALSA) eso esta bien??

Deberías tener otros dispositivos más ya que según tu salida del comando **aplay** porsteada originalmente tienes otros dos más. Prueba cambiando en esa misma ventana y ve si puedes reproducir sonido.

---

### Post by Carlos C on 2009-05-24
estimado, me acaban de sugerir que pruebes la siguiente solución. Escribe, por favor, las siguientes lineas al final de tu archivo /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
```

Si no arreglan el problema las borras.

Saludos.

---

### Post by moreback on 2009-06-04
> **Carlos C said:**
> estimado, me acaban de sugerir que pruebes la siguiente solución. Escribe, por favor, las siguientes lineas al final de tu archivo /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
```Si no arreglan el problema las borras.

Saludos.

Carlos_C:

Este tip me ayudó a arreglarle el sonido a un colega. Él tiene un **HP Pavillion dv5** y tenía el mismo problema que se escuchaba por la salida de audífonos pero no por los parlantes. Con esas líneas funcionó impecable.

Gracias!

---

### Post by jose.ibarra on 2009-07-10
Hola, si aun no has solucionado tu problema, lo que debes hacer es sobreescribir un archivo, como lo comentaban al inicio del tema:

sudo gedit /etc/modprobe.d/alsa-base.conf

Luego le añades lo siguiente:

options snd-hda-intel model=hp-m4

Te lo digo porque tengo el mismo notebook por el que consultas.
Aqui esta la respuesta al problema, [Chilecomparte]("http://www.chilecomparte.cl/index.php?showtopic=815970")

Ojala sirva de algo   ;)   ):P

---

### Post by danesparce on 2009-09-20
Hola!
instale ubuntu 9.04 en una compaq cq40-505la
en el archivo /etc/modprobe.d/alsa-base.conf agregue lassiguientes lineas
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel como indica anteriormente carlos y el sonido funciona bien con audifonos y altavoces pero...
no funciona el microfono integrado:(:(  
Por favor si alguien me puede ayudar 
Gracias de antemano

---

### Post by danesparce on 2009-09-20
> **victor maldonado said:**
> Hola primero que todo gracias por la respuesta, pero lamentablemente ya lo probe los controles de volumen y no hay caso no logo hacer funcionar los altavoces del note, y otra cosa que no lo queria mencionar para no abusar es que la camara integraday el microfono integrado no los renococe y el control de volumen  activo el mic y cierro vuelvo a abrir y aparece bloqueado tendran relacion con el altavoz? bueno seguire buscando que puedo hacer con los altavoces y con la cam.

doy las gracias las personas que me han ayudado hasta ahora.

atte

victor.


Hola, lograste solucionar lo del microfono??
tengo una cq40-505la y con la solucion de carlos funciono el sonido, pero me pasa lo mismo q a ti con el microfono
Gracias!

---

### Post by VonlisT on 2009-11-06
> **danesparce said:**
> Hola!
instale ubuntu 9.04 en una compaq cq40-505la
en el archivo /etc/modprobe.d/alsa-base.conf agregue lassiguientes lineas
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel como indica anteriormente carlos y el sonido funciona bien con audifonos y altavoces pero...
no funciona el microfono integrado:(:(  
Por favor si alguien me puede ayudar 
Gracias de antemano

Probaste actualizar a alsa 1.0.20 ?
Yo también tengo un laptop compaq pero de otra serie, me imagino que las características deben ser muy similares, yo también tuve el problema del sonido, sólo compilé alsa 1.0.20, reinicé el sistema, subí el volume y listo.
Te explico como:

Abre una terminal: ALT+F2 --> gnome-terminal (y apretas ENTER)
y ahora "stopeamos" alsa tecleando (copiando-pegando xD)
> vonlist@Matrix: ~$ sudo /etc/init.d/alsa-utils stop  
Ahora se compila el header y se instalan algunas herramientas:
> vonlist@Matrix: ~$ sudo apt-get -y install build-essential ncurses-dev gettext xmlto
vonlist@Matrix: ~$ sudo apt-get -y install linux-headers-`uname -r` libncursesw5-devCambiamos de directorio y bajamos los archivos necesarios...
> vonlist@Matrix# cd /opt
vonlist@Matrix: ~$ sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
vonlist@Matrix: ~$ sudo wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
vonlist@Matrix: ~$ sudo wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
Con los link de descarga debes tener cuidado, ya que el foro los resume con "..." así que debes ver los link reales haciendoles clic secundario y propiedades.
Ahora descomprimimos los archivos descargados con wget:
> vonlist@Matrix: ~$ sudo tar xjf alsa-driver*
vonlist@Matrix: ~$ sudo tar xjf alsa-lib*
vonlist@Matrix: ~$ sudo tar xjf alsa-utils*Compilamos el driver, las librerias y las utilidades:
> 
vonlist@Matrix: ~$ cd alsa-driver*
vonlist@Matrix: ~$ sudo ./configure
vonlist@Matrix: ~$ sudo make
vonlist@Matrix: ~$ sudo make install> 
vonlist@Matrix: ~$ cd ../alsa-lib*
vonlist@Matrix: ~$ sudo ./configure
vonlist@Matrix: ~$ sudo make
vonlist@Matrix: ~$ sudo make install> vonlist@Matrix: ~$ cd ../alsa-utils*
vonlist@Matrix: ~$ sudo ./configure
vonlist@Matrix: ~$ sudo make
vonlist@Matrix: ~$ sudo make installUna vez compilado todo, reinicias y verificas que tengas la versión recién instalada con:

cat /proc/asound/version

A mi me salió esto:
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Nov  6 2009 for kernel 2.6.28-16-generic (SMP).

Luego ejecutas:
sudo alsaconf
sigues las instrucciones y una vez listo, subes el volume con:
sudo alsamixer
te mueves con los cursores hacia los lados y para subir o bajar voluma, hacia arriba o abajo.
Fácil y bonito, no ?
Espero haberte ayudado

Te recomiendo actualizar el sistema antes de hacerlo, por si es que hay algún kernel disponible, así te evitas la lata de estar compilando denuevo :D
Saludos :KS

---

### Post by MDK2000 on 2009-11-08
Aqui encontre solucion para el sonido

Abres una consola y escribes:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```y al final del archivo agregas:
```
options snd slots=snd-hda-intel
options snd-hda-intel enable_msi=1 model=hp-dv5
# Intel Corporation 82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
```Espero que con eso te funcione

Para el micrófono prueba lo siguiente:

En preferencias (esto en control de volumen) agregar Captura y Captura1 que son las entradas de audio y ahí puedes subirles el volumen

Ahora te puedo decir que si instalas Karmic Koala (versión 9.10) no tendrás este problema ya que fue solucionado

Saludos

---

### Post by Carlos C on 2009-11-08
> **MDK2000 said:**
> Aqui encontre solucion para el sonido...


Gracias por el aporte, pero esa solución ya había sido posteada en este mismo hilo. Por favor recuerda leer lo que ya ha sido propuesto para que no nos repitamos.

De todas maneras se aprecia la intención.
Saludos.

---

### Post by Arielopez on 2009-12-07
Buenas, les cuento, me compre este mismo modelo, instalé con Karmic y todo va como la seda, exepto el sonido.

El problema no es que no se escuche, si no que se escucha pero no tan nítido como en windows, probé con alsamixer, y nada.

¿Que me recomendarían?

De antemano gracias.

---

### Post by moreback on 2009-12-08
¿No tan nítido? mmh... puede que te falte ajustar el ecualizador, [Banshee]("apt:banshee") viene con uno, el Rhythmbox no.

---

### Post by Arielopez on 2009-12-08
> **moreback said:**
> ¿No tan nítido? mmh... puede que te falte ajustar el ecualizador, [Banshee]("apt:banshee") viene con uno, el Rhythmbox no.

Gracias por contestar, si, también pensé en eso, pero los videos de youtube suenan igual. 

¿habrá un ecualizador para todo el sistema que no sea el alsa-mixer?

---

