---
title: "como instalar ubuntu como root"
date: 2009-09-08
forum: Instalación y Actualización
---

### Post by Felipe_MayheM on 2009-09-08
ola!
mi pregunta es cunado instalo ubuntu
me pude que cree un usuario, la crearlo e instalar ubuntu
cunado ingreso a ubuntu no puedo ingresar como root, solamente como el usuario que cree, habilitar root desde consola con la pass y permitir en ventana de red

lña pregunta es hay otra forma de instalar ubuntu y que quede solamente como root altiro y no hacer estos pasos

espero que este bien mi explicacion y me puedan ayudar! 

saludos

PD: yo udo el 8.04 LTS Desktop

---

### Post by gmunioz on 2009-09-08
Hola fel...:

Por defecto, y por razones de seguridad Ubuntu

se instala con el usuario root deshabilitado 

Es posible habilitarlo, teniendo presente que el

actuar como root y en un entorno gráfico es peligroso

y desaconsejable.

Para habilitar el usuario root efectúa este 

procedimiento:

En una consola (aplicaciones - Accesorios - Terminal)

a) Te logueas como root:

    sudo su

b) Editas el archivo /etc/gdm/gdm.conf

    gedit /etc/gdm/gdm.conf

c) Lo recorres en busca de la línea que dice:

    AllowRoot=false

d) La cambias por:

    AllowRoot=true

  Y guardas el archivo

e) Creas la contraseña para el usuario root:

      passwd root

f) Reiniciamos las gráficas

    /etc/init.d/gdm restart

Ahora eliges como usuario root y la contraseña elegida

g) Y que la fuerza te acompañe.

  Ten a mano un cd live para reinstalar el sistema 

  cuando lo dañes.

---

### Post by Felipe_MayheM on 2009-09-14
si hay me resulto!! lo malo que cada vez que lo inicio  me aparece esta ventaba 


[[IMG]http://img225.imageshack.us/img225/3616/ubuntu.th.jpg[/IMG]](http://img225.imageshack.us/i/ubuntu.jpg/)


no se si se podra eliminar!! pero si puedo logearme como root

---

### Post by Maciett on 2009-09-15
Hola Felipe,

Esa ventana que te sale es lo mismo que te advirtieron en el foro, no es seguro.

Independiente que puedas quitarla o no es importante que entiendas que es peligrosa no por lo que tú puedas hacer como root, si no por lo que otros o un script que tu bajes hagan.

Una de las ventajas de linux, ubuntu de forma particular, es su buena seguridad, si te logueas como root la vulneras y das la posibilidad de hacer lo que sea.

Hazle caso a la ventana y logueate como usuario normal.

Saludos

---

### Post by Felipe_MayheM on 2009-09-15
si yo se que es por seguridad
solo que yo lo uso como medio de estudio en maquina virtual!! aun...

pero se agradece igual los comentarios y todo!!

:KS:KS:KS:KS

---

