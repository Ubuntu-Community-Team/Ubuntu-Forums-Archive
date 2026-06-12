---
title: "Conectar 2 PC's en red ¿algún tutorial para hacerlo?"
date: 2008-11-22
forum: Hardware
---

### Post by atari130xe on 2008-11-22
Gente del foro, resulta que tengo nuevos habitantes en mi casa y los cuales tienen su propia PC, el tema es que me gustaria saber si hay algun tuto de como poner las 2 PC&#347; en red con banda ancha (modem ethernet), o sea que se necesita y como hacerlo, alguno podria orientarme? nunca lo hice aclaro el punto, gracias! :)

---

### Post by guillermolisi on 2008-11-22
> **atari130xe said:**
> Gente del foro, resulta que tengo nuevos habitantes en mi casa y los cuales tienen su propia PC, el tema es que me gustaria saber si hay algun tuto de como poner las 2 PC&#347; en red con banda ancha (modem ethernet), o sea que se necesita y como hacerlo, alguno podria orientarme? nunca lo hice aclaro el punto, gracias! :)
Si solo tenes un modem que no tiene posibilidad de rutear, como son los cablemodems, y no tenes un router para colocar en tu conexion a Internet, mi consejo es poner dos placas de red en la maquina que tiene la conexion (una placa ya la tenes, te faltaria una mas).

Por que dos placas ?
Por una cuestion de seguridad. Una placa tendra la IP publica que te asigna el ISP y la otra una IP privada que le asignas vos cuando la configuras (normalmente en los bloques 192.168.0.x o 10.x.x.x). De esta forma, para que accedan a tu LAN van a tener que laburar un buen rato :).

Esa segunda placa es la que se conecta a la otra PC a traves de un cable cruzado. Si agregas un switch/router vas a tener que cambiar ese calbe por uno recto, sin cruzar.

Si queres agregar una tercer PC vas a tener que incorporar un switch (o un router/switch).

Luego, tenes que configurar el firewall de Ubuntu para que haga NAT (yo lo hice instalando y configrando Firestarter). NAT hace que las dos PCs se vean desde Internet como una sola (usan la dos la misma IP publica).

La PC que tiene las dos placas de red es la que oficia de pasarela o getway (a traves de su IP privada) para la otra PC.

La IP de la segunda PC tiene que estar en la misma red que la primera. Es decir, si la primera tiene 192.168.0.1 y 255.255.255.0 (por ejemplo) como mascara de red, la segunda deberia tener 192.168.0.2 255.255.255.0 (por ejemplo), como default gateway 192.168.0.1 (la IP de la primera) y con servidor DNS tambien la IP de la primera - 192.168.0.1.

Paro aqui para no marearte. Pregunta lo que necesites.

---

### Post by atari130xe on 2008-11-22
> **guillermolisi said:**
> Si solo tenes un modem que no tiene posibilidad de rutear, como son los cablemodems, y no tenes un router para colocar en tu conexion a Internet, mi consejo es poner dos placas de red en la maquina que tiene la conexion (una placa ya la tenes, te faltaria una mas).

Por que dos placas ?
Por una cuestion de seguridad. Una placa tendra la IP publica que te asigna el ISP y la otra una IP privada que le asignas vos cuando la configuras (normalmente en los bloques 192.168.0.x o 10.x.x.x). De esta forma, para que accedan a tu LAN van a tener que laburar un buen rato :).

Esa segunda placa es la que se conecta a la otra PC a traves de un cable cruzado. Si agregas un switch/router vas a tener que cambiar ese calbe por uno recto, sin cruzar.

Si queres agregar una tercer PC vas a tener que incorporar un switch (o un router/switch).

Luego, tenes que configurar el firewall de Ubuntu para que haga NAT (yo lo hice instalando y configrando Firestarter). NAT hace que las dos PCs se vean desde Internet como una sola (usan la dos la misma IP publica).

La PC que tiene las dos placas de red es la que oficia de pasarela o getway (a traves de su IP privada) para la otra PC.

La IP de la segunda PC tiene que estar en la misma red que la primera. Es decir, si la primera tiene 192.168.0.1 y 255.255.255.0 (por ejemplo) como mascara de red, la segunda deberia tener 192.168.0.2 255.255.255.0 (por ejemplo), como default gateway 192.168.0.1 (la IP de la primera) y con servidor DNS tambien la IP de la primera - 192.168.0.1.

Paro aqui para no marearte. Pregunta lo que necesites.

