---
title: "problema para rutear modem"
date: 2009-06-18
forum: Hardware
---

### Post by feche_mza on 2009-06-18
asi de simple no puedo entrar a 192.168.1.1 para configurar mi modem como ruter , no se por que, ya probé con varios navegadores como firefox konqueror, opera y nada, y lo peor es que no se me conecta automáticamente con pppoeconf, tengo que andar reiniciando la conexión con /etc/init.d/networking restart, alguna idea de que puedo hacer??...muchachos:P

---

### Post by pablo.s on 2009-06-18
Marca y modelo del modem?

---

### Post by luks911 on 2009-06-18
Eso, marca y modelo :P
En mi experiencia, con un Zyxel 6**, para configurarlo por primera vez como router debía hacerlo a esa dirección (192.168.1.1) pero por telnet.

---

### Post by feche_mza on 2009-06-18
es un ZTE 831 series

---

### Post by pablo.s on 2009-06-18
Por lo que veo en la
pagina de Timofonica
estas haciendo el
procedimiento correcto...
Probaste con resetearlo?

---

### Post by guillermolisi on 2009-06-18
Con resetearlo queres significar volverlo a los valores de fabrica, cierto ?

---

### Post by pablo.s on 2009-06-18
Supongo. Que te parece 
el consejo?

---

### Post by luks911 on 2009-06-19
Sumo un par de dudas y sugerencias. 
1) Para poder acceder a la ip del router, ¿no debería antes configurar los datos de ip de la PC, máscara de red y puerta de entrada en Ubuntu?
2) Mirate este tutorial[0], aunque no va a servir de mucho hasta que puedas entrar a la configuración por web.
3) Esto lo pienso relacionado con 1), ¿cuál es el contenido de tu archivo /etc/netrwork/interfaces ? Para saberlo, en una terminal ejecutá

```
cat /etc/netrwork/interfaces
```

lo que te devuelve es el contenido del archivo.

[0] [http://tecnicoenlaplata.blogspot.com/2008/08/un-mnimo-apunte-cmo-configurar-el-modem.html](http://tecnicoenlaplata.blogspot.com/2008/08/un-mnimo-apunte-cmo-configurar-el-modem.html)

---

### Post by guillermolisi on 2009-06-19
> **pablo.s said:**
> Supongo. Que te parece 
el consejo?
Esta bueno pero siempre lo considero de ultima instancia, cuando se te quemaron todos los papeles y no hay otra cosa que hacer (con lo cual no importa volverlo a valores de fabrica ya que de todas formas no es funcional).

---

### Post by feche_mza on 2009-06-20
si lo resetie de ahí vino el problema, 
aver la cosa es así, hace tiempo yo tenia dualboot, ubuntu-xp, y tuve un problema parecido, entonces me dijeron aca en el foro que lo rutee al modem, y lo hice desde xp y quedo asi, pero ahora formatie y saque windows, y el kubuntu no conectaba, asi que se me dio por resetearlo y configurar la conexión con pppoeconf, pero mágicamente dejo de conectarse de forma automática, entonces dije "bue'...lo ruteo de nuevo," y no pude entrar a 192.168.1.1> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
ese el el contenido de /etc/network/interfaces

---

### Post by mama21mama on 2009-06-20
asi ruteo mi modem/router xavi:

> sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0

asi lo dejo para entrar con:

> [http://192.168.1.1/](http://192.168.1.1/)

lo otro depende tu modelo ):P

---

### Post by feche_mza on 2009-06-20
nop, logre entrar a 192.168.1.1 y rutear el modem, pero después de  que reinicia el modem no conecta alguna otra idea??

---

### Post by mama21mama on 2009-06-20
con un reset, se solucionara.

---

### Post by faktorqm on 2009-06-21
moderador pelado y muy molesto ¬¬

[http://www.sismonda.com.ar/node/56](http://www.sismonda.com.ar/node/56)

---

### Post by Hei Ku on 2009-06-21
> **faktorqm said:**
> de buscar en google ni hablar no?

[http://www.sismonda.com.ar/node/56](http://www.sismonda.com.ar/node/56)

Sabes que la busqueda en Google es recomendada, pero no requerida para postear una pregunta acá.

Contamos con que buenas personas como vos dirijan a la gente a los sitios que tienen la información correcta. ;)

---

### Post by faktorqm on 2009-06-21
si pero para mi no lo esta reseteando a valores de fabrica. cuando lo puedas hacer, segui el tuto que te pase. si buscabas en google te aparecia el procedimiento, a pesar de lo que diga el pelado. salu2!

---

### Post by feche_mza on 2009-06-24
nop... no sirve el tuto ese, y si esta con los valores de fabrica ya lo eh reseteado como 90 veces

---

