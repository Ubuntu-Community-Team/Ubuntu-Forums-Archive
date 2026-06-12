---
title: "[SOLUCIONADO] Ubuntu 8.04 &quot;dpkg --configure -a&quot;"
date: 2009-08-24
forum: Instalación y Actualización
---

### Post by jesusalcalde on 2009-08-24
hola amigos, me presento mi nombre es jesus soy de valpo y novato en el tema linux en general, les explico mi ploblema, hace unos dias instale ubuntu 8.0.4 en una laptop acer 4520 2gb en ram 120gb en disco logre instalar  Nvidia y wifi y funciona bastante bien el asunto ahora es que se bloqueo el gestor de paquetes synaptic cuando intento abrir el gestor me dice......E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report..................la verdad no entiendo que hice mal pero no puedo instalar nada 
espero sus respuestas
atte 
jesus alcalde

---

### Post by pawhtiobo on 2009-08-24
Hola :)

¿Has probado a hacer lo que recomienda lo error

Realiza en la **consola**,


[B]sudo dpkg --configure -a


[/B]Entonces, dime el resultado...

hasta ahora....

---

### Post by jesusalcalde on 2009-08-24
gracias por responder tan rapido , en consola al poner sudo dpkg --configure -a, me pidio la contraseña lo cual la puse ....enter y me dice configurando java-common y luego sale mi nombre de usuario trato de entrar al gestor de paquetes y me sale "tiene un paquete roto en su sistema"........como veo que paquete es o en consola como seria............
perdon por mi novatismo extremo 
gracias
atte 
jesus alcalde

---

### Post by pawhtiobo on 2009-08-24
hola :)

Para ver lo paquete dañado puede hacer lo siguiente:

**sudo apt-get check**

Para aprender el **apt-get** dejo aquí estes enlaces:

[http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html](http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html)

[http://es.wikipedia.org/wiki/Advanced_Packaging_Tool#Comandos](http://es.wikipedia.org/wiki/Advanced_Packaging_Tool#Comandos)

[http://www.debian.org/doc/manuals/apt-howto/index.es.html](http://www.debian.org/doc/manuals/apt-howto/index.es.html)

hasta ahora.....

---

### Post by jesusalcalde on 2009-08-24
gracias ya solucione el problema



atte 
jesus alcalde

otra vez mil gracias

---

### Post by pawhtiobo on 2009-08-24
Bueno!! :D

---

### Post by Carlos C on 2009-08-24
Hola jesusalcalde, me alegro que se haya solucionado tu problema. Nada más quería señalarte que la próxima vez que postees en el foro por favor hazlo en el subforo adecuado. He publicado un post en cada uno  donde señalo lo que corresponde publicar en ellos.
Lo otro que deseaba señalarte es que trates de siempre escoger un título que sea lo más descriptivo posible de tu problema. Te sugiero leer las normas del foro:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Movido al subforo "Instalación y actualización".
Saludos

---

