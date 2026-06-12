---
title: "Conexion por cable Telsur"
date: 2011-02-09
forum: Hardware
---

### Post by Iced1 on 2011-02-09
Hola, como ven tengo un router telsur wifi, de modo que decidí automatizar el wifi, osea que con tan solo la clave del wifi tener internet. Sin el molesto doble marcado... 

Use esta guia:
[http://www.chw.net/foro/internet-y-redes-f24/494081-configurar-router-zhone-de-telsur-para-conectarse-a-wifi.html](http://www.chw.net/foro/internet-y-redes-f24/494081-configurar-router-zhone-de-telsur-para-conectarse-a-wifi.html)

Todo perfecto hasta ese momento, hasta que decidí instalar ubuntu 10.10 en un computador de escritorio, este al no tener wifi, tengo que configurar la red por cable, busque guias y no las encontré, me podrían ayudar a configurar la red, con las ip, etc... ?? ya que lo intente y no lo logre

Gracias de antemano

---

### Post by RafaelG on 2011-02-09
Iced1,

A continuacion dejo un Link donde detalla como hacer la conexcion de red en Ubuntu espero te sirva

[http://www.guia-ubuntu.org/index.php?title=Configuraci%C3%B3n_de_red](http://www.guia-ubuntu.org/index.php?title=Configuraci%C3%B3n_de_red)

Saludos cordiales,

---

### Post by asterix77 on 2011-02-10
Un poco extraña la situación, soy cliente de telsur y nunca he tenido problema al momento de conectarme.

Lo único que he hecho cada vez que he actualizado a una nueva versión, es correr el programa pppoeconf en la terminal. Aquí lo único que hay que hay que ingresar es el nombre de usuario y contraseña (ojo no es para conectarte al wifi, sino la contraseña pppoe), el resto se deja tal cual.

Después al reiniciar eso si, no sé porque la conexión no se hace en forma automática (en las versiones anteriores era automática), sino que debo activarla con el network-manager, esto es click derecho del mouse sobre el icono del nm en el panel, y listo.

También te puedes conectar por la terminal con el comando $pon dsl-provider (pero una vez configurado con pppoeconf), o puedes hacer un script con este comando, darle permiso de ejecución, y  después hacerle un doble cick; también puedes dejarlo para que se inicie en el arranque, etc. Las opciones son variadas.

Tu pc al conectarlo en forma directa por cable, debiera conectarse sin problema al router; los router de telsur por defecto vienen con dhcp habilitado por lo que debiera asignarte una dirección ip en forma automática una vez que te conectas por cable (salvo que hayas deshabilitado el dhcp en el router) .


De todos modos sería bueno que postearas la salida de lo siguiente en la terminal

$cat /etc/network/interfaces

Pero tengo una duda ¿ocupas el wifi o no? y si la ocupas ¿con que equipo es?¿es con tu pc de escritorio?

Saludos

---

### Post by Iced1 on 2011-02-14
Muchas gracias, lo solucione... sinceramente ya habia probado los comandos pppoeconf y dsl-provider, pero estos no funcionaban, aun así extrañamente al dia despues intente nuevamente conectame con pppoeconf, y no tuve problemas...

---

### Post by 3nG3ndR0 on 2011-02-14
> **iced1 said:**
> muchas gracias, lo solucione... Sinceramente ya habia probado los comandos pppoeconf y dsl-provider, pero estos no funcionaban, aun así extrañamente al dia despues intente nuevamente conectame con pppoeconf, y no tuve problemas...

post equivocado...

---

