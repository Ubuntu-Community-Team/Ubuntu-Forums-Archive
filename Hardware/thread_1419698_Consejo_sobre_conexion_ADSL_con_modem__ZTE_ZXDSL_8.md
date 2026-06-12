---
title: "Consejo sobre conexion ADSL con modem  ZTE ZXDSL 831"
date: 2010-03-02
forum: Hardware
---

### Post by atari130xe on 2010-03-02
Muy buenas foro, les pido consejos para lo siguiente:
Solicité Speedy y me enviaron un modem Ethernet ZTE ZXDSL 831 (se parece al Huawei) y tengo 2 PC's para conectar al mismo.

1) Deseo utilzar la conexión de manera permanente con ambas computadoras (que ninguna dependa de la otra, o sea que no deba tener una encendida para que se conecte la otra).

2) Debo poner el modem en modo router y agregarle un router? en ese caso debería configurar el router de alguna manera en especial o simplemente conectar las placas de red a los 2 puertos del router?

Espero consejos, muchas gracias!

PD: Estoy averiguando y encontré info en el sitio de Speedy sobre como rutear este modem: [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=")

---

### Post by guillermolisi on 2010-03-02
> **atari130xe said:**
> Muy buenas foro, les pido consejos para lo siguiente:
Solicité Speedy y me enviaron un modem Ethernet ZTE ZXDSL 831 (se parece al Huawei) y tengo 2 PC's para conectar al mismo.

1) Deseo utilzar la conexión de manera permanente con ambas computadoras (que ninguna dependa de la otra, o sea que no deba tener una encendida para que se conecte la otra).

2) Debo poner el modem en modo router y agregarle un router? en ese caso debería configurar el router de alguna manera en especial o simplemente conectar las placas de red a los 2 puertos del router?

Espero consejos, muchas gracias!

PD: Estoy averiguando y encontré info en el sitio de Speedy sobre como rutear este modem: [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=)
Si pones en modo router al ZTE solo te hara falta un switch (mas economico que un router) y ahi conectas la dos PCs en forma permanente y con ip fijas o dinamicas (para esto ultimo deberas habilitar algun servidor interno DHCP, ya sea en una maquina o en el router mismo).

Si el ZTE no esta como router, podes agregar un router que lo conectas al modem, por un lado, y ahi las PCs, por el otro. La gestion de IPs es equivalente al caso anterior.

Personalmente preferiria usar el modem como router, es mas barato y tenes conexion inmediata cuando inicias Ubuntu ya que el discado lo hace el mismo equipo.

---

### Post by atari130xe on 2010-03-02
> **guillermolisi said:**
> Si pones en modo router al ZTE solo te hara falta un switch (mas economico que un router) y ahi conectas la dos PCs en forma permanente y con ip fijas o dinamicas (para esto ultimo deberas habilitar algun servidor interno DHCP, ya sea en una maquina o en el router mismo).

Si el ZTE no esta como router, podes agregar un router que lo conectas al modem, por un lado, y ahi las PCs, por el otro. La gestion de IPs es equivalente al caso anterior.

Personalmente preferiria usar el modem como router, es mas barato y tenes conexion inmediata cuando inicias Ubuntu ya que el discado lo hace el mismo equipo.

Como siempre muchas gracias Guillermo, compraré un switch entonces, el tema es que lo que quiero es evitar que para que una de las pc tenga conexión dependa de que la otra o sea que permanezca encendida y conectada a Internet. Voy a averiguar lo del servidor DHCP (no tengo idea de como se hace pero leyendo se llega a Roma no? ;) .

---

### Post by guillermolisi on 2010-03-02
> **atari130xe said:**
> Como siempre muchas gracias Guillermo, compraré un switch entonces, el tema es que lo que quiero es evitar que para que una de las pc tenga conexión dependa de que la otra o sea que permanezca encendida y conectada a Internet. Voy a averiguar lo del servidor DHCP (no tengo idea de como se hace pero leyendo se llega a Roma no? ;) .
Los routers contemporaneos incluyen ese servicio de asignacion dinamica de IPs via DHCP para la LAN, asi que es cuestion de ver como activarlo y configurarlo en el ZTE y listo. No te vuelvas loco con eso instalando paquetes que en realidad no necesitas.

Tu idea esta bien clara y de alguna de las dos formas que te comente podes lograrlo. Las PCs tendran conexion a Internet en forma independiente. Lo unico que compartiran es la IP publica ya que saldran por el mismo enlace, pero esto es transparente para el uso corriente y diario.

---

### Post by atari130xe on 2010-03-04
Guillermo tendrías algún Switch en especial que conozcas como para recomendarme? obvio no más de 5 puertos en lo posible porque estuve mirando y vi de 8, 16, 24 etc. y tengo solo 2 PC's.
Gracias!

PD: Si en lugar de switch instalo un Hub seria mas sencillo y funcionaria? o debo usar un switch?

---

### Post by guillermolisi on 2010-03-04
> **atari130xe said:**
> Guillermo tendrías algún Switch en especial que conozcas como para recomendarme? obvio no más de 5 puertos en lo posible porque estuve mirando y vi de 8, 16, 24 etc. y tengo solo 2 PC's.
Gracias!

PD: Si en lugar de switch instalo un Hub seria mas sencillo y funcionaria? o debo usar un switch?
Salvo que alguien lo encuentre tirado debajo de un monton de cosas viejas, lo desempolve y funcione, no conseguis hubs porque fueron reemplazados por switchs.
El switch posee cierta inteligencia que el hub nunca tuvo y por eso funcionan mejor, aun cuando son pocas las PCs en la red.

En mi casa tengo un Encore de 8 bocas de 10/100 Mbps con un pequeño buffer que da servicio a una red de entre cuatro a seis PCs, entre cableadas e inalambricas. Nunca tuve problemas, asi que no me puedo quejar.

Para el laburo compramos unos switch de 16 bocas marca Linksys, cableadas, de 10/100 Mbps que son un fierrazo. Pero la diferencia de precio entre el Encore y ese Linksys es abismal (un poco por la cantidad de bocas, otro por la marca y el resto porque debe ser "otro" tipo de switch).

Instalar un hub es exactamente igual a instalar un switch para tu caso.

---

### Post by atari130xe on 2010-03-04
> **guillermolisi said:**
> Salvo que alguien lo encuentre tirado debajo de un monton de cosas viejas, lo desempolve y funcione, no conseguis hubs porque fueron reemplazados por switchs.
El switch posee cierta inteligencia que el hub nunca tuvo y por eso funcionan mejor, aun cuando son pocas las PCs en la red.

En mi casa tengo un Encore de 8 bocas de 10/100 Mbps con un pequeño buffer que da servicio a una red de entre cuatro a seis PCs, entre cableadas e inalambricas. Nunca tuve problemas, asi que no me puedo quejar.

Para el laburo compramos unos switch de 16 bocas marca Linksys, cableadas, de 10/100 Mbps que son un fierrazo. Pero la diferencia de precio entre el Encore y ese Linksys es abismal (un poco por la cantidad de bocas, otro por la marca y el resto porque debe ser "otro" tipo de switch).

Instalar un hub es exactamente igual a instalar un switch para tu caso.

Mil gracias!

---

### Post by atari130xe on 2010-03-05
Pc's conectadas de la siguiente forma:
Modem ADSL: ZTE ZXDSL 831 II (Configurado en modo router)
Switch    : TP-LINK TL-SF1005D (5 puertos)
resultado: todo funciona perfecto sin configurar nada en ninguna de las 2 PC's
Gracias!

---

### Post by guillermolisi on 2010-03-05
Buen trabajo ! :)

---

