---
title: "Ayuda urgente! Red e internet con xp y switch!!!!!"
date: 2008-11-12
forum: Hardware
---

### Post by alanlionheart on 2008-11-12
Hola, les comento mi problema qe me tiene buscando por todos lados, en este foro y otros por google. Acaban de comprarle una pc a mi hno (obvio con xp), y la tiene en su pieza, la cuestion es qe para ponerle internet yo qeria comprar un router y listo, problema solucionado, pero el hecho es qe mi vieja llamo a fibertel para qe le hagan la conexion con un switch qe te vienen a instalar ellos.
Cuando hicieron la conexion le dijeron a mi hno qe tardaba un rato porqe tenian qe habilitar no se qe cosa, por eso tardaba un dia y pico, pero resulta qe cuando llamo a los 3 dias para qejarse le dijeron qe de su parte estaba todo bien, qe tenia qe llamar a un tecnico personal. 
Ya me puse a configurar la conexion de la pc con XP pero muy bien no sabia, y creo qe lo mas probable es qe sea problema de esta maqina, qe se yo. Estube buscando por todo el foro pero no encontre ninguna situacion qe incluya swicth.
Desde ya muchas gracias por las respuestas, abrazo!

---

### Post by faktorqm on 2008-11-12
Es la primera vez que escucho que alguien hace eso... por eso no puedo darte una respuesta. 

Lo que hace todo el mundo es comprar un router por su cuenta, de 4 bocas por lo general, que en realidad es switch + router en el mismo aparato, y se conectan todas las pc's ahi sin que fibertel se de cuenta jamas. Pagas una, le das a todas. Salu2!!

---

### Post by guillermolisi on 2008-11-12
Es que con un switch me parece que no logras lo que queres hacer ya que necesitas definir una maquina, de las dos que tenes, como gateway a Internet y en funcion de ello configuras la otra para que pase por la primera hacia y desde Internet.

Normalmente se recomienda, por cuestiones de seguridad, que la PC que oficia de gateway tenga dos placas de red. De esta forma tenes una placa de red con IP dinamica (la que te asigna Fiber) y la otra con IP fija formando parte de tu LAN domestica que permite que la otra PC entre y salga de Internet a traves usando el switch y la PC con dos placas (gateway).

Para evitar esta movida, generalmente se instala un router que permite que todas las PCs que se le conectan "vean" Internet a traves de el.

Personalmente me gusta mas la primera opcion porque me da la sensacion de mayor control sobre la seguridad de la LAN.

Por otra parte, no tiene sentido pagarle, a Fiber ni a ningun otro ISP que te brinda un ancho de banda determinado, por tener una PC adicional conectada ya que a ellos no les modifica en nada la capacidad de servicio que pueden prestar (por mas PCs que tengas, nunca vas a superar el ancho de banda maximo que te da el enlace contratado).

Si use terminos que no comprendes, marcamelos y los paso a "criollo puro".

---

### Post by alanlionheart on 2008-11-12
Sisi, se qe es una mala indea pagarle a fibertel por hacer la conexion, pero le debo esta situacion a la mala comunicacion de padres separados. Si algien tiene alguna solucion por favor se lo agradeceria mucho, por lo menos qe configurar o por donde toqetear! gracias!

---

### Post by Mauro22 on 2008-11-12
La cosa es sencilla...


1) No se bien si Fibertel bloquea el acceso a traves de la MAC Adress. Que alguien lo confirme o desmienta.


2) Los pasos a seguir serian:

* Compras un router + switch (generalmente al pedir un router te viene con 4 bocas como dijeron arriba), con esto seguis usando el modem que te dan ellos. Del modem va un cable de red a tu PC? bien, lo sacas de ahi y lo metes en alguna boca del router y del routes cableas la tuya y la de tu hno.

* Una vez que el modem se conecta, envia internet al router, el que se encarga "de compartir" internet...


No hay mas que enchufar los cables en las 2 PC y listo. Los router de ahora vienen con un cd con un asistente demasiado facil y a prueba de neofitos.

---

### Post by alanlionheart on 2008-11-12
Te comento mauro qe la conexion ya esta echa, solo qe con un switch. El problema es qe no hay conexion en la maqina nueva y yo qeria ver si habia alguna solucion para eso. osea qe me decis qe haber comprado el switch a fibertel fue al ****?

---

### Post by guillermolisi on 2008-11-12
> **Mauro22 said:**
> La cosa es sencilla...


1) No se bien si Fibertel bloquea el acceso a traves de la MAC Adress. Que alguien lo confirme o desmienta.


Al principio hacia eso con todas las conexiones, luego y hasta la fecha, solo lo mantienen para los clientes con IP fija, aparentemente.

---

### Post by guillermolisi on 2008-11-12
> **alanlionheart said:**
> Te comento mauro qe la conexion ya esta echa, solo qe con un switch. El problema es qe no hay conexion en la maqina nueva y yo qeria ver si habia alguna solucion para eso. osea qe me decis qe haber comprado el switch a fibertel fue al ****?

Y ... no te quiero desilusionar .. pero fue mas o menos asi.

Mira, en mi casa tengo una pequeña LAN compuesta por dos maquinas con Ubuntu y dos con WinXP (Lipe se espanto cuando las vio). Oviamente uso las que tienen Ubuntu y mantengo/doy soporte a las que tienen XP (que usa el resto de la familia).
Tambien tengo un switch y uso FIbertel.

Una de las maquinas con Ubuntu es el gateway a Internet.
Para ello le puse oportunamente a esa maquina una placa de red adicional (tenia una integrada) y de esa forma tengo:

eth0 con IP dinamica a Internet (lease cablemodem)
eth1 con IP fija (al igual que el resto de las PCs) al switch.

Las PCs con Win y la otra que tiene Ubuntu server tambien van al switch y a traves de el conforman la LAN.

En cada PC configure en la placa de red que el default gateway es la IP fija de la PC que hace de gateway como tambien configure que la direccion IP del servidor DNS es esa misma (cuando instalas Firestarter te agrega funcionalidad basica de DNS server y lo deja configurado para consumir servicios de Internet).

Luego con Firestarter configure el firewall de Ubuntu en la PC con dos placas de red y listo. Todas salen a Internet con la misma IP publica, como si fuera una sola maquina (eso se llama NAT - Network Address Translation), asi que Fiber nunca supo/sabe cuantas PCs tengo conectadas.

Si ya tenes el switch solo te falta la segunda placa de red y el firestarter o equivalente.

El hecho de tener dos placas de red te brinda un margen adicional de seguridad ya que si no estableces ruteos en el firewall a traves de servicios conocidos, cualquiera que llegue a la placa publica (la que mira a Internet) de ahi no pasa.

---