Gracias! bueno te comento que las 2 pc's (la mía y la de la otra persona) tienen placa de red, la conexion se&#341;ia speedy o alguna de ellas, los modems que envia telefonica son speedtouch o zyxel (tmb huawei) todos ethernet (a pedido) el speedtouch que yo tenia se puede configurar como router asi que si es uno de eso andaria supongo, bueno ahora tengo que esperar a la instalacion de la banda ancha y a organizarme para ver como sale.

---

### Post by guillermolisi on 2008-11-22
> **atari130xe said:**
> Gracias! bueno te comento que las 2 pc's (la mía y la de la otra persona) tienen placa de red, la conexion se&#341;ia speedy o alguna de ellas, los modems que envia telefonica son speedtouch o zyxel (tmb huawei) todos ethernet (a pedido) el speedtouch que yo tenia se puede configurar como router asi que si es uno de eso andaria supongo, bueno ahora tengo que esperar a la instalacion de la banda ancha y a organizarme para ver como sale.
Lee bien que dije que la maquina que posee la conexiona Internet es la que recomiendo tenga *dos* placas de red.

Telefonica te entrega los router en modo bridge, por lo menos era su costumbre hasta no hace mucho tiempo, por lo cual o lo usas asi y armas un script para que el modem disque y se conecte, o pones un router que lo haga por vos o lo configuras como router.

