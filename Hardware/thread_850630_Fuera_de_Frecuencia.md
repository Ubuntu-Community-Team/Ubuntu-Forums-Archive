---
title: "Fuera de Frecuencia"
date: 2008-07-05
forum: Hardware
---

### Post by Guo on 2008-07-05
Hola a todos, soy nuevo en el mundo UBUNTU y ya necesito de su ayuda; hace rato que intento instalar el SO desde el cd y cuando esta por iniciar la platafoirma operativa mi monitor (LG 500 g)se pone negro y muestra un cartel de fuera de frecuencia. Tienen alguna solucion?

---

### Post by Mauro22 on 2008-07-05
Apreta:

Control + Alt + + (o sea, control alt mas).


Hacelo varias veces hasta que se vea...


Sino vas a tener que bajar la version Alternate, que se instala mediante la consola.

---

### Post by pablo0469 on 2008-07-07
Bue, iba a postear y justo me encuentro con esto que viene al pelo.

Tengo ese mismo monitor y basicamente el mismo problema, pero al disparar aplicaciones (se pone la pantalla negra, leyenda "fuera de rango 83.1 KHz / 65 Hz" y cuelgue completo del sistema), y a esta altura ya no bajo mas Live-CDs, me bajo los Alternate...

Hago Ctrl + Alt + + y no pasa nada.

Hago la misma preguna ¿Tiene solucion?

Gracias y saludos.

---

### Post by faktorqm on 2008-07-08
Proba de entrar en modo vga o de ajustarle la resolucion, aunque creo que de todas maneras no funciona.... pero bueno. Sino ponele editar las opciones las opciones de booteo y agrega la linea "vga=761" (sin comillas) a ver que pasa. Salu2!!

---

### Post by fedescha on 2009-04-11
Hola: tengo el m ismo problema.
Cuando inicio la pc aparece en un cuadro el siguiente mensaje:

Fuera de frecuencia 
HF  63.9 KHz
VF  60.0 Hz
Frecuencia de Operacion
HF  30-54 KHz
VF  50-12 Hz
Gestion de energia (timer -19)+

Supongo que me dice cual es el rango de frecuencia en el que tengo que trabajar el monitor, pero la pregunta es: ¿como lo modifico si no puedo entrar al sistema?

Saludos,

---

### Post by Hei Ku on 2009-04-11
Probaste entrar en modo de recuperacion?

La otra prueba es:
Apretas Ctrl + Alt + F1 y te logueas por terminal
Una vez adentro, pones:

sudo dpkg-reconfigure -phigh xserver-xorg

Si con esto no anda, necesitariamos saber el modelo de tu monitor, y el contenido del archivo /etc/X11/xorg.conf

---

### Post by ramiro_md on 2009-04-11
Ami me pasó igual en Debian Lenny. Configuré a mano el xorg, la parte del monitor y salió andando.

---

