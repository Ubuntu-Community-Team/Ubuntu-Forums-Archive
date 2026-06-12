---
title: "¿Como configurar  wifi telsur?..."
date: 2009-06-19
forum: Hardware
---

### Post by pat0v3n on 2009-06-19
Holas Lores del Ubuntu acabo de instalar Ubuntu en el notebook pero no puedo configurar el wifi para navegar por internet , pero la conexion por cable red funciona perfectamente . llame al MAGNIFICO servicio tecnico de Telefonica del Sur y su respuesta fue "No damos soporte para Ubuntu" espero ayuda desde ya gracias .-;)

version Ubuntu 9.04

---

### Post by CdK1 on 2009-06-19
Pues ve si tu tarjeta está reconocida y usa wicd para la configuración...

Prueba con:

sudo iwconfig

Te mostrara en que dispositivo está;

iwlist ethx scan  ==> Las redes posibles;

sudo ifconfig ethx up
sudo iwconfig ethx essid ELNOMBRE
sudo iwconfig ethx key s:PASSWORD
sudo dhclient ethx

---

### Post by Carlos C on 2009-06-19
También sería bueno saber qué tipo de conexión tienes. También si pudieras decir la salida del siguiente comando:
```
lspci |grep Ethernet && lspci |grep Wireless && lspci |grep Network
```Asi tenemos una idea de las especificaciones de tu hardware.

He movido el hilo al subforo adecuado. Por favor pon atención donde publicas ;)
Saludos.

---

### Post by moreback on 2009-06-19
Las conexiones de Wifi de Telefónica del Sur son PPPoE sobre una conexión Wi-fi, ni idea como hacer la conexión.

A lo mejor funciona haciendo una conexión de DSL con el Network-Manager y dejándola bloqueada a la interfaz wlan0 con la MAC de ésta (ver pestaña Cableada).

Saludos.

---

### Post by Carlos C on 2009-06-20
Un amigo mio tiene terra que usa wifi sobre pppoe y conseguimos hacer funcionar la conexión usando un router conectado al modem. De esa manera el router se loguea usando el usuario y el password asignado y entrega una red wifi normal con encriptación wpa. Sin un router ignoro como hacerlo.

---

### Post by fesbir on 2009-12-03
Luego de mucho tiempo buscando como conectarme a telsur con Ubuntu 9.04 he dado con la respuesta, espero les sirva.
Lo primero que tenemos que hacer es conectarnos a la red inalámbrica mediante el asistente de conexiones para linux, wicd (en esta pagina pueden encontrar los pasos para su instalación [http://www.dacostabalboa.com/gal/wicd-controla-a-tua-conexion-inalambrica-wifi-en-linux/517](http://www.dacostabalboa.com/gal/wicd-controla-a-tua-conexion-inalambrica-wifi-en-linux/517)), al seleccionar la red ponemos todos los datos (para trabajar con una ip estática), la ip, los dns, la clave, etc. en opciones avanzadas
con la siguiente configuración:
**ip: 192.168.1.12**
**dns1: 216.155.73.40**
**dns2:216.155.73.41**
**dns3:216.155.73.42**
puerta de enlace: **192.168.1.254** o su alternativo **192.168.1.1** (depende del modem)
Cuando elegimos el tipo de cifrado utilizaremos **WEP (Passphrase)** e ingresamos la clave de nuestra red inalámbrica, aceptamos y luego conectamos.
Hasta ahora estamos conectados a la red inalámbrica pero no tenemos aún acceso a internet. Para esto ingresaremos a la terminal de Ubuntu en modo root y hacemos correr el comando pppoeconf de la siguiente forma.
**~ sudo pppoeconf**
nos pedirá ingresar el username y el pass, ingresando estos datos ya podremos acceder a internet.


Pipo

---

### Post by chilenozo on 2009-12-16
Hola cabros, yo no uso Ubuntu pero igual quería ver si me pueden guiar con algunas de las preguntas que tengo sobre la wifi de telsur:

Yo tengo Fedora 9 ( no he querido cambiarme porque me funciona excelente con mi hardware, y ya me acostumbré).
 Mi pregunta es.
 

Yo instalé WICD y apagué NetworkManager. Aun asi, aunque veo la red de telsur, no se conecta nunca al modem adsl wifi ( o sea un paso previo a instalar un PPPOE). Entonces tampoco  tengo idea si el DHCP ta dando ips dinámicas o estáticas.


 También probé entrar al modem inalámbricamente con windows y los browser IE y Firefox (windows XP y vista tienen internet y funcionan bien) para obtener información de él, y no puedo. Traté de usar casi todos los códigos ip que se pueden obtener en internet para mi modem actual, un Thomson Speedtouch ST585 v6, y no pude wn (incluso en telsur me dicen que la ip del router es 168.192.1.254, y que solo me puedo conectar a él por cable ethernet, lo cual hago y tampoco puedo [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_sad.gif[/IMG] )


Éste es el modem:


[http://www.thomson.net/GlobalEnglish/Deliver/xDSL-Fiber/dsl-modems-gateways/residential_wireless/other_supported_products/thomson_st585v6/Pages/default.aspx](http://www.thomson.net/GlobalEnglish/Deliver/xDSL-Fiber/dsl-modems-gateways/residential_wireless/other_supported_products/thomson_st585v6/Pages/default.aspx)

Ayer anduve en diferentes lugares de Valdivia que tenían wifi gratis y tanto el NetworkManager como el WICD me funcionaron la raja y no tuve ningún problema pa conectarme a esas redes.
 

Alguna sugerencia?
Pa resumir

 

1) Cómo se si mi DHCP está dando ip dinámica o estática?
2) Cómo se los DNS de mi conexión?, algunas direcciones DNS se ven desde windows, son estáticas estas, o sea, si las uso en Linux, sirven igual?.
3) Como entro a mi modem ya sea desde linux o windows?
 4) Es fácil conectar al modem speedtouch un router adicional al cual yo si me pueda conectar con linux?, cómo lo hago?



