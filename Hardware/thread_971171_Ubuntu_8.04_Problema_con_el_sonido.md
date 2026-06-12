---
title: "Ubuntu 8.04 Problema con el sonido"
date: 2008-11-04
forum: Hardware
---

### Post by piruchin on 2008-11-04
Ante todo deseo presentarme. Soy Sergio, desde Lobos, Argentina. Paso a describir mi problema aclarando que soy "bastante nuevo" con respecto a Linux. Me bajé la imagen de la versión 8.04, la probé y no dudé en instalarla. Quiero dejar de usar window$ y sacarle el jugo a linux en todo lo que pueda hacer. El live cd me reconoció todo, navegué en internet al toque, mi impresora epson cx4900 fue reconocida y lista para trabajar, es decir, todo bien hasta acá.

Después de instalar Ubuntu en mi pc, dejó de andar el sonido. He leido varios post de varios foros y no se para donde ir.

si ejecuto el comando lspci -v sale lo siguiente:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASRock Incorporation Unknown device 9761
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at febff800 (32-bit, non-prefetchable) [size=512]
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

si ejecuto aplay -l me dice:

aplay: device_list:205: no se encontraron tarjetas de sonido...

Sinceramente no entiendo nada, y lo que más me confunde es que con el live cd el sonido anda perfecto.

Muchas gracias de antemano. Espero que puedan guiarme para solucionar el único inconveniente que tengo.

Sergio.

---

### Post by pol666 on 2008-11-04
jaja, me parece que tenes bajos los altavoces. FIjate clickeando en el icono y despues en propiedades habilita todos los canales.

A mi me pasa que en el live tengo los altavoces altos y cuando se instala estan en mute.

---

### Post by piruchin on 2008-11-04
Gracias por la respusta amigo, pero paso a decirte que el ícono de sonido tiene el símbolo de "anulado" (?) y si hago doble clic sobre éste me sale el siguiente cartel "No se han encontrado complementos o dispositivos control de volumen de GStreamer".

:confused::confused:

---

### Post by piruchin on 2008-11-05
> **piruchin said:**
> Gracias por la respusta amigo, pero paso a decirte que el ícono de sonido tiene el símbolo de "anulado" (?) y si hago doble clic sobre éste me sale el siguiente cartel "No se han encontrado complementos o dispositivos control de volumen de GStreamer".

:confused::confused:

Ejecutando el live cd, funciona todo. si ejecuto el comando aplat -l sale:

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

y ademàs puedo ejecutar el alsamixer.


:confused::confused::confused::confused::confused:

---

### Post by faktorqm on 2008-11-05
Que raro che! A veces pasa eso de que en el live cd anda todo y despues no, pero no te preocupes, si anda tiene que andar!
¿Tenes estos paquetes instalados?

gstreamer0.10-alsa
gstreamer0.10-pulseaudio
gstreamer0.10-tools

¿Que te dice cuando queres ejecutar alsamixer?
copia y pega la salida cualquier cosa. Salu2!

---

### Post by piruchin on 2008-11-05
> **faktorqm said:**
> Que raro che! A veces pasa eso de que en el live cd anda todo y despues no, pero no te preocupes, si anda tiene que andar!
¿Tenes estos paquetes instalados?

gstreamer0.10-alsa
gstreamer0.10-pulseaudio
gstreamer0.10-tools

¿Que te dice cuando queres ejecutar alsamixer?
copia y pega la salida cualquier cosa. Salu2!


Gracias factorqm por responderme. Te comento, si ejecuto alsamixer me sale:

alsamixer: function snd_ctl_open failed for default: No such file or directory

No tengo idea de como saber so los paquetes están instalados. Me podrás guiar como hacerlo? Otra pregunta: ¿hay alguna forma de instalar los drivers de la placa de sonido a partir del live cd? Disculpame la ignorancia al preguntarte esto ya que si ejecuto el live cd el sonido funciona de 10.

