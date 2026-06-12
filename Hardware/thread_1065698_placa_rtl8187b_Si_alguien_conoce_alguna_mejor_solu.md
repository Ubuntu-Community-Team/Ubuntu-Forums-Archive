---
title: "placa rtl8187b Si alguien conoce alguna mejor solución..."
date: 2009-02-10
forum: Hardware
---

### Post by david_mza on 2009-02-10
Hola a todos, es mi primera particioación en el foro así que espero que sea productivo 

Hace poco compre una notebook olivetti up200 bastante recomendable en todos los aspectos pero... la placa wifi (realtek rtl8187b) si bien es detectada inmeditamente en ubuntu intrepid por network-manager la recepción de la señal es muy débil a tal punto de perder completamente la señal a sólo 10 mts del router, lo q me impedia usarla desde mi cama ](*,). 

Despues de intentar con wifi-radar y ndiswrapper la solución la encontré :P con wicd y agregando un opcion en el script de wicd antes de conectarse, aca vá:

**1. Instalar wicd agregando previamente los repositorios y la clave correspodiente:**
En una consola ejecutamos 
# sudo gedit /etc/apt/sources.list 

y agregamos esta línea 
“deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras”  (sin comillas)

agregamos la clave gpg
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

luego actualizamos e instalamos
# sudo apt-get update
# sudo apt-get install wicd

Esto instalará wicd y desinstalará network-manager y al reiniciar ya será nuestro nuevo gestor de redes.

**2. Una vez detectada la red wifi vamos a preferencia y tildamos “Usar dBm** para medir la intensidad de la señal” esto hará que la visualización de la intensidad de la señal se ajuste mas a la realidad a nuestros ojos.

**3. Luego dentro de la conexión pinchamos en el botón “scripts” y en** “pre-connection script” agregamos la siguiente línea  “iwconfig wlan0 rate 12M fixed” (sin comillas). Esto fija la tasa de trasnferencia a 12mb.

Despues de realizar esto la recepción de la placa mejoró considerablemente pero tengo la sensación de que la placa puede dar mucho mas y que esto es sólo un parche. **Si alguien tiene alguna sugerencia par mejorarlo o conoce una solución de fondo será mas que bienvenida.**

Desde ya... Gracias!! ;)

---

### Post by julioipn on 2009-02-16
hola que tal, yo tengo una netbook con la misma tarjeta wifi, mi problema era que despues de unos minutos se perdia la conexion con el router, es decir, el network manager marcaba que seguia conectado y con buena intensidad, pero no podia ni siquiera hacer ping al router, por lo tanto no podia usar internet, intente muchas cosas, lo que mejor me funciono fue escribir a realtek y pedir el driver para linux, al dia siguiente me llego, solo lo compile y lo instale y desde entonces no he tenido ningun problema

---

### Post by david_mza on 2009-02-19
Gracias por contestar... Ahora, es posible que me mandes el driver asi no hago el mismo tramite? inclusive, podriamos dejarlo en algun servidor y postear el link, y si no es mucho pedir sería bueno que me digas los pasos para compilarlo e instalarlo. GRaacias de nuevo! 

> **julioipn said:**
> hola que tal, yo tengo una netbook con la misma tarjeta wifi, mi problema era que despues de unos minutos se perdia la conexion con el router, es decir, el network manager marcaba que seguia conectado y con buena intensidad, pero no podia ni siquiera hacer ping al router, por lo tanto no podia usar internet, intente muchas cosas, lo que mejor me funciono fue escribir a realtek y pedir el driver para linux, al dia siguiente me llego, solo lo compile y lo instale y desde entonces no he tenido ningun problema

---

### Post by julioipn on 2009-02-20
Por supuesto, con mucho gusto te lo paso, aunque seria mejor si lo pidieras a Realtek, asi se darian cuenta que hay muchos usuarios de linux que necesitan el driver, ya que aunque lo tienen este no esta disponible para su descarga en la pagina de realtek, pero como gustes, si quieres que te lo mande dejame tu correo o si quieres pedirlo esta es la direccion: [email]wlanfae@realtek.com[/email], a mi me llego unas cuantas horas despues de haberlo pedido, ya sea que lo pidas a realtek o quieras que te lo  pase, una vez que lo tengas solo tienes que descomprimir el archivo (viene como tar.gz) y luego en la terminal te vas  a la carpeta descomprimida yejecutas el siguiente comando para compilar:

make

y luego para instalar

sudo make install

despues reinicias y al regresar a ubuntu checas en "System->Administration->Hardware Drivers" que aparezca activado y en uso el siguiente driver:
 Linux Driver for Realtek RTL8187 WiFi Cards

y eso es todo lo que hice, espero te sirva

---

### Post by Nahamen on 2009-03-02
Serias tan amable de mandarmelo a mi tambien!!! 
Por favor!!!!

mi mail: [email]nahamen@gmail.com[/email]

---

### Post by jaehoo on 2009-03-09
> **Nahamen said:**
> Serias tan amable de mandarmelo a mi tambien!!! 
Por favor!!!!

mi mail: [email]nahamen@gmail.com[/email]

pueden  enviarmelo a mi tambien???

[email]jaehoo@gmail.com[/email]

---