Gracias

---

### Post by moreback on 2009-12-16
Tengo la impresión que la conexión se hace hacia el modem inalámbricamente, pero no debes usar DHCP para obtener una IP, sino que debes levantar una conexión PPPOE hacia el modem sobre esa conexión inalámbrica.

---

### Post by chilenozo on 2009-12-16
> **moreback said:**
> Tengo la impresión que la conexión se hace hacia el modem inalámbricamente, pero no debes usar DHCP para obtener una IP, sino que debes levantar una conexión PPPOE hacia el modem sobre esa conexión inalámbrica.

gracias pero ya lo solucioné.

Llamé a estos tipos de telsur y me cambiaron el modem a un zhone. Lo que pasa es que el speedouch no podía ser configurado como multiusuario ( según ellos), en cambio el nuevo si.

Una vez que me pude conectar al modem (con el programa wicd), levanté una PPPOE usando '/sbin/pppoe-setup' y una vez configurada, la activé con: /sbin/ifup 'nombre de mi conexion'

Lo único malo es que no encuentro forma de que se la PPPOE active automáticamente sola cada vez que reinicio o prendo mi pc, o cuando me desconecto de internet. Siempre tengo que hacer un webeo, fácil, pero latoso de escribir mi información de usuario.

Pero por lo menos tengo internet, no me puedo quejar.

Salu2.

---

### Post by nechus on 2009-12-16
Soy un feliz Ubuntero usuario de wifi de Telefónica del Sur, y del famoso modem Zhone.

Les cuento mi experiencia: Cuando recién me instalaron el servicio, usaron un notebook con Windows. Como mi notebook con Ubuntu no lograba conectarse a pesar de captar la señal, configuraron el módem de modo que no fuera necesario "el ícono". Ahora enciendo mi notebook y se conecta inmediatamente a internet.

Pero fue todo un atao lograr que Telefónica del Sur me pescara. Primero me dijeron que no tenían soporte para Linux, así que no había nada que hacer.  Insistí media hora más tarde y me dijeron que habría que "eliminar el ícono y configurar el acceso directo a la red", pero que tenían que mandar un técnico a mi casa y eso había que pagarlo aparte.  Acepté, y cuando me llamaron para coordinar la visita del técnico, me dijeron que no había que pagar nada.

Así que cuando los de Telefónica del Sur les digan que no tienen soporte para Linux, explíquenles que lo único que quieren es "eliminar el ícono" para conectarse directamente a Internet. Y que no les cobren porque a mí no me cobraron. Santo remedio.

¿Y qué es eso de "el ícono"?  Es que para conectarte a Internet en Windows tienes que hacer doble clic en un ícono que Telefónica del Sur pone en tu escritorio e ingresar tu clave.

Una última cosa por si les sirve: hace un tiempo mi conexión empezó a caerse sistemáticamente. Alcanzaba a meterme en una sola página de Internet, pero a los cinco segundos la conexión ya se había caído. Costó mucho encontrar la causa, pero finalmente un técnico que vino nos contó que les había llegado un mail a todos los técnicos avisando que los modems Zhone tenían problemas con el firmware. Me cambiaron el módem (por otro Zhone) y se arregló el problema.

---

### Post by renzo.martinez.friz on 2010-02-12
> **nechus said:**
> Soy un feliz Ubuntero usuario de wifi de Telefónica del Sur, y del famoso modem Zhone.
 
Les cuento mi experiencia: Cuando recién me instalaron el servicio, usaron un notebook con Windows. Como mi notebook con Ubuntu no lograba conectarse a pesar de captar la señal, configuraron el módem de modo que no fuera necesario "el ícono". Ahora enciendo mi notebook y se conecta inmediatamente a internet.
 
Pero fue todo un atao lograr que Telefónica del Sur me pescara. Primero me dijeron que no tenían soporte para Linux, así que no había nada que hacer. Insistí media hora más tarde y me dijeron que habría que "eliminar el ícono y configurar el acceso directo a la red", pero que tenían que mandar un técnico a mi casa y eso había que pagarlo aparte. Acepté, y cuando me llamaron para coordinar la visita del técnico, me dijeron que no había que pagar nada.
 
