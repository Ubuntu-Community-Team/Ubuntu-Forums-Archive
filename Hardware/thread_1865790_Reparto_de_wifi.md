---
title: "Reparto de wifi"
date: 2011-10-20
forum: Hardware
---

### Post by mama21mama on 2011-10-20
Hola,

mas que nada les comento mi proyecto aquí en mi ciudad de Lincoln, Bs As.

Queremos **repartir wifi** a un barrio que no tiene acceso a Internet.

El pc servidor es un ubuntu con proxy cache **squid+thundercache**,

En el esquema mas o menos trato de explicar como creo que ira la conexión.

El problema que me surge a mi limitado conocimiento técnico en redes, es 

como hacer que el **squid+thundercache** con ip **192.168.0.2** pueda hacer que el 

**cliente1**, **cliente2** y **cliente3** cada vez que usen el **puerto 80** pasen por el 

proxy.

No se si debería comprarme otra **targeta de red** y ponérsela al servidor y 

ver que onda.

Esa es mi duda, principalmente si así con el diagrama pueden los clientes 

usar el servidor cache o debo adquirir otro hardware como placa de red.

O si es algo de **iptables** para que los usuario al usar el 80 pasen por el 

proxy.

Sinceramente colegas ando desorientado, solo llegue a en la **pc puppy** usar 

Internet cacheada, y videos a la perfección, pero me hice un lió si los 

clientes1, clientes2 y clientes3 asi como esta podran usar cache o no.

Espero que me orienten un poco, a ver si aprendemos juntos.

Saludos

---

### Post by hictio on 2011-10-20
Si, usualmente se hace con una regla de iptables que redirecciona todo el tráfico con destino al puerto HTTP (80) hacia el puerto en el que está escuchando el Squid, puerto 3128.
Mi sugerencia, es que te simplifiques la vida, y si podés, en la computadora que va a funcionar como firewall instales una distribución de Linux creada para eso.
Un buen candidato sería [Endian, especialmente el Comunnity Edition](http://www.endian.com/en/community/overview/), que es gratis, y Open Source, y hay que no la puede probar todavía, pero que parece bastante buena, es [Zentyal](http://www.zentyal.org/), basada en Ubuntu Server (10.04, con soporte hasta el 2015).

---

### Post by mama21mama on 2011-10-20
Gracias por responder.

Estaba viendo [un hilo]("microsistemas.venezuela-foro.com/t262p15-manual-thunder-cache-30-squid-mikrotik") y en la receta mencionan 2 tarjetas de red en el servidor, una que entra la internet, la otra con salida al router wifi con el squid incluido.

---

### Post by hictio on 2011-10-20
> **mama21mama said:**
> Gracias por responder.

Estaba viendo [un hilo]("microsistemas.venezuela-foro.com/t262p15-manual-thunder-cache-30-squid-mikrotik") y en la receta mencionan 2 tarjetas de red en el servidor, una que entra la internet, la otra con salida al router wifi con el squid incluido.

Exacto, como mínimo 2 tarjetas de red.
En tu caso, quizás sería conveniente 3, una para internet, una para la red interna (verde) y una para el WiFi (azul).

---

### Post by mama21mama on 2011-10-20
Bueno, ahora esta mas claro el asunto.

Los colores son por algo en particular?

---

### Post by alfplayer on 2011-10-20
Como el objetivo es servir internet, creo que habría que encararlo desde el principio por ahí. Nunca tuve esta experiencia, pero creo que por ejemplo faltaría hacer control de tráfico para que un cliente no limite a los demás (especialmente para tráfico no HTTP que no atraviesa Squid). Habría que encontrar una solución para todo.

---

### Post by mama21mama on 2011-10-20
Por el momento solo dejare el puerto 80 y 443 abierto.

Todos los demás, cerrado. Es para que la gente que recién se inicia usen un 

mensajero o red social.

Mas adelante se vera.

---

### Post by hictio on 2011-10-20
> **mama21mama said:**
> Por el momento solo dejare el puerto 80 y 443 abierto.

Todos los demás, cerrado. Es para que la gente que recién se inicia usen un 

mensajero o red social.

Mas adelante se vera.

Una pequeña acotación, estrictamente para limitar la salida a internet con sólo los destinos 80 y 443 no necesitás un proxy Squid, podés hacerlo sólo con el firewall.

---

### Post by mama21mama on 2011-10-21
Claro si; obvio. El [Squid]("http://www.albasol.info/index.php/foros/index.php?topic=69.0") lo uso para que mi subida de 60KB/s se multiplique a 25MB/s

Como hago esto?.... Simple uso Squid+Thundercache

Todas las peticiones de mis futuros Clientes la primera vez usaran la banda 

de 60KB/s que es mi Internet de subida.

La segunda vez en la petición de una web, mis clientes usaran la pagina que 

alojada en mi servidor, así funciona squid, luego en X tiempo la pagina se 

borra y el proceso reiniciara de nuevo. El thunder cache lo uso para el 

tema videos, dinámicos de los servicios conocidos.

---

### Post by juancarlospaco on 2011-10-21
**sudo apt-get install wondershaper**

---

