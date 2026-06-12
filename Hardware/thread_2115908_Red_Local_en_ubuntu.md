---
title: "Red Local en ubuntu"
date: 2013-02-14
forum: Hardware
---

### Post by asterix77 on 2013-02-14
Consulta a la comunidad:

Poseo dos modem/router adsl (zhone 6218),  uno de ellos conectado a la linea telefónica para acceso a Internet a mi pc con Ubuntu 12.04. A  este Modem 1, le quiero conectar el otro (Modem 2) a través de un cable  RJ45, con el objeto de:

a) Expandir mi señal wifi ya que hay lugares en mi casa en que me llega muy débil, y así obtener acceso a internet.

b) A su vez crear una LAN casera con varios pc, notebook, etc.

No  sé si se pueda, ya que estos modem, cuentan en la parte posterior con  una entrada para la linea de teléfono (RJ11), que es por donde llega la  señal de internet, y 4 entradas RJ45 numeradas como Lan1 Lan2 Lan3 Lan4.

Al menos en forma inalámbrica logro conectarme al modem 2, pero sin tener acceso a internet.

¿Alguien sabe si esto es posible?¿o si hay que configurar algo en el modem 2 o 1 para tener acceso a internet?.

Saludos

---

### Post by biale on 2013-02-14
Sin haber leido el manual de los modems te digo que en principio se puede. 

Uno de los modems se configura completo, es decir que provee/rutea internet a los ports rj45 y WIFI.El segundo modem se configura solo como salto/ cascada para interconectarse al modem anterior (no dhcp, etc). 

Si la interconexión se hace por cable UTP hay que estudiar si se requiere un cable UTP "cruzado" o el modem resuelve el cruce en alguno o todos los ports. Tendras dos redes WIFI distintas, una por modem.

Si la interconexion se hace por WIFI la cosa se complica un poco y los modems tienen que soportar esta modalidad. En este caso podrías acceder a la misma red WIFI conectandote al modem mas cercano.

---

### Post by guillermolisi on 2013-02-14
Mostranos como estan configurados cada uno de los modems, en particular lo que es WAn y LAN para el modem1 y LAN para el modem2.

Son modems o routers ?

Los routers WiFi modernos vienen con una caracteristicas llamada WDS que permite enlazarlos inalambricamente, es decir, los interconecta sin usar cable pero esto consume algo del ancho de banda disponible en el tramo del segundo router WiFi.

---

### Post by asterix77 on 2013-02-15
Estimados, gracias por su respuestas. En estos momentos, estoy en mi trabajo donde lamentablemente me obligan al uso del sistema de las ventanitas :(, pero bueno, ya llegaré a mi casita con mi ubuntu ):P.

Les cuento lo que he realizado. Despúes de tanto batallar para ingresar a la configuración de ese modem, me di cuenta de dos cosas.

a) primero hay que poner la placa de red de mi pc, en el mismo rango que la del modem/router (ya que este asigna ip automáticamente).

b) segundo, el cable RJ45, debo conectarlo a la entrada LAN1 del modem router para poder ingresar desde un navegador, en el resto me fue imposible.

El modem/router 1, el que tiene acceso a internet (M/R de ahora en adelante), tiene la ip 192.168.1.254; no toqué nada acá.

