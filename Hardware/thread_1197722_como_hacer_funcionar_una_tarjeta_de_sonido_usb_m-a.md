---
title: "como hacer funcionar una tarjeta de sonido usb m-audio jamlab"
date: 2009-06-26
forum: Hardware
---

### Post by clave on 2009-06-26
Bueno, esta es mi duda, tengo una tarjeta de sonido Jamlab usb de la empresa M-audio y quiero hacerla funcionar en mi Vaio VGN-N160G en Ubuntu 9.04; como no funcionaba de buenas a primeras intente buscar pero no encontre mas que esto [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)  y en la lista de hardware "compatible" ( [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) ) y no esta esta tarjeta de sonido, estoy super perdido pq intenté meterme donde dice que envíe un mail si mi hardware no es soportado (aca [http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)) pero no entendi nada, e intenté abrir en "The mailing list for ALSA developers" solo veo listas de mensajes y no se donde poner; ademas no se si ahi es donde deberia estar.

ahora también me fije que si la conecto y entro al "control de volumen" aparecen 3 dispositivos nuevos: 
-Playback: Jamlab - USB Audio (PulseAudio Mixer)
-Capture: Monitor of Jamlab - USB Audio (PulseAudio Mixer)
-Capture: Jamlab - USB Audio (PulseAudio Mixer)

pero ninguno de los 3 funcionan.

que puedo hacer?

---

### Post by RafaelG on 2009-06-26
Hola Clave, Ubuntu reconoce la tarjeta, te recomiendo revisar** PULSEAUDIO** que esta en: Aplicaciones>Sonido & Video>PulseAudio>Control de Volumen y revisar que este la tarejeta M-Audio como Default para Playback, Recording, Output Device y Input Device.


Espero sea de ayuda mi Comentario
Saludos

---

### Post by Carlos C on 2009-06-26
Tengo una duda, qué te parece si con la tarjeta conectada escribes en el terminal:
```
lsusb
```Lo otro, escribe en el terminal:
```
asoundconf list
```Te dará una lista de las tarjetas de sonido disponibles. Escoge la tarjeta que deseas escribiendo:
```
asoundconf set-default-card <nombre_de_la_tarjeta>
```Y veamos si con eso funciona.

---

### Post by clave on 2009-06-26
RafaelG, pulse ausio no esta en mis aplicaciones/sonido y video, lo busqué en editar menús pero tampoco aparece.
CarlosC, hize lo que me dijite en el terminal y no paso nada, sigue sonando la Intel (del notebook) y de la Jamlab no sale nada.

---

### Post by RafaelG on 2009-06-27
Hola Clave primero que nada si tienes Ubuntu 9.04 deberias tener entonces PulseAudio que esta incluido por Default en esta ultima Version, de no ser asi puedes instalar PulseAudio desde los repositorios de Ubuntu osea desde: Sistema>Administracion> Synaptic Package Manager, te va pedir tu contrasena y podras ingresar, una vez abierto puede teclear en la casilla buscar Pulse Audio, una vez instalado pulse Audio vuelve a repetir el paso que en mi primer Post tengo. 

Disculpa trata de Pegar en tus respuestas toda la informacion que te arroja los codigos que haces en el terminal como por ejemplo lo indicado por CarlosC ya que es importante tener conocimiento de lo que arroja tu terminal

Saludos

---

### Post by clave on 2009-06-27
hola!, gracias, disculpa esque estoy aprendiendo, sabes es raro porque busque en el gestor de paquetes synaptic y decia que hay un pulse audio, pero no esta en mi menu y no esta incluso si pongo "editar menus". no se que estará pasando.

aca van los resultados 
al escribir lsusb: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0763:2013 Midiman M-Audio JamLab
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

con la tarjeta puesta al poner asoundconf list:

Names of available sound cards:
Intel
JamLab

pero si pongo asoundconf set-default-card Jamlab 
no aparece nada, solo se abre otra linea


