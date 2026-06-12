---
title: "Arnet se corta seguido"
date: 2009-07-25
forum: Hardware
---

### Post by alberto71 on 2009-07-25
Hola. 

Hace unas cuantas semanas, pasé del servicio de Arnet 640k al de 3 megas. El problema es que la conexión se cae bastante seguido. Es decir, al hacer un pppoe-status me dice que está caída la conexión. No logro casi nunca recuperarla y tengo que reiniciar la pc.

Si bien tengo el "alfajor del diablo" (Huawei MT810 luces rojas), desde hace 4 años, sé que el módem anda bien y que puede gestionar conexiones de 3 megas y más aún.

Esto me llevó a reinstalar XP :( y así ver si era problema de soft o no. En XP la conexión anda perfecto y no se cortó en semanas. Solo me queda asumir que es algo en Ubuntu pero no tengo la más mínima idea de como atacar el problema.

Algunas sugerencias para experimentar?

Gracias.

---

### Post by alberto71 on 2009-07-27
Hola.

Encontré algo que me preocupa: al ejecutar Ctrl+Alt+Fx en lugar de un prompt listo para recibir órdenes me topo con una pantalla llena de líneas con la frase:

```
Hub 1-1:1.0: Unable to enumerate usb device on port 3
```

La salida de lsusb reporta:

```
Bus 001 Device 007: ID 4c2d:2900  
Bus 001 Device 002: ID 05e3:0607 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn) ADSL WAN Adapter
Bus 002 Device 002: ID 03f0:0a01 Hewlett-Packard ScanJet 2400c
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Con lo que, al parecer, mi puerto 3 está conectado al módem usb (maldito alfajor)... Sin embargo, bajo Windows no tuve problemas de corte de conexión.

Esto me llevó a buscar un poco más y encontré que posiiblemente es un bug de Ubuntu: ver [aquí]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767") y [aquí]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273"), por ejemplo.

Aún así, me gustaría saber si alguien conoce un método de testeo del dichoso alfajor, para probar que funciona correctamente (o no) y así buscar si existe otro problema :confused:

Mucha gracias desde ya por cualquier ayuda.

---

### Post by guillermolisi on 2009-07-27
Solo para desechar posibilidades, cuando tenes la printer y el scanner conectados notas ese sintoma o siempre, sin importar que dispositivos USB tenes conectados ?

Siempre tuviste esos cortes o comenzaron a partir de cierto momento ?
Cuando el sacanner y la impresora estan apagados tambien sucede ?

---

### Post by alberto71 on 2009-07-28
Hola.

Aún con la impresora y el scanner des/conectados pasa lo mismo.

Puedo relacionar los cortes aproximadamente al cambio de velocidad de Arnet, por lo que creí era problema de ellos o del modem, pero bajo winbugs no se corta la conexión.

El problema sucede de manera aleatoria, con los periféricos usb apagados; con los equipos encendidos no me pasó que se cortara.

Sin embargo, al revisar la situación para escribir éste post, me doy con que ya no tengo esos mensajes en consola y hacen 20 horas que no se corta la conexión. No me inspira confianza, pero voy a seguir vigilando.

---

### Post by guillermolisi on 2009-07-28
Si tu maquina tiene placa Ethernet, pedi que te cambien el modem (busca una razon simple pero efectiva, por ejemplo "no me funcionan mas las bocas USB y tengo placa de red") para que te den un modem moderno y muchisimo mas estable.
Speedy accede a esas solicitudes abonando una hora de tecnico ($ARG 35.-)

Mi sugerencia es casi OT pero absolutamente practica.

---

### Post by luks911 on 2009-07-28
No sé si sumo, pero bueh... el más frecuente culpable de los cortes en la conexión está en la línea de teléfono. Además, una conexión de 3 megas necesita una línea (un cable y sus empalmes, bah) en mejor estado que una más lenta. 
No soy experto, pero hay valores de ruido en la línea que hacen que sea apta o no para determinada velocidad[0]. Y eso varía en función de la antigüedad de los cables, el estado en el que se encuentran, etc. Por ejemplo, mi conexión suele morir cuando llueve, aunque eso también depende de cuál sea la dirección del viento. En serio. Los cables llevan 20 años colgando de un poste y esa es la consecuencia cuando se los usa para proveer ADSL.
Digo, es probable que el problema tenga que ver, en efecto, con el cambio de velocidad. Lo que puede mejorar la situación es cambiar el modem por algún router un poco mejor, nada del otro mundo, que reciba mejor la señal. Noté un cambio cuando pasé del Huawei a un Zyxel, y luego a otro Zyxel con wifi. Usándolo en Win el Huawei tiene una opción para ver los valores de la línea. Si mal no recuerdo abriendo las opciones desde el triangulito del panel de tareas y presionando luego Alt+D.

[0] [http://wiki.telecomsucks.com/Valores_de_linea](http://wiki.telecomsucks.com/Valores_de_linea)

EDIT: Perdón, escribí esto sin ver el post de Guillermo, que llegó a la misma conclusión :P

---

### Post by guillermolisi on 2009-07-28
En teoria, y solo en ese ambito, el proveedor deberia ofrecer un servicio factible.

Como en la practica hay cantidad de factores, como acaba de mencionar Luks911, que el vendedor desconoce, posiblemente la calidad de los cables (ultima milla para ser mas genericos), distancia a la que estas del nodo ADSL/central telefonica de Telecom al cual estas conectado, el "alfajor del diablo" que posiblemente este llegando al final de su ciclo de servicio, etc., etc. se suman para que los 3Mb sean inviables, ya sea porque nunca los tendras o porque la conexion se torna inoperante por su inestabilidad.

---

### Post by alberto71 on 2009-07-29
Muy buenas pistas muchachos; muchas gracias por responder.

Desde el principio fue mi temor (¿¿?????) que el alfajor esté despidiéndose de a poco...

La línea no es muy nueva, tiene 5 años, así que también es buena idea pedir a Telecom que la chequeen, como quien descarta problemas. 

Supongo que será posible usar un modem o modem-router ethernet, que para mí sería lo ideal y en Ubuntu estoy seguro que van como piña, pero no sé si Telecom venda alguno, entusiasmados con vender los "sencillos" modems usb...

Gracias.

---

### Post by Mauro22 on 2009-07-29
Lo ideal es perdir que te bajen de velocidad, con eso el sincronismo no es muy grave y anda a lo que tiene que andar.


Yo tengo speedy 3m y es de terror con los microcortes, tengo qeu esperar a que cierren la factura o algo asi para bajarme a 2.5mb porque con 3mb no soporta la linea.

---

### Post by guillermolisi on 2009-07-29
Desde hace mas o menos un año Arnet/Telecom distribuye Huawei dual (USB/Ethernet) MT 882 o superior.

---

### Post by alberto71 on 2009-07-29
Ví el MT882 y parece bastante buena opción; además, lo usé en un entorno Ubuntu 8.04 - XP - Mac OS con ethernet y anduvo de lo más bien.

Tu experiencia Mauro, me deja pensando... Como el aumento fué parte de una promo, pero quizás valga la pena intentar.

---

### Post by Mauro22 on 2009-07-29
Recién llame y con el chamuyo que del speedy 2.0 y toda la bola... El cambio de velocidad esta suspendido :(

así que estoy entre la espada y la pared.


Lo que tenés que hacer es ver cuanto ruido tenés en la línea. Yo tengo 6db y li mínimo son 12 dB... Con 2.5 mb tenía 14...     Una lastima que pagando no tengo derechos

---

### Post by guillermolisi on 2009-07-29
> **Mauro22 said:**
> Recién llame y con el chamuyo que del speedy 2.0 y toda la bola... El cambio de velocidad esta suspendido :(

así que estoy entre la espada y la pared.


Lo que tenés que hacer es ver cuanto ruido tenés en la línea. Yo tengo 6db y li mínimo son 12 dB... Con 2.5 mb tenía 14...     Una lastima que pagando no tengo derechos
Pedi la baja del servicio a ver que hacen.

---