El M/R 2 lo configuré con la ip 192.168.1.10, además lo configuré con el gateway 192.168.1.254. No he tocado nada más en el. Luego conecté el M/R 2 al M/R 1 vía cable RJ45, y me conecté vía inalámbrica con un notebook al M/R 2; la conexión se establece bien, pero no tengo acceso a internet. De hecho he usado un programa llamado Fing que muestra la topología de mi red sin problemas. (192.168.1.2 que es mi notebook; 192.168.1.10 que es mi M/R 2; 192.168.1.254 que es el M/R que es el que sale a internet.

¿Será que necesito el cable cruzado?

PD: no vienen con WDS

Saludos

---

### Post by guillermolisi on 2013-02-15
Cuando decis "no tengo acceso a Internet", de que formas verificaste esto ? (ademas de la comentada con ese utilitario)

No decis nada sobre que valores le diste a los DNS de M/R 2.

---

### Post by asterix77 on 2013-02-15
Estimado:

Verifiqué mi conexión, conectando un notebook inalámbricamente al M/R 2 y abriendo un navegador web. No cargaba ninguna página.

El notebook al conectarlo también inalámbricamente al M/R 1, tenía acceso a Internet; sobre el tema de los DNS en el M/R 2, no realicé ningún cambio, de hecho el M/R 2 tiene los mismos dns que el que se conecta a internet (M/R 1).

Otra cosa, haciendo ping al M/R 1 pasando primero por el M/R 2, tengo respuesta, por lo que creo que estoy cerca.

Saludos

---

### Post by guillermolisi on 2013-02-15
El hecho de probar si hay o no conexion a Internet con un web browser no es la forma adecuada porque podes llegar a Internet sin problemas pero si no tenes bien configurado que DNS vas a utilizar no podras llegar a ningun website.

Para probar si llegas a Internet, la primera forma simple es usando ping y una direccion IP de un sitio conocido y confiable (que se sepa que siempre esta on line, caso Google, por ejemplo).
Si queres hacer una prueba equivalente usando un web browser, en lugar de poner el nombre del website tenes que usar la IP. Por ejemplo con [http://173.194.42.14](http://173.194.42.14) deberias llegar a google.com
Si probando de esta forma no llegas a sitio web, entonces hay otro problema.

Si el ping devuelve paquetes recibidos sin problema o usando el navegador web con la IP del sitio se llega perfectamente, entonces claramente te esta faltando definir que DNS usaran las maquinas que se conecten a M/R 2. Por eso mi comentario respeco de que nada dijiste sobre que valores de DNS pusiste en ese router.

Respecto de esto ultimo, tenes dos posibilidades
Definirle IPs de DNS publicos conocidos, por ejemplo los de Google
Definirle la IP interna de M/R 1 y que este se encargue de usar los DNS que tiene definidos por el administrador.

---

### Post by asterix77 on 2013-02-15
Guillermo, te comento que hoy al mediodía al ir a mi casa a almorzar, no tenía mucho tiempo para experimentar con mi red casera, por lo que lo estaba dejando para la tarde, pero por curiosidad me conecté por wifi del M/R 2 con mi smartphone, pues recordé una utilidad para realizar ping como mencionas. Tal fue mi sorpresa que realicé el ping y obtuve respuesta, luego abrí por curiosidad el navegador de mi smartphone, y :p me pude conectar sin problemas, hasta ví unos par de videos en youtube.

No sé que habrá pasado de ayer a hoy, pero lo cierto es que me funcionó mi red casera, ahora solo me resta dejar las ip fijas de mis equipos ya que aún continúan en forma dinámica; no creo tener problemas de desconfiguración  de mi red al hacer esto.

De todos modos, no daré victoria aún hasta probar un poco más mi red casera, para después darlo por solucionado.

Saludos y gracias.

---

### Post by biale on 2013-02-15
La interconexion UTP entre los equipos lleva un cruce. Pero ese cruce puede ser resuelto en forma automatica por uno de los equipos. En otros casos hay un puerto especial que debería usarse conectando "normal" a "especial" (ver manual!). Y si ninguno de los dos resuelve el cruce entonces hay que caer en un cable UTP cruzado.

Los dos modems operan sobre una única red implementada por el MR/1. El MR/2 resuelve sobre la capa de enlace y solo engancha paquetes a la red local.

Conectas la pc al MR/1 via UTP y si podes salir a internet anotate los resultados de los comandos "ifconfig" y "route"

Conectas ahora la pc al MR/2 via UTP y los resultados de los comandos anteriores deberían ser identicos.

Si no es el caso, el segundo router esta aportando cosas a la pc que no debería, pueden ser neutras o molestar. Cuando le configuras el def gateway al segundo router, es para el mismo, para poder configurarlo desde la internet. No se lo debería "entregar" a la PC

---

