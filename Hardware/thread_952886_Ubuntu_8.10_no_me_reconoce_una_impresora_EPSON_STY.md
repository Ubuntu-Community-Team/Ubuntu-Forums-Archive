---
title: "Ubuntu 8.10 no me reconoce una impresora EPSON STYLUS DX4400"
date: 2008-10-19
forum: Hardware
---

### Post by lo gambusí on 2008-10-19
Saludos!

Me llamo Oriol y vivo en Barcelona. Voy con la beta de Ubuntu 8.10.

Me he comprado una impresora EPSON STYLUS DX4400 y he seguido los pasos de [este]("http://blog.toranks.es/instalar-impresora-epson-stylus-dx4400-e") blog para configurarla. Por desgracia una vez hecho todo ni funciona el escáner ni la impresora. Os lo escribo aquí porque lo he preguntado en el Catalan Team y no han podido ayudarme, y debería devolver la impresora, si no consigo cofigurarla, antes de el miércoles.

Podríais ayudarme un poco? Os lo agradeceré de todo corazón, porque estoy un poco desesperado... :?

Gracias!!

---

### Post by Mauro22 on 2008-10-19
Bienvenido!!


Vamos por paso, calculo que esa impresora es USB, no?


* Ubuntu la reconoce?
* Postea la salida del comando ```
lsusb
```
* Con el LiveCD funciona? porque a mi me ha pasado que en el LiveCD funcionasen cosas que instalado no.
* Y lo ultimo que se me ocurre es la version, la 8.10 sigue siendo beta (aunque falta 10 dias) pero puede ser que en Hardy ande lo mas bien


Aqui tienes otra guia (ingles)
[http://ubuntuforums.org/showthread.php?t=627471](http://ubuntuforums.org/showthread.php?t=627471)


:)

---

### Post by lo gambusí on 2008-10-19
Saludos, Mauro.

lsusb me dice:

> Bus 005 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


livecd ahora mismo no tengo por aquí el del intrepid. lo miro luego ;)

---

### Post by lo gambusí on 2008-10-19
Ya he aconseguido el LiveCD del Intrepid, pero tampoco me reconoce la impresora. 

Para instalarla he provado de ir System/Administration/Printing/New Printer/APPSocket/HP Direct y seguir los pasos. Puede que me equivoque aquí y deba poner Other? (en el archivo adjunto tienes el pantallazo: screenshot.PNG).

Te adjunto otro pantallazo (capturamw1.PNG) para que veas qué me dice (el pantallazo lo he echo en la sesión live, pero me pasa exactamente lo mismo en mi sesión) una vez instalados los supuestos drivers, cuando intento hacer una impresión de prueba.

A ver si podéis ayudarme. :)

---

### Post by faktorqm on 2008-10-20
Mira este post mio, fijate de cambiar las versiones actualizadas y de ver el product ID de tu dx4400.
[http://ubuntuforums.org/showthread.php?t=730856&page=4](http://ubuntuforums.org/showthread.php?t=730856&page=4)

Salu2!

---

### Post by lo gambusí on 2008-10-20
Debo seguir tus pasos a partir de [este]("http://ubuntuforums.org/showpost.php?p=4972514&postcount=10") post, supongo?:)

---

### Post by faktorqm on 2008-10-20
ehh si, pero no, el que posteo él esta mejorado... (leer el thread...) por que habia alguna cosas que del mio original no andaban... entonces con su feedback armamos ese que es el que anda. Salu2!

---

### Post by lo gambusí on 2008-10-20
Empezamos mal... creo que no me detecta la conexión usb:> logambusi@logambusi-laptop:~$ lsusb
Bus 005 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by faktorqm on 2008-10-20
ahh bue.. primera vez que lo veo. estas frito men! salu2!

---

### Post by pol666 on 2008-10-20
Tenes dual boot con windows?

Anda bien ahi no? proba cambiando a donde conectas la impresora

---

### Post by lo gambusí on 2008-10-21
El dual boot con windows ese no lo tengo ni sé qué es. :?

Y ya he probado de canviarlo de puerto usb, pero sigue sin hacer nada... :(

---

### Post by lo gambusí on 2008-10-21
> **faktorqm said:**
> ahh bue.. primera vez que lo veo. estas frito men! salu2!

Quieres decir que no ya puedo devolver la impresora?:?

---

### Post by pol666 on 2008-10-21
Digo si tambien tenes Windows instalado o no.

por que capas, la impresora, ni anda.

---

### Post by lo gambusí on 2008-10-21
Por lo tanto *bye-bye* impresora, no?:?

---

### Post by pol666 on 2008-10-21
mmm no se, tendrias que probarla en otra pc que tenga windows para asegurarte eso...

---