y no funciona, sigue sonando la Intel y si cambio el dispositivo en el control de volumen por los jamlab sigue sonando el intel.

que hago?

---

### Post by RafaelG on 2009-06-27
Desde el Gestor de Paquetes Synaptic debes instalar PulseAudio, debes hacer Click derecho sobre PulseAudio y marcar para instalacion una vez hecho eso en el menu del gestor de paquetes de Synaptic haces Click en Instalar y una vez que se instale PulseAudio repites el paso de mi Primer Post en este Thread. 

Te recomiendo leas el siguiente link para informarte sobre Repositorios en el Gestor de Paquetes de Synaptic en Ubuntu.

[https://help.ubuntu.com/community/PreguntasComunes#Repositorios%20y%20sources.list](https://help.ubuntu.com/community/PreguntasComunes#Repositorios%20y%20sources.list)

Tambien te Recomiendo leas la documentacion oficial de Ubuntu cuando tengas dudas en el siguiente link

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Saludos.

---

### Post by Carlos C on 2009-06-28
> **clave said:**
> hola!, gracias, disculpa esque estoy aprendiendo, sabes es raro porque busque en el gestor de paquetes synaptic y decia que hay un pulse audio, pero no esta en mi menu y no esta incluso si pongo "editar menus". no se que estará pasando.

aca van los resultados 
al escribir lsusb: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0763:2013 Midiman M-Audio JamLab
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

con la tarjeta puesta al poner asoundconf list:

Names of available sound cards:
Intel
JamLab

pero si pongo asoundconf set-default-card Jamlab 
no aparece nada, solo se abre otra linea


y no funciona, sigue sonando la Intel y si cambio el dispositivo en el control de volumen por los jamlab sigue sonando el intel.

que hago?
Solo para estar seguros, escribiste:
```
asoundconf set-default-card Jam**l**ab 
```o
```
asoundconf set-default-card Jam**L**ab 
```De todas maneras revisa PulseAudio, también creo que es buena idea mirar por ahí. PulseAudio es el servidor de sonido. Es un proceso que corre en background. Su función es aceptar la entrada de sonido de algún proceso o dispositivo de captura y lo redirecciona a alguna tarjeta de sonido u otro proceso.

---

### Post by clave on 2009-06-28
Rafael , fui al gestor de paquetes, aparece ya instalado el Pulse Audio (ya que habia instalado el paquete ubuntustudio de audio), sin embargo reinstalé todo (todos los que dicen 1:0.9.14, el gstreamer 0.10.14 y el audacious-plugins-extra 1.5.1)  y aun asi no aparece en la lista de aplicaciones, ni en se puede agregar editando el menu, no se la verdad que estara pasando.

además, Carlos C, intenté poner JamLab (en vez de Jamlab, o jamlab) y simplemente no pasa nada, sigue sonando la Intel.

---

### Post by Carlos C on 2009-06-29
Puedes instalar el paquete padevchooser. Lo ejecutas y luego reproduces algún archivo de sonido. Si haces click sobre el ícono que aparecerá en tu panel podrás escoger entre algunas opciones básicas.

---

### Post by CdK1 on 2009-06-29
Que error te da al ejecutar un archivo de audio?, que te sale al ejecutar mplayer archivo.mp3? o cuando ejecutas con otro programa para escuchar musica, que te dice el dmesg y .xsession-error?

---

### Post by RafaelG on 2009-06-29
Hola Clave, Jamlab tiene las siguientes caracteristicas:
> Entrada de guitarra (1/4"), salida de auriculares/línea (1/8"), cable USB incorporado,calidad de audio 24 bits, 44,1/48kHzEstamos hablando de una tarjeta externa basica, Ubuntu reconoce tu tarjeta ahora debes asignar el Out and In del Notebook y para eso necesitas de un programa que en este caso puede ser  PULSEAUDIO. 

Por favor has  ALT+F2 se abrira una pequena ventana donde vas a escribir:

> pulseaudioDespues busca en la barra superior lado derecho un Plug negro ese es Pulseaudio, haces click sobre este plug negro y saldran varias opciones la cual hace click en control de Volumen y se abrira una pequena ventana de PulseAudio avisame si llegas hasta este paso.


Saludos
[FONT=Arial Narrow][SIZE=1]
[/SIZE][/FONT]

---

### Post by clave on 2009-07-02
[CdK1]("http://ubuntuforums.org/member.php?u=851995") no me sale ningun error, esque no la puedo hacer sonar, pero llegue a abrir el pulse audio, instalando el paquete que me indico Carlos C ahora en aplicaciones-sonido y video aparece un pulseaudio device chooser y un volume control, cuando abro el device chooser aparece el plug negro.

RafaelG, si esa es mi Jamlab, pero aun asi no tengo idea que hacer ahora me meto a manager pero no tengo idea, hasta ahora vamos bien asi que estare esperando sus respuestas, gracias de antemano!

---

### Post by RafaelG on 2009-07-03
> **clave said:**
> [CdK1]("http://ubuntuforums.org/member.php?u=851995") no me sale ningun error, esque no la puedo hacer sonar, pero llegue a abrir el pulse audio, instalando el paquete que me indico Carlos C ahora en aplicaciones-sonido y video aparece un pulseaudio device chooser y un volume control, cuando abro el device chooser aparece el plug negro.

RafaelG, si esa es mi Jamlab, pero aun asi no tengo idea que hacer ahora me meto a manager pero no tengo idea, hasta ahora vamos bien asi que estare esperando sus respuestas, gracias de antemano!


Hola Clave has lo siguiente: PulseAudio>Volumen control: Playback,Recording,Outputs Device y Input Device. En cada una de esas Pestanas saldra tu tarjeta Jamlab y en ese lugar seleciona tu tarjeta Jamlab, te dejo una imagen de ayuda avisa si te funciona esto.


Nota: has esto utilizando el IN & OUT de tu tarjeta Jamlab

---

### Post by clave on 2009-07-06
no me sale la opcion en playback, solo me sale System Sounds - Mono; en recording dice: No Application is currently recording audio, y jamlab aparece en el output y en el input devices, junto a la intel y metiendo mano hize como un canal donde aparecen ambas y nisiquiera se como sacar eso, intente moverl el jamlab a default pero sigue sonando la intel.

---

### Post by roccohefner on 2009-07-07
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
 
:guitar:

---

### Post by augias on 2009-07-08
He buscado info sobre tu tarjeta en los foros gringos y no hay mucho que te pueda decir. Yo no tengo muy claro la pragmatica de tu situacion y sin saber eso, decir que algo no funciona a mi no me hace sentido. 

-Cómo es tu instalacion fisica ahora, y por favor se claro para que no haya ambiguedades. Donde estan conectados tus parlantes, cuál es el propósito que le das a la tarjeta, grabacion o reproducion o ambos? 

Por el momento, te recomiendo que jueges con "jack control" en el menu de aplicaciones/sonido y video. Se que viene automaticamente en ubuntustudio y es el controldor de audio mas veloz y compatible que hay en linux. Una vez abierto, abre los "settings" y prueba con los diferentes drivers y configuraciones, aplica y cierra, apreta "play", probar y repetir el proceso jugando con diferentes posibilidades. Acuerda elegir jack como tu driver en tus aplicaciones.

---

### Post by RafaelG on 2009-07-08
> **clave said:**
> no me sale la opcion en playback, solo me sale System Sounds - Mono; en recording dice: No Application is currently recording audio, y jamlab aparece en el output y en el input devices, junto a la intel y metiendo mano hize como un canal donde aparecen ambas y nisiquiera se como sacar eso, intente moverl el jamlab a default pero sigue sonando la intel.


Hola clave estuve averiguando informacion de productos M-audio en Ubuntu y puede que necesites la actualizacion de Alsa Drivers pero para eso necesitamos saber que version de Alsa estas Utilizando escribe en un terminal y pega aca lo que te salga

```
cat /proc/asound/version
```

---

### Post by kamus on 2009-07-08
> **clave said:**
> no me sale la opcion en playback, solo me sale System Sounds - Mono; en recording dice: No Application is currently recording audio, y jamlab aparece en el output y en el input devices, junto a la intel y metiendo mano hize como un canal donde aparecen ambas y nisiquiera se como sacar eso, intente moverl el jamlab a default pero sigue sonando la intel.

[http://forums.m-audio.com/showpost.php?p=8335&postcount=5](http://forums.m-audio.com/showpost.php?p=8335&postcount=5)

:guitar:

---

### Post by clave on 2009-07-16
1.- kamus, vi el post, y gracias pero no entendi nada, tampoco entendi donde estaba la solucion al "quote" que hiciste, porfavor les ruego paciencia ya que este es mi primer thread y mi primer mes se ha ido en este thread, soy un nbie; no se que es compilar ni nada de lo que dice en ese foro; ademas mi problema es peor, porque no puedo nisiquiera escucharla aunque parece que alsa la reconociese.

2.- RafaelG puse lo que me dijiste y me salio esto:

Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

3.- Augias, gracias por responder; bueno mira repito todo claramente mi "instalacion fisica" es un notebook vaio vgn-n160g que tiene una tarjeta obviamente y sus parlantes de laptop, que es la Intel; y bueno, yo quiero hacer sonar una m-audio jamlab que es una tarjeta (de sonido) externa usb, cuyas caracteristicas son:

"Entrada de guitarra (1/4"), salida de auriculares/línea (1/8"), cable USB incorporado,calidad de audio 24 bits, 44,1/48kHz 			 		" 
fisicamente es una cajita que tiene un cable usb que va al notebook y en la caja estan tanto la entrada como la salida.

dadas las especificaciones entenderas que da lo mismo que parlantes estan conectados, cualquier cosa (audifonos parlantes, monitores, etc) conectada al out del jamlab deberia sonar si funciona.
hasta ahora no he podido nisiquiera hacer sonar un mp3 en el totem con la jamlab, que me parece lo primero antes de lo que quiero.
lo que deseo es trbajar con audio cone sta tarjeta, osea grabar y reproducir (meclar - masterizar ) musica; pero nisiquiera se para que es cada programa musical (descargé el paquete de ubuntustudio - audio); intente jugando con el jack y simplemente no logré nada mas que perder una tarde y bastante frustración.
nisiquiera aparece la jamlab en jack, pero si aparece al poner los comandos

"asound conf list"
 
y aparece en alsa drivers pero incluso he entrado en el IRC del foro y no la hemos logrado hacer sonar (nisiquiera un mp3 en el totem!) 

bueno eso. espero poder solucionarlo pronto

[FONT=monospace][/FONT]

---

### Post by RafaelG on 2009-07-16
> **clave said:**
> bueno eso. espero poder solucionarlo pronto

Hola Clave se que tu interface trabaja en Ubuntu, creo que algun paso o dificulta debes tener anexo a las soluciones que te han dado en el Foro, se que no viene al tema pero en lo personal desde que utilizo Ubuntu primero tuve dificultades con OSS y ahora ALSA un poco mejor pero todavia falta lejos mucho para ser una Excelente Architectura de Sonido, Por mi trabajo debo utilizar Pro-tools y softwares que vienen con las interfaces lamentablemente en Ubuntu no Corre ninguno de estos, tambien tengo entendido que tu interface trae un Software con multiefectos & Delay de fabricacion M-Audio que tampoco corre en Ubuntu.
   
Saludos

---

### Post by clave on 2010-03-05
logre que funcionara instalando la ultima version de ubuntu studio. gracias a todos.

---

