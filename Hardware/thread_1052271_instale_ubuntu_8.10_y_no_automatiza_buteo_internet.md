---
title: "instale ubuntu 8.10 y no automatiza buteo internet"
date: 2009-01-27
forum: Hardware
---

### Post by pachecojuancarlos on 2009-01-27
Hola ya consegui que mediante la orden  sudo ifconfig eth0 192.168.0.132 netmask 255.255.255.0 up y  sudo route add default gw 192.168.0.1, puedo navegar y enviar este mensaje, no logro que se automatice al arranque del equipo, revise el archivo /etc/network/interfaces este lo cambie si bien no entiendo las sentencias le coloque una que me recomendaron que es la siguiente:
auto lo
iface eth0 inet loopbak
auto eth0
iface eth0 inet static
address 192.168.0.132
netmask 255.255.255.0
gateway 192.168.0.1

aun asi no consegui nada el equipo busca siempre la red inalambrica, pero este servicio no esta disponible aunque lee que tengo una linea , fuera de eso no se que mas hacer porque en realidad he actualizado el soft y navego bien pero al apagar el equipo y arrancar tengo que volver a escribir la orden sudo ifconfig...........
espero alguna sugerenca, gracias

---

### Post by guillermolisi on 2009-01-27
> **pachecojuancarlos said:**
> Hola ya consegui que mediante la orden  sudo ifconfig eth0 192.168.0.132 netmask 255.255.255.0 up y  sudo route add default gw 192.168.0.1, puedo navegar y enviar este mensaje, no logro que se automatice al arranque del equipo, revise el archivo /etc/network/interfaces este lo cambie si bien no entiendo las sentencias le coloque una que me recomendaron que es la siguiente:
auto lo
iface eth0 inet loopbak
auto eth0
iface eth0 inet static
address 192.168.0.132
netmask 255.255.255.0
gateway 192.168.0.1

aun asi no consegui nada el equipo busca siempre la red inalambrica, pero este servicio no esta disponible aunque lee que tengo una linea , fuera de eso no se que mas hacer porque en realidad he actualizado el soft y navego bien pero al apagar el equipo y arrancar tengo que volver a escribir la orden sudo ifconfig...........
espero alguna sugerenca, gracias

Varias sugerencias.

La primera y no menor es que esto es parte de otro hilo/thread y abrir uno nuevo desvirtua el objetivo del foro que es facilitarle las cosas a todo aquel que este buscando una solucion a problemas que otro ya resolvio.

La segunda es que si la placa de red que esta conectada a Internet es la eth0 entonces la que conecta a la LAN debe llamarse eth1 y por ello tenes que corregir el script porque estas configurando dos veces la misma placa de formas distintas, por eso sucede lo que comentas con la inalambrica.

Loopback esta mal escrito, le falta la "c" antes de la "k".

Podes copiar y pegar contenidos que te sugieran por esta via, asi no cometes tantos "typos".

---

### Post by pachecojuancarlos on 2009-01-27
> **guillermolisi said:**
> Varias sugerencias.

La primera y no menor es que esto es parte de otro hilo/thread y abrir uno nuevo desvirtua el objetivo del foro que es facilitarle las cosas a todo aquel que este buscando una solucion a problemas que otro ya resolvio.

La segunda es que si la placa de red que esta conectada a Internet es la eth0 entonces la que conecta a la LAN debe llamarse eth1 y por ello tenes que corregir el script porque estas configurando dos veces la misma placa de formas distintas, por eso sucede lo que comentas con la inalambrica.

Loopback esta mal escrito, le falta la "c" antes de la "k".

Podes copiar y pegar contenidos que te sugieran por esta via, asi no cometes tantos "typos".

OK  pido disculpas, mira no me quedo claro lo de eth0 y eth1, te explico el charco se me hizo porque me decis que una esta conectada a internet y otra a la LAN (eth0 y eth1 respectivamente)pero si no se como se le dice que una sea eth0 o eth1 yo solo copio las ayudas, y esta la malcopie (reconozco) de una ayuda de cuando instale ubuntu 8.4, pero ahora ya se termino y pera colmo no pude encontrar el hilo anterior y tuve que joder por correo, te la hago corta yo voy a probar alternativamente en el script los valores de eth0 y eth1 y luego te cuento,gracias

---