Así que cuando los de Telefónica del Sur les digan que no tienen soporte para Linux, explíquenles que lo único que quieren es "eliminar el ícono" para conectarse directamente a Internet. Y que no les cobren porque a mí no me cobraron. Santo remedio.
 
¿Y qué es eso de "el ícono"? Es que para conectarte a Internet en Windows tienes que hacer doble clic en un ícono que Telefónica del Sur pone en tu escritorio e ingresar tu clave.
 
Una última cosa por si les sirve: hace un tiempo mi conexión empezó a caerse sistemáticamente. Alcanzaba a meterme en una sola página de Internet, pero a los cinco segundos la conexión ya se había caído. Costó mucho encontrar la causa, pero finalmente un técnico que vino nos contó que les había llegado un mail a todos los técnicos avisando que los modems Zhone tenían problemas con el firmware. Me cambiaron el módem (por otro Zhone) y se arregló el problema.
 
 
Estimado:  En mi caso tenía un PC con Windows y un NB con Ubuntu 9.04 (actual 9.10) y las claves de conexión tienen que dejarla en el móden, es decir, que en cualquiera de los 2 casos por el solo hecho de encender el PC quedan en red sin presionar iconos ni entregar claves ni leseras.  Tal como un PC de empresa donde lo primero que hace uno al llegar es encenderlo y quedar con acceso a internet (...para leer el diario online).
 
Actualmente, pasé (aunque con algunos problemas) el PC a Ubuntu y nunca me ha pedido clave de nada, ni cuando lo instalé la primera vez.

---

### Post by Lutho on 2010-03-27
Estimados, he leido todo los post sobre la configuracion de wifi telsur. 
Para mi parecer, despues de mucho leer y probar muchas de las confguraciones via internet, encontre un metodo bastante facil.

como todos saben wifi telsur, nos entrega una calve de acceso, que es la mac del router que ellos instalan, con la espesificacion de que tiene que estar escribto en mayuscula.

Para poder conectarnos, tan solo leccionamos nuestra red, la que dice "wifitelsur_ooo" cuando nos pida la clave, la ingresamos. A todo esto nos volvera a preguntar nuevamente la clave pero es ahi donde le damos cancelar.

Se preguntaran por que, bueno es simple mente por que tenemos que hacer un enlace local. con nuestro router.

Cuando hayas cancelado la segunda vez que te pidio la clave, hacemos click derecho sobre el icono de la red inalambrica, luego pinchams "editar las conexciones..." 
cuando nos aparesca la ventana, nos vamos a la pestaña que dice "inalambricas" 
seleccionamos nuestra red telsur, la cual es "wifitelsur_ooo" y luego pichamos en "editar"
cuando pichamos en "editar" nos aparece una ventana, la cual nos dirijimos a la pestaña "Ajustes de IPv4"
cuando pinchamos ahi, donde dice "metodo" seleccionamos el que dice "Solo enlace local" 
y para finalizar "aplicar" y "cerrar"

ya con todo esto.. 
ALT+F2  "gnome-terminal"
$sudo pppeoconfig
seguir los pasos y listo 

xD

nota: cuando reinician el pc se desaparecera la wifi y no veran ninguna red, pero no asustar .. por que deben editar el siguiente archivo..

interfaces

que esta en 
/etc/network

deben de comentar la linea que dice algo de 
"iface wlan0 ......

eso espero que les sirva.. sorry por la mala ortografia y mi redaccioon .. 
saludos .. 
xD:p

---

### Post by riv_7 on 2010-08-12
Lutho...mira hice todo y me funciono tuve wifi..pero reinicie...se me perdio el icono de redes y me fui a editar el archivo "interfaces"...pero lo abro y no me deja modificarlo..como puedo hacerlo...desde ya muchas gracias

---

### Post by Carlos C on 2010-08-15
> **riv_7 said:**
> Lutho...mira hice todo y me funciono tuve wifi..pero reinicie...se me perdio el icono de redes y me fui a editar el archivo "interfaces"...pero lo abro y no me deja modificarlo..como puedo hacerlo...desde ya muchas gracias

Editar ese archivo requiere de permisos de administrador, para ello utilizas el comando [sudo]("http://www.guia-ubuntu.org/index.php?title=Sudo"):

```
sudo gedit /etc/network/interfaces
```Cualquier carpeta que no pertenezca a tu usuario (en general cualquiera que no esté en tu carpeta /home) requiere de los permisos adecuados para ser modificada. El [sistema de permisos]("http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros#Permisos") en linux es fundamental para la seguridad de todo el sistema, por lo que te aconsejo que averigües bien al respecto.

Saludos.

---

### Post by Lutho on 2010-09-18
Oops, sorry descuide el tema ubuntu. 

Lo Siento..

---

