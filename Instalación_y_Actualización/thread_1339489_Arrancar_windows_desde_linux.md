---
title: "Arrancar windows desde linux"
date: 2009-11-27
forum: Instalación y Actualización
---

### Post by Blackaiser on 2009-11-27
Hola, he probado arrancar windows desde linux y funciona impecable, a excepcion del asunto de la tarjeta de video que obviamente no funciona al 100% pero aperra genial.

La pregunta que tengo es:

Tengo Linux ubuntu 9.10 en un disco y en otro windows xp, no tengo el asunto de seleccionar el sistema en el arranque por que me dio problemas al instalarlo, pero me salio mejor ya que ahora si quiero arrancar windows debo precionar una tecla en el booteo y seleciono el disco desde el cual quiero arrancar y listo... nadie sabe que tengo ese virus en mi pc...

Ahora la pregunta.... se puede arrancar el winbugs que tengo instalado en ese disco desde linux? esa es la cuestión... Saludos.

---

### Post by Patriciologico on 2009-11-28
Hola, los dos sistemas no pueden estar corriendo al mismo tiempo en el mismo equipo sino es por virtualizacion. Lo que puedes hacer es crear una maquina virtual e instalarle windows, asi estaran los dos sistemas funcionando al mismo tiempo. 

[Virtualbox]("http://es.wikipedia.org/wiki/VirtualBox") te servira para eso.

Hay dos versiones la "ose" que instalas con un simple

```
sudo aptitude install virtualbox-ose
```

o la version que bajas de la pagina de Sun, que trae algunas opciones extras, pero su licencia no es completamente libre

lee mas sobre eso en [http://www.guia-ubuntu.org/index.php?title=VirtualBox](http://www.guia-ubuntu.org/index.php?title=VirtualBox)

Saludos!

---

### Post by Patriciologico on 2009-11-28
Hola, los dos sistemas no pueden estar corriendo al mismo tiempo en el mismo equipo sino es por virtualizacion. Lo que puedes hacer es crear una maquina virtual e instalarle windows, asi estaran los dos sistemas funcionando al mismo tiempo. 

[Virtualbox]("http://es.wikipedia.org/wiki/VirtualBox") te servira para eso.

Hay dos versiones la "ose" que instalas con un simple

```
sudo aptitude install virtualbox-ose
```

o la version que bajas de la pagina de Sun, que trae algunas opciones extras, pero su licencia no es completamente libre

lee mas sobre eso en [http://www.guia-ubuntu.org/index.php?title=VirtualBox](http://www.guia-ubuntu.org/index.php?title=VirtualBox)

Saludos!

---

### Post by Blackaiser on 2009-11-28
bueno.. asi lo hice anteriormente... lo que quisiera saber es si en vez de INSTALAR DE 0 el windows en la maquina virtual, puedo arrancar el sistema en el disco ya instalado.... no se si se entiende...


ejemplo paso a paso..

-. instalar el vitualbox
-. al momento de elegir particion y sistema, quiero usar los ya existentes para arranacarlos con la maquina virtual.

se puede hacer? existe algo similar?

igual gracias por la atención.;)

---

### Post by Patriciologico on 2009-11-28
La verdad no entiendo muy bien.

Pero creo confundes el disco duro físico con el disco duro virtual.

Virtualbox, crea un equipo "ficticio" para que al instalarle un sistema operativo "crea" que es un PC físico y no virtual. Si tu tienes dualboot en tu disco físico e instalas windows en un disco virtual, son dos windows distintos.

---

### Post by Patriciologico on 2009-11-28
La verdad no entiendo muy bien.

Pero creo confundes el disco duro físico con el disco duro virtual.

Virtualbox, crea un equipo "ficticio" para que al instalarle un sistema operativo "crea" que es un PC físico y no virtual. Si tu tienes dualboot en tu disco físico e instalas windows en un disco virtual, son dos windows distintos.

---

### Post by moFeta on 2009-11-29
Se puede, pero el resultado es variable, ya que se ejecuta en una máquina virtual, pero el windows que ya tienes instalado espera encontrar otro video y sonido, el del hardware real y no el virtualizado y a veces no arranca.
[http://casidiablo.net/media/correr-diferentes-so-instalados-con-vbox/](http://casidiablo.net/media/correr-diferentes-so-instalados-con-vbox/)
Lo que a mi me resulto fue virtualizar el disco duro y después instalarle windows.
Suerte.

---

### Post by Blackaiser on 2009-11-29
Eso me temía... ya que al momento de instalar el sistema virtual, lo que jode es el video... Pero bueno... gracias de todos modos, no me queda otra que seguir arrancando las particiones desde 0...

Gracias a todos por su tiempo.

---