### Post by guillermolisi on 2009-01-28
> **pachecojuancarlos said:**
> OK  pido disculpas, mira no me quedo claro lo de eth0 y eth1, te explico el charco se me hizo porque me decis que una esta conectada a internet y otra a la LAN (eth0 y eth1 respectivamente)pero si no se como se le dice que una sea eth0 o eth1 yo solo copio las ayudas, y esta la malcopie (reconozco) de una ayuda de cuando instale ubuntu 8.4, pero ahora ya se termino y pera colmo no pude encontrar el hilo anterior y tuve que joder por correo, te la hago corta yo voy a probar alternativamente en el script los valores de eth0 y eth1 y luego te cuento,gracias
Mas facil que andar toqueteando la configuracion del /etc/network/interfaces es cambiar los cables de red de placa y ver si tenes salida a Internet desde todas las maquinas.

---

### Post by pachecojuancarlos on 2009-01-29
> **guillermolisi said:**
> Mas facil que andar toqueteando la configuracion del /etc/network/interfaces es cambiar los cables de red de placa y ver si tenes salida a Internet desde todas las maquinas.

En casa hay tres maquinas cada una tiene un cable que sale desde el servidor del proveedor (vecino), en las tres tengo salida a internet con windows sin ningun problema, en mi maquina, ademas tengo ubuntu 8.10, y ahora tengo salida a internet, pero siempre que escriba en terminal la orden que me explicaron en el Thread se borra al apagar la maquina,tal vez esto aclare porque yo insista en toquetear la configuracion, es verdad que yo no se de linux,pero lo del cable te juro fue lo primero, es mas cambie de lugar las maquinas. y estas reconocieron la red pero no salieron a internet porque me explica el vecino, que auque cambie el IP no es la misma maquina y por eso no sale a internet, luego el dice que cambio eso y todas las maquinas salieron con los distintos cables, despues me dejo todo como estaba.
las maquinas y los cables estan bien todas salen a internet a estas alturas quisiera saber si es mi hard o la configuracion general de mi maquina la que me impide automatizar el buteo de internet, gracias

---

### Post by guillermolisi on 2009-01-29
> **pachecojuancarlos said:**
> En casa hay tres maquinas cada una tiene un cable que sale desde el servidor del proveedor (vecino), en las tres tengo salida a internet con windows sin ningun problema, en mi maquina, ademas tengo ubuntu 8.10, y ahora tengo salida a internet, pero siempre que escriba en terminal la orden que me explicaron en el Thread se borra al apagar la maquina,tal vez esto aclare porque yo insista en toquetear la configuracion, es verdad que yo no se de linux,pero lo del cable te juro fue lo primero, es mas cambie de lugar las maquinas. y estas reconocieron la red pero no salieron a internet porque me explica el vecino, que auque cambie el IP no es la misma maquina y por eso no sale a internet, luego el dice que cambio eso y todas las maquinas salieron con los distintos cables, despues me dejo todo como estaba.
las maquinas y los cables estan bien todas salen a internet a estas alturas quisiera saber si es mi hard o la configuracion general de mi maquina la que me impide automatizar el buteo de internet, gracias

Bueno, por lo que acabas de comentar me parece que quien te provee la conexion a Internet hace control por MAC address de cada PC conectada, por eso te dijo que si cambiabas la PC no funcionaba "porque no era la misma PC".

La MAC address es como el DNI (o mejor aun) ya que identifica en forma unica cada placa de red fabricada (o se supone que deberia ser asi).
Entonces, como cada placa tiene una identificacion unica, cuando cambias la PC cambia esta identificacion y ahi es cuando rechaza la conexion.

Una razon para hacer esto es poder controlar que no le conectes cualquier maquina que no sea tuya (y conocida por el, de alguna forma).

Respecto de que cada vez que reinicias la maquina Ubuntu pierde la configuracion de la placa de red (mas precisamente la que figura en el archivo /etc/network/interfaces) no deberia ser asi a menso que el NetworkManager este haciendo de las suyas.

Cuando dije cambiar el cable me referia a cambiarlo de boca (de placa de red) en la misma PC para determinar cual es identificada como eth0 y cual como eth1, no cambiar el cable por pensar que este defectuoso.

Cuando reincias la PC, que contenido posee el mencionado archivo ?
La configuracion de la placa la haces editando el archivo o a traves del Network Manager ?

Releyendote, que queres decir, significar, con eso de "automatizar el buteo de Internet" ?

---

### Post by pachecojuancarlos on 2009-06-27
gente este mensaje es mi pequeño aporte, despues de 5 meses y dandole como se podia, verifique que era un error de parte mia al configurar la placa de red, pues (realmente el aleman me tuvo loco)no cargaba el valor de dns al final siendo que me dieron como 5 dns gratuitos, finalmente cuando lo logre cambie a ubuntu 9.04 y ahora todo bien asi que cuando pueda acordarme le doy final a este hilo y quiero empezar otr porque ahora es problema de capturadora.
saludos

---