### Post by jaehoo on 2009-03-16
> **julioipn said:**
> Por supuesto, con mucho gusto te lo paso, aunque seria mejor si lo pidieras a Realtek, asi se darian cuenta que hay muchos usuarios de linux que necesitan el driver, ya que aunque lo tienen este no esta disponible para su descarga en la pagina de realtek, pero como gustes, si quieres que te lo mande dejame tu correo o si quieres pedirlo esta es la direccion: [email]wlanfae@realtek.com[/email], a mi me llego unas cuantas horas despues de haberlo pedido, ya sea que lo pidas a realtek o quieras que te lo  pase, una vez que lo tengas solo tienes que descomprimir el archivo (viene como tar.gz) y luego en la terminal te vas  a la carpeta descomprimida yejecutas el siguiente comando para compilar:

make

y luego para instalar

sudo make install

despues reinicias y al regresar a ubuntu checas en "System->Administration->Hardware Drivers" que aparezca activado y en uso el siguiente driver:
 Linux Driver for Realtek RTL8187 WiFi Cards

y eso es todo lo que hice, espero te sirva


Hola, muchas gracias por el driver.

Tambien lo pedí por correo a la direccion que dices: [email]wlanfae@realtek.com[/email] y me llego al día siguiente, si alguien lo necesita les sugiero que lo pidan directamente a Realtek, porque es bien cierto necesitamos que comiecen a ver a la comunidad de usuarios linux y tal vez en un futuro ya tengamos este driver en su pagina de soporte.


Tengo instalado ubuntu 8.10 (2.6.27-11-generic) y mi tarjeta tiene el iguiente ID:
**0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter**

Seguí las instrucciones del readme.

1. Compilar el driver
**[INDENT]$ make[/INDENT]**
2. Instalas el driver
**[INDENT]$ sudo make install [/INDENT]**
3. Reinicias la computadora

4. Activas el driver:

"System->Administration->Hardware Drivers"  tiene que aparecer activado el driver "Linux Driver for Realtek RTL8187 WiFi Cards"

Nota: en mi caso ya estaba habilitado pero no funcionaba así que tuve desactivarlo y volverlo a activar para que reconociera la interfaz.

Y listo todo funciona perfecto :D!!

Gracias y saludos.

---

### Post by Nano.uy on 2009-11-02
Hola amigos. Dí con este tópico porque yo también "sufro" la misma placa (sufro también de SIS, pero eso es otra historia :D). Como muchos acá pedí por mail los drivers a Realtek, sigo recomendando a todos los que me preguntan que pidan los drivers a la empresa a ver si algún día les da vergüenza y los suben a la página. Pero ahora instalé el Karmic Koala, y cuando fui tranquilamente a instalar los drivers me encontré con esto: 

```
nano@nano-laptop:~/Respaldos/Drivers/rtl8187b$ makemake[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.o
/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/nano/Respaldos/Drivers/rtl8187b/ieee80211] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
nano@nano-laptop:~/Respaldos/Drivers/rtl8187b$ 

```

Buscando por internet me topé con esto otro: 

"[...] linux kernel 2.6.31. This kernel removes backwards compatibility for the old network driver api. Only the new net_driver_ops structure api is supported. "

O sea que parece que el los kernel 2.6.31.x no soportan la estructura de estos drivers. 
En el foro en ingles encontré ya un tópico con este problema. Lo dejo por acá para que sigamos la discusión.

Lo que pienso hacer ahora es mandarle el error al servicio de Realtek para ver que me dicen, sería interesante que a los que tengan este driver y tengan el mismo problema manden su propio mail a ver si podemos por lo menos generarles un poquito aunque nomas sea de presión. 

Saludos y hasta luego.

---

### Post by mhoyos on 2009-12-23
buenas a tod@s:

en el dia de ayer, tuve un gran problema: una placa wifi rebelde !!!!

detectaba las redes (abiertas y cerradas) sin problema, pero no conectaba !!!

al querer "enlazarse" al AP, daba un error de timeout.. y luego, no
tomaba los parametros via dhcp.

intente tambien, hacerlo en forma "manual" y nada.. :(

y justo, la instalacion la tenia que hacer, a una persona que esta
empezando con el SL en el ambiente politico... se podran imaginar,
cual era mi "desesperacion" para que funcione.:!!!

la notebook, es una olivetti, y el detalle de la placa es este (lsusb):

Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B
Wireless 802.11g 54Mbps Network Adapter

y los modulos que cargan:


mac80211              181076  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211


hasta le instale el wicd, y nada..

alguno le paso lo mismo ? alguna idea de como solucionarlo ?

desde ya, gracias..

P.D: y si alguno logro pasar de los 800x600 en una placa SIS en una
notebook, que tambien avise !!! :)

---

### Post by guillermolisi on 2009-12-23
Marco

Dale una leida a [este doc]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b") y despues comenta que tal te fue.

---

### Post by guillermolisi on 2009-12-23
Por si aun no lo leyeron, [aqui hay un doc]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b") que puede servir

---

### Post by mhoyos on 2009-12-27
> **guillermolisi said:**
> Marco

Dale una leida a [este doc]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b") y despues comenta que tal te fue.

lamento decirte que eso es para la serie B..

la que tengo problemas es la RTL8187 "a secas" sin la B...

:(

sigo intentando.. ya que el "dueño" de una notebook, se resiste a usar win solo x el wifi..

saludos..

---