Si elegis esta ultima opcion te recomiendo este site [http://www.adslzone.net/](http://www.adslzone.net/)

---

### Post by hictio on 2008-11-22
No se muy bien tu situacion, pero lo mas facil es que te compres un router WiFi, y que lo pongas detras del modem de tu ISP, entre todas las maquinas que tengas en tu casa.

Un cable de red va del modem, a un puerto ethernet en el router, y dependiendo el modelo, tenes varios puertos ethernet para conectar varias maquinas mas, normalmente, 4 puertos; ademas de los que se conecten por WiFi.

El router, por default, les va a dar direccion IP, DNS, etc a quien se conecte.

En mi opinion personal, para una casa, es la solucion mas simple, rapida y barata, a menos, por supuesto, que tengas ganas de experimentar con un router/ firewall linux fatto in casa (que por supuesto, podes incorporar luego a pesar de ya tener un router WiFi), o que necesites implementar controles de trafico, entrada/ salida, controles de ancho de banda, etc.

---

### Post by atari130xe on 2008-11-23
> **guillermolisi said:**
> Lee bien que dije que la maquina que posee la conexiona Internet es la que recomiendo tenga *dos* placas de red.

Telefonica te entrega los router en modo bridge, por lo menos era su costumbre hasta no hace mucho tiempo, por lo cual o lo usas asi y armas un script para que el modem disque y se conecte, o pones un router que lo haga por vos o lo configuras como router.

Si elegis esta ultima opcion te recomiendo este site [http://www.adslzone.net/](http://www.adslzone.net/)

Ahora entendí 2 placas en mi pc seria la de la conexion... gracias again :)

---

### Post by atari130xe on 2008-11-23
> **hictio said:**
> No se muy bien tu situacion, pero lo mas facil es que te compres un router WiFi, y que lo pongas detras del modem de tu ISP, entre todas las maquinas que tengas en tu casa.

Un cable de red va del modem, a un puerto ethernet en el router, y dependiendo el modelo, tenes varios puertos ethernet para conectar varias maquinas mas, normalmente, 4 puertos; ademas de los que se conecten por WiFi.

El router, por default, les va a dar direccion IP, DNS, etc a quien se conecte.

En mi opinion personal, para una casa, es la solucion mas simple, rapida y barata, a menos, por supuesto, que tengas ganas de experimentar con un router/ firewall linux fatto in casa (que por supuesto, podes incorporar luego a pesar de ya tener un router WiFi), o que necesites implementar controles de trafico, entrada/ salida, controles de ancho de banda, etc.

si yo habia pensado en eso tmb del router wifi pero hay que implementar claves y filtros para que otros no utilicen la conexion y me quiten ancho de banda no?

---

### Post by atari130xe on 2008-11-23
> **hictio said:**
> No se muy bien tu situacion, pero lo mas facil es que te compres un router WiFi, y que lo pongas detras del modem de tu ISP, entre todas las maquinas que tengas en tu casa.

Un cable de red va del modem, a un puerto ethernet en el router, y dependiendo el modelo, tenes varios puertos ethernet para conectar varias maquinas mas, normalmente, 4 puertos; ademas de los que se conecten por WiFi.

El router, por default, les va a dar direccion IP, DNS, etc a quien se conecte.

En mi opinion personal, para una casa, es la solucion mas simple, rapida y barata, a menos, por supuesto, que tengas ganas de experimentar con un router/ firewall linux fatto in casa (que por supuesto, podes incorporar luego a pesar de ya tener un router WiFi), o que necesites implementar controles de trafico, entrada/ salida, controles de ancho de banda, etc.

Si lo habia pensado pero como dije mas arriba tendria que implementar filtros y claves para que no me roben ancho de banda (fuera de mi casa claro)

---

### Post by guillermolisi on 2008-11-23
> **atari130xe said:**
> si yo habia pensado en eso tmb del router wifi pero hay que implementar claves y filtros para que otros no utilicen la conexion y me quiten ancho de banda no?
Si vas a usar red alambrica no hace falta todo eso. Podes inhabilitar la red inalambrica del router hasta que tengas necesidad de usarla (cuando te visite alguien con una notebook o habiendo incorporado placas de red inalambricas a tu LAN domestica).

De todas formas, configurar la seguridad de una red inalambrica en el router es cada vez mas sencillo.

Hace cuentas porque economicamente hablando no es lo mismo una solucion que la otra (usar una PC como gateway vs router inalambrico).

---

### Post by zeroadrenaline on 2008-11-25
La respuesta a tu pregunta depende de varios factores a saber:
Queres la solucion facil o la dificil?.
Rapida o trabajosa?.
Costosa(arriba de $300) , medianamente costosa (promedio $200), economica($100 o menos)?.
Respuesta 1: Rapida, Costosa, Facil: router wifi mas cables.
Motivos: Costosa, los roter wifi, no acces point estan entre 250 y 300, mas los cables, puede doler un poco.Un nene manco de 4 años configura un router en 5 minutos, 
Respuesta 2:Rapida, Medianamente costosa, facil:router ethernet mas cables.
Motivos: Menos Costosa, los roter ethernet, dependiendo del modelo, rondan los $200 quisas menos, mas los cables.Idem 1, un nene manco de 4 años configura un router en 5 minutos.
Desventajas, cables tirados por toda la casa.
Ventajas, mayor velocidad de tranferencia de datos en la red interna o LAN.
Respuesta 3:Trabajosa, economica, dificil: 2 placas ethernet en tu maquina, una que va conectada al modem, y la otra a la otra maquina. Motivos:Visto y considerando que no tenes un gran conocimiento den administracion de redes (que no se entienda esto como un acto de sobervia, yo se dos porotitos mas que vos posiblemente, o nisiquiera), este puede ser un proceso mas dificultoso.Como primera medida, deverias de dejar tu maquina encendida permanentemente, y conectada a internet para brindarle servicio a la otra maquina,  previa instalacon de una segunda placa de red en tu gabinete.
Importante aclarar que nececitaras un cable cruzado para conectar tu pc a la otra, no uses uno recto porque no labura.
Te recomiendo que leas un thread que te puede orientar un poquito en lo que es la configuracion de las dos maquinas para poder darle internet a la maquina que te cayo ahora.

[http://ubuntuforums.org/showthread.php?t=947350](http://ubuntuforums.org/showthread.php?t=947350) el post #55 aclara como configurar tu maquina para que funcione como servidor de internet de la otra maquina.

La verdad no te recomiendo esta ultima alternativa, salvo que tengas tiempo y quieras aprender a l afuerza.
Lo mas sano, para tu mente y bolsillo, comprate un router ethernet, dos cables rectos, y lee en google cualquier post de configuracion de redes ethernet, es realmente muy sensillo de conceguir.
Si tenes problemas, pregunta de nuevo, de ultima postea qu elink seguiste asi es mas facil aclarar dudas.

---

### Post by faktorqm on 2008-11-26
Yo digo: si tenes un modem ruteable, para speedy o esas cosas, lo configuras en modo router y listo, (sino sabes postea y te ayudamos)
y te compras un switch de los torabas (noganet por ejemplo) que para lo que vos necesitas andan _perfectamente_ y uno de 5 bocas o 8 bocas sale 50 pesos (no se la inflacion, vió). Pones, un cable de red del modem al switch, y uno de cada pc al switch, y listo el pollo, pelada la gallina. No tenes que tocar nada por que el router tiene server dhcp asi que te asigna las direcciones automaticamente, lo mismo con los dns. Salu2!!!

---

### Post by zeroadrenaline on 2008-11-26
Ad-hiero a la respuesta de Martin, siempre y cuando tengas speedy como servicio de internet, y te hayan dado un modem ZyXel, de lo contrario, no sabria decirte a ciencia cierta si es conveniente, el switch.
Si no es ZyXel, y no tenes la certeza de poder configurar el modem como router, mejor comprate un router ethernet, ademas ya te queda para futuros laburos.

---

