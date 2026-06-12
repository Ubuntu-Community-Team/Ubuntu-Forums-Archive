---
title: "2 puertas de enlace - desafio (?)"
date: 2009-04-24
forum: Hardware
---

### Post by Lokkete on 2009-04-24
Hola, la hago corta....

una placa de red 2 routers (2 conexinoes) es posible tener 2 ips en la placa de red para tener 2 puertas de enlace, depues por que conexion uso cada servicio es otra cosa, pero es posible esto?
una tendrias que ser dhcp y otra fija pero bue eso son detalles

ubuntu 8.10

PD: no soy abaro de no poner otra placa de red....:P es lo que necesito para evitarme 1000 problemas que no vienen al caso

---

### Post by clasificado on 2009-04-24
Si, y no, porque la verdad es que no se entiende una goma lo que querés hacer :P

Una pc puede tener cuantas ips quiera y cuantas placas quieras. lógicamente son abstraídas por las interfaces.

El camino que tomen los paquetes para llegar a destino corresponde al enrutador.

si ponés en la consola "sudo route" te dice las máscaras y que caminos toman.

Ahora, si bien es técnicamente automático (el sistema de enrutamiento), lógicamente suele ser complicado para alguien que no está acostumbrado.

Por ejemplo, No es lo mismo:
- una línea de backup: cuando la conexión se cae, que comience a responder la otra.
- un load balancer: cuando una conexión se satura, empezar a usar la otra. Eso tiene el problema de detectar cuando una conexión se satura, y al mismo tiempo respetar aquellas conexiones que tienen que ir si o si en una sola ip (ftp, https, por citar algunas)
- una intranet: separar la conexión a internet de la conexion a las computadoras locales, esto se suele usar para el server de una empresa, haciendo de proxy (aunque sea transparente) y controlando desde el servidor
- una zona desmilitarizada: esto se usa para tener un acceso a una zona que no tenga las limitaciones de firewall (y seguridad) que tiene su sistema principal

y así, siguen y siguen

clasificado

---

### Post by Lokkete on 2009-04-24
claro, el ruteo no hay drama, es mas lo hice mil veces pero con 2 placas de red

lo que me interesa investigar a mi si se puede hacer con 1 sola placa de red

seria algo como dividir la placa de red en 2 logicamente para que funcione 2 a travez de una sola placa de red 2 dos ips de distintas redes

---

### Post by Hei Ku on 2009-04-24
podes asignarle 2 ip a la placa de red. Pero creo que la salida es solo por 1.

---

### Post by Lokkete on 2009-04-24
> **Hei Ku said:**
> podes asignarle 2 ip a la placa de red. Pero creo que la salida es solo por 1.

claro, hasta donde yo se podes tener 2 config y elegir o una u otra.... pero simultaneamente? eso es lo q pregunto

---

### Post by Hei Ku on 2009-04-24
Eso es lo que quise decir.

