---
title: "Problemas con conexion a internet"
date: 2009-03-24
forum: Hardware
---

### Post by ubles on 2009-03-24
Hola! Tengo un problema hace rato, y no he podido resolverlo. Les comento la situacion a ver si me pueden ayudar:

-Hay 4 pcs, 3 con linux y 1 con ubuntu (solo consola). 
-Las pcs se ven entre si y comparten archivos sin problemas.
-Las pcs que tienen windows tienen acceso a internet sin problemas.

-La pc que tiene ubuntu no tienen acceso a internet. Y aqui esta el problema. Si pongo exactamenten la misma confiruacion (ip, mascara, gateway) en un maquina windows anda, pero en ubuntu no.

-Las cuatro maquinas estan conectadas a un router (o tal vez a un proxy) al cual no tengo acceso.

-Cuando hago ping a [www.google.com](www.google.com) resuelve la ip (es decir el dns local funciona) pero la respuesta al ping nunca llega.

Espero sus sugerencias.
Saludos

---

### Post by Edgar09 on 2009-03-24
Hola Amigo..
Tuve un problema ALGO similar pero...... con la red inalambrica...
Lo que hice fue entrar al SO en Recovery Mode(Modo de Recuperacion) y me salio efectivo.....

---

### Post by ubles on 2009-03-25
Pero que debo cambiar en Recovery Mode, alguna configuracion? Sabes que causa el problema, si es un tema externo de la lan o de configuracion del ubuntu?

Gracias por resopnder.

---

### Post by ubles on 2009-03-25
He modificado configuraciones y buscado informacion pero no hay caso, no tengo salida externa a internet. Puede ser un problema de la LAN o sera de configuracion de Ubuntu?

Agradeceria cualquier ayuda y/o sugerencia.

Saludos

---

### Post by guillermolisi on 2009-03-26
> **ubles said:**
> Hola! Tengo un problema hace rato, y no he podido resolverlo. Les comento la situacion a ver si me pueden ayudar:

-Hay 4 pcs, 3 con linux y 1 con ubuntu (solo consola). 
-Las pcs se ven entre si y comparten archivos sin problemas.
-Las pcs que tienen windows tienen acceso a internet sin problemas.

-La pc que tiene ubuntu no tienen acceso a internet. Y aqui esta el problema. Si pongo exactamenten la misma confiruacion (ip, mascara, gateway) en un maquina windows anda, pero en ubuntu no.

-Las cuatro maquinas estan conectadas a un router (o tal vez a un proxy) al cual no tengo acceso.

-Cuando hago ping a [www.google.com](www.google.com) resuelve la ip (es decir el dns local funciona) pero la respuesta al ping nunca llega.

Espero sus sugerencias.
Saludos

Que hagas ping a un host y te conteste no significa que la resolucion de nombres este funcionando bien. Solo te dice que la conexion de red llega hasta esa maquina.

Para saber si los DNS estan operando hace en una terminal/consola:
```
sudo tracert www.google.com
```

Si los DNS funcionan bien, deberias obtener una salida similar a la que copio a continuacion:
```

traceroute to www.google.com (209.85.195.147), 30 hops max, 40 byte packets
 1  hephaestus (192.168.0.10)  0.155 ms  0.154 ms  0.150 ms
 2  200-41-61-1.static.impsat.net.ar (200.41.61.1)  8.104 ms  15.978 ms  22.473 ms
 3  200-32-127-85.static.impsat.net.ar (200.32.127.85)  12.393 ms  12.420 ms  13.368 ms
 4  redgetlp1-vlan1.impsat.net.ar (200.0.194.99)  14.419 ms  14.636 ms  14.851 ms
 5  190-216-41-30.static.impsat.net.ar (190.216.41.30)  16.181 ms  16.874 ms  17.567 ms
 6  200-55-0-53.static.impsat.net.ar (200.55.0.53)  18.263 ms  20.353 ms  20.562 ms
 7  so0-1-3-2488M.scr1.EZE1.gblx.net (67.16.160.217)  26.284 ms  23.520 ms  23.582 ms
 8  te3-1-10G.ar3.EZE1.gblx.net (67.16.132.170)  23.866 ms te-3-2-10G.ar3.EZE1.gblx.net (67.17.67.26)  24.143 ms te3-1-10G.ar3.EZE1.gblx.net (67.16.132.170)  24.717 ms
 9  64.208.27.34 (64.208.27.34)  24.402 ms  24.977 ms *
10  * * *
11  * * *
12  * * *
13  * * *
14  * 209.85.195.147 (209.85.195.147)  19.809 ms  19.801 ms
```

Si no obtenes una salida similar, entonces no tenes navegacion porque no funcionan los DNS.

Otra forma rapida de probarlo sin usar el tracert es colocar la IP en lugar de la URL en la ventana del web browser y ver si accede al sitio que buscas.

---