Saludos.

---

### Post by llove on 2008-11-06
hola, para instalar los paquetes podes usar synaptic, que esta dentro de system, administration, y sino abris una termina y escribis
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-pulseaudio gstreamer0.10-tools

saludos

---

### Post by faktorqm on 2008-11-07
Si, tambien sino podes probar 

```
sudo dpkg-reconfigure alsa-base
```

a ver que pasa. O ya nos tendriamos que poner a compilar alsa. Salu2!

---

### Post by ariel on 2008-11-10
> **piruchin said:**
> Ante todo deseo presentarme. Soy Sergio, desde Lobos, Argentina. Paso a describir mi problema aclarando que soy "bastante nuevo" con respecto a Linux. Me bajé la imagen de la versión 8.04, la probé y no dudé en instalarla. Quiero dejar de usar window$ y sacarle el jugo a linux en todo lo que pueda hacer. El live cd me reconoció todo, navegué en internet al toque, mi impresora epson cx4900 fue reconocida y lista para trabajar, es decir, todo bien hasta acá.

Después de instalar Ubuntu en mi pc, dejó de andar el sonido. He leido varios post de varios foros y no se para donde ir.

si ejecuto el comando lspci -v sale lo siguiente:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: ASRock Incorporation Unknown device 9761
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at d800 [size=256]
    I/O ports at dc00 [size=64]
    Memory at febff800 (32-bit, non-prefetchable) [size=512]
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

si ejecuto aplay -l me dice:

aplay: device_list:205: no se encontraron tarjetas de sonido...

Sinceramente no entiendo nada, y lo que más me confunde es que con el live cd el sonido anda perfecto.

Muchas gracias de antemano. Espero que puedan guiarme para solucionar el único inconveniente que tengo.

Sergio.


Hay otra gente con el mismo problema con ese chipset de sonido, al parecer uno de los updates del kernel de 8.04 es el culpable.

x.ej: 
[http://tehpost.blogspot.com/2008/07/ubuntu-no-sound-using-intel-corporation.html](http://tehpost.blogspot.com/2008/07/ubuntu-no-sound-using-intel-corporation.html)
[http://sudan.ubuntuforums.com/showthread.php?t=966381](http://sudan.ubuntuforums.com/showthread.php?t=966381)

si despues de instalar dejaste que el sistema baje los parches de internet...eso explica porque el livecd funciona, pero no la instalacion.

... para ahorrar tiempo - te recomendaria que pruebes con 8.10

---

### Post by piruchin on 2008-11-10
:)
Hola gente!!! gracias a todos por su ayuda, en serio, gracias porque de a poco uno va conociendo Linux y "enamorándose" al mismo tiempo. Paso a contarles: cuando instalé ubuntu lo hice con el live cd sin haberlo ejecutado, es decir, desde el primer menú en donde te permite "probarlo sin alterar nada" o instalarlo. Les recuerdo que cuando lo probé antes de instalar funcionaba todo.
Decidí reinstalar ubuntu, pero esta vez primero ejecuto el live cd como para "probarlo" y verifiqué que el sonido funcionaba. Es ese momento hago clic en el ícono de instalación que está en el escritorio. 
Una vez terminada la instalación ¡¡el sonido funcionó!!!.

Muchas gracias a todos.
Sergio

---

### Post by ravl on 2008-11-10
Yo instale el Kubuntu 8.04 en mi laptop y no tuve problemas con el sonido. Ayer, haciendo experimentos dañe mi particion y tuve q reinstalar el sistema.

Recuperé mi directorio /home de mis respaldos, y el sonido dejo de funcionar. Supongo q es un problema de configuracion, es decir, sobreescribi un config en alguna parte.

Lo extraño es q no me da errores, ni mensajes en dmesg. Simplemente no suenan los parlantes.

Si alguien sabe q puede estar sucediendo, les agradezco la informacion.

---