[http://www.linuxplanet.com/linuxplanet/tutorials/6553/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6553/1/)

---

### Post by gmunioz on 2009-04-24
Hola lok....:

Lo que planteas es perfectamente posible, es mas es muy comun, dentro

de una red, armar otra red entre determinados ordenadores, por ejemplo

en una red del tipo 10.100.100.1 donde las ips se establecen por dhcp

hacer correr con esas mismas tarjetas y los mismos cables y switchs, otra

del tipo 192.168.1.1 para comunicación entre determinados ordenadores, 

en este caso con ips estáticas.

Para configurar distintas ips en una misma tarjeta de red, suponiendo que

esta sea eth0, se deberían ejecutar los siguientes comandos:

```


sudo ifconfig lo 127.0.0.1

sudo ifconfig eth0 up

sudo ifconfig eth0 172.16.3.1

sudo ifconfig eth0:1 192.168.3.100

sudo route add -net 127.0.0.0

sudo route add -net 172.16.3.0 dev eth0

sudo route add -host 172.16.3.1 dev eth0

sudo route add -net 192.168.3.0 dev eth0:1

sudo route add -host 192.168.3.100 dev eth0:1

sudo route add default gw 172.16.3.200 dev eth0

sudo route add default gw 192.168.3.100 dev eth0:1


```

En el ejemplo que planteas, los routers tendrian que estar conectados

a un switch, y actuar como gateways con distintos rangos de ip, y la

tarjeta del ordenador al switch, a traves del cual establecería 

comunicación con los routers.

Saludos.

---

### Post by Lokkete on 2009-04-25
> **gmunioz said:**
> 
```




sudo ifconfig eth0 172.16.3.1

sudo ifconfig eth0:1 192.168.3.100




```

Saludos.

:o intersante entonces cuando yo quiero programar otra red en una misma eternet tengo que agregarle el dos puntos y un nro....:O intereante...


por ahora solo me interean 2 pero si queiro agregar mas (que es muy posible el mes que viene) puedo meterle "sudo ifconfig eth0:2..." ? y meter tres conexiones?

en palabras correctas sería una placa de red funcionando como tres placas de red en forma lógica no?

tiene un limite?

PD: gracias por la data pasado mañana me traen el router y ya tenerlo solucionado es mucho...xD

y supongo que en vez de poner una ip fija puedo meterle sin drama el dhcp en la linea de  ifconfig no hay drama

---

### Post by fmsismo on 2009-04-25
Se puede hacer eso que vos queres con round-robin pero con una conexión dhcp tengo entendido que no se puede (tenes que definir los gateways en la configuración del nat y si tenes una conexión por dhcp sonaste).

Si es para una empresa, y tenes una conexión para servicios (simétrica con ip formal) y otra para navegar (dhcp asimétrica), podes con nat para donde queres que natee cada servicio rango de ip (es la típica soluciones para empresas).

Saludos

---

### Post by Lokkete on 2009-04-25
> **fmsismo said:**
> Se puede hacer eso que vos queres con round-robin ....

Saludos

mmmm por lo que estuve investigando no es muy eficiente el round-robin, me recomendaron algo como "algoritmo de proporcionalidad justa" cosa que todavia estoy investigando...¬¬

---

### Post by faktorqm on 2009-04-26
pregunta, yo hice eso en el laburo para otra cosa pero tuve que poner en el /etc/network/interfaces cada dispositivo virtual igual que lo pones vos ahi, pero tuve que levantar el modulo para controlar 802.1q y poner el switch en modo trunk para la boca que conectaba el server. ¿El no tendria que hacer lo mismo en su switch? O sea, teniendo 2 routers conectados al mismo switch cada router perteneciente a dos redes distintas, haciendo lo que posteo gmunioz, no hace falta hacer 2 vlan's en el switch? 

Yo lo que digo es, router1 con red1, router2 con red2, boca 2 del switch a router1 con vlan2, boca 3 del switch a router2 con vlan3, y pones la boca 4 en trunk y la conectas al server, luego creas, eth0 con dhcp, eth0:2 configurada con red1 y eth0:3 configurada con red2, levantas el modulo para manejar 802.1q y ya.


Salu2!

---

### Post by guillermolisi on 2009-04-26
> **faktorqm said:**
> pregunta, yo hice eso en el laburo para otra cosa pero tuve que poner en el /etc/network/interfaces cada dispositivo virtual igual que lo pones vos ahi, pero tuve que levantar el modulo para controlar 802.1q y poner el switch en modo trunk para la boca que conectaba el server. ¿El no tendria que hacer lo mismo en su switch? O sea, teniendo 2 routers conectados al mismo switch cada router perteneciente a dos redes distintas, haciendo lo que posteo gmunioz, no hace falta hacer 2 vlan's en el switch? 

Yo lo que digo es, router1 con red1, router2 con red2, boca 2 del switch a router1 con vlan2, boca 3 del switch a router2 con vlan3, y pones la boca 4 en trunk y la conectas al server, luego creas, eth0 con dhcp, eth0:2 configurada con red1 y eth0:3 configurada con red2, levantas el modulo para manejar 802.1q y ya.


Salu2!
Basicamente lo que propones es particionar el switch y que cada interface con su router se maneje en la red que le corresponde.

---

### Post by faktorqm on 2009-04-27
y si, es que creo que no conozco otra forma de hacerlo. o al menos de hacerlo "bien". ¿que dice el resto? Salu2!

---

### Post by gmunioz on 2009-04-27
Hola fak....:

Solo lo he configurado en mi trabajo y de esta forma:

Red comun a todos, servidor Suse con squid y dhcp administrando el

acceso a internet y otorgando ips por dhcp a 40 ordenadores, 

servidor de archivos con Windows server 2003 con aplicación desarrollada

en Delphy

Tres secciones, con seis ordenadores en total que corren Linux, en estos

el acceso a Internet a través del servidor Suse, con eth0 con ips por dhcp

cada sección de dos ordenadores cada una con ips estaticas en eth0:1, en

distinto rango y con grupo de trabajo propio para intercambiar archivos

mediante giver y compartir algunas tareas, entre los componentes de cada

sección.

Saludos.

---

