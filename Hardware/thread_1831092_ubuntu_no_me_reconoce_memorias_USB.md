---
title: "ubuntu no me reconoce memorias USB"
date: 2011-08-22
forum: Hardware
---

### Post by drazhe on 2011-08-22
acabo de instalar ubuntu 11.04 en una notebook, desde un pendrive USB ya que no funcionaba la unidad de DVD, no hubo ningu problema durante la instalacion, pero al terminar, los pendrives, y discos rigidos externos no eran reconocidos...
Alguno sabe la causa y como solucionarlo? los puertos parecen funcionar bien, ya que mi mouse funciona sin problema, pero los pendrives ni siquiera aparecen... 

les agradeceria la respuestas...

---

### Post by gmunioz on 2011-08-23
En principio, enchufa el/los pendrive/s y ejecuta en una terminal:
sudo su
lsusb
Y postea la salida.

---

### Post by drazhe on 2011-08-23
Esto es lo que dice la terminal con las ordenes que me pediste... 

vero@Vero-PC:~$ sudo su
[sudo] password for vero: 
root@Vero-PC:/home/vero# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b055 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by drazhe on 2011-08-23
sigo con mis problemas de novato en natty narwhal, ahora me tira un error en las actualizaciones y no me deja instalar ningún programa hasta que se resuelvan las dependencias, el problema es que nunca termina de solucionar el problema... alguna idea?
adjunto imagen y mensajes de error para ver si me pueden ayudar... 

[IMG]http://s3.subirimagenes.com:81/fondosycapturas/previo/thump_6837525pantallazo.png[/IMG]


Mensaje de error:

Los siguientes paquetes tienen dependencias incumplidas:

language-pack-es: Depends: language-pack-es-base (>= 1:11.04+20110607) pero 1:11.04+20110421 está instalado
language-pack-gnome-es: Depends: language-pack-gnome-es-base (>= 1:11.04+20110607) pero 1:11.04+20110607 está instalado
                        Depends: language-pack-es-base (>= 1:11.04+20110607) pero 1:11.04+20110421 está instalado

---

### Post by gmunioz on 2011-08-24
Pues por lo que se ve en la salida, no esta reconocido como conectado ninguno de los pendrives, solo se ven conectados:

Bus 003 Device 003: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
que parece ser el mouse usb.

Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
que parece ser un disco rígido externo, usb.

Prueba ejecutar con los pendrives conectados, en una terminal:
sudo su
fdisk -l
Pega las salidfas en el post.

Además, actualiza el sistema.
Desde synaptic, habilita todos los repositorios y luego en una terminal,
conectada la laptop a internet ejecuta:
sudo su
apt-get update
apt-get upgrade

---

### Post by guillermolisi on 2011-08-24
> **gmunioz said:**
> Además, actualiza el sistema.
Desde synaptic, habilita todos los repositorios y luego en una terminal,
conectada la laptop a internet ejecuta:
sudo su
apt-get update
apt-get upgrade
O tambien podes utilizar el Gestor de Actualizaciones, si no queres utilizar consola/terminal y no tenes Synaptic instalado.

En caso que decidas usar apt-get, sugiero cambiar la segunda linea por ```
apt-get dist-upgrade
```para que se apliquen cambios mayores tales como nuevas versiones de kernel, por ejemplo.

---

### Post by guillermolisi on 2011-08-24
> **drazhe said:**
> sigo con mis problemas de novato en natty narwhal, ahora me tira un error en las actualizaciones y no me deja instalar ningún programa hasta que se resuelvan las dependencias, el problema es que nunca termina de solucionar el problema... alguna idea?
adjunto imagen y mensajes de error para ver si me pueden ayudar... 

[IMG]http://s3.subirimagenes.com:81/fondosycapturas/previo/thump_6837525pantallazo.png[/IMG]


Mensaje de error:

Los siguientes paquetes tienen dependencias incumplidas:

language-pack-es: Depends: language-pack-es-base (>= 1:11.04+20110607) pero 1:11.04+20110421 está instalado
language-pack-gnome-es: Depends: language-pack-gnome-es-base (>= 1:11.04+20110607) pero 1:11.04+20110607 está instalado
                        Depends: language-pack-es-base (>= 1:11.04+20110607) pero 1:11.04+20110421 está instalado
Cerra el gestor de actualizaciones y abri una consola/terminal. Una vez ahi, ingresa ```
sudo dpkg --configure -a
```y contanos como te fue. Si hay algo roto, tal como dice la imagen, deberia resolverse aplicando las actualizaciones parciales pendientes.

Todo esto basado en la suposicion que los repositorios que tenes activos corresponden todos a la version que Ubuntu que estas corriendo.

---

### Post by drazhe on 2011-08-26
Bueno después de intentar todo lo que me dijeron, ya sea para las dependencias y actualizaciones fallidas y por el asunto ese de que no reconocida las unidades usb decidí hacer borrón y cuenta nueva y reinstale el sistema desde 0 y todo parece haberse solucionado, ya no tira los errores de actualización y los pendrives son reconocidos y pueden ser utilizados sin problemas... la verdad es que no se me ocurre que pudo haber pasado... 

el nuevo problema es el siguiente, la portátil en la que instale el **Ubuntu 11.04** trae una webcam integrada y no consigo hacerla funcionar, leyendo por varios foros recomiendan distintos tipos de programas y la verdad es que ya no se cual escoger, asi que les agradecería alguna sugerencia...

---

### Post by guillermolisi on 2011-08-26
> **drazhe said:**
> Bueno después de intentar todo lo que me dijeron, ya sea para las dependencias y actualizaciones fallidas y por el asunto ese de que no reconocida las unidades usb decidí hacer borrón y cuenta nueva y reinstale el sistema desde 0 y todo parece haberse solucionado, ya no tira los errores de actualización y los pendrives son reconocidos y pueden ser utilizados sin problemas... la verdad es que no se me ocurre que pudo haber pasado... 

el nuevo problema es el siguiente, la portátil en la que instale el **Ubuntu 11.04** trae una webcam integrada y no consigo hacerla funcionar, leyendo por varios foros recomiendan distintos tipos de programas y la verdad es que ya no se cual escoger, asi que les agradecería alguna sugerencia...

Ingresa en una consola/terminal ```
lsusb
```y mostra que te devuelve

---

### Post by guillermolisi on 2011-08-26
> **drazhe said:**
> bueno, queriendo instalar el cubo de compiz y sus efectos, instale estos paguetes:

compizconfig-settings-manager 

compiz-fusion-plugins-extra

y todo parece haber funcionado bien, pero cuando activo el cubo y resuelvo sus problemas, me desaparecio la barra de titulo superior, donde estarian los botones de cerrar, maximizar y minimizar

[IMG]http://s2.subirimagenes.com/imagen/previo/thump_6846363pantallazo.png[/IMG]

tambien dejaron de funcionar las combinaciones de teclas, alt+f1, crtl+alt+t etc.... 


por cierto como no me gusta unity, siempre inicio con el escritorio clasico de GNOME, puede ser eso el problema?

Abri un nuevo hilo con este asunto ya que no tiene nada que ver con el topico original. Gracias

Edit: Listo, ya lo hice por vos. Esta [aqui]("http://ubuntuforums.org/showpost.php?p=11188440&postcount=1").

Por favor, leer y observar las pautas tematicas indicadas para cada seccion de este foro antes de publicar un mensaje.

---

### Post by drazhe on 2011-08-26
XXXX@XXXX-PC:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 04f2:b055 Chicony Electronics Co., Ltd **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



la que marco en negrita creo que es la camara, por lo que estuve leyendo en internet...

---

### Post by guillermolisi on 2011-08-26
Si, hasta ahi esta bien reconocida.
Ahora, con que la estas probando para determinar que no funciona ?

---

### Post by drazhe on 2011-08-26
empathy es lo unico que trae Ubuntu 11.04 o me equivoco?

---

### Post by drazhe on 2011-08-26
Acabo de instalar un programa llamado **Cheese webcam booth** y la camara funciona perfecto, toma foto, filma y todo eso... 
así que parece que fue reconocida, el problema es que el empathy aparentemente no funciona para hacer vídeo conferencias... o yo no lo se configurar para que haga eso... 
Me podrías ayudar con el tema o recomendarme algún programa para poder hacer vídeo conferencias a través de la red del **MSN Live** o **Skype**?

---

### Post by rojojuan on 2011-08-26
Hasta hace poco Skype me reconocía la webcam (logitech), pero desde que Microsoft compró esa compañía, dejó de funcionar.
Estuve viendo que Gmail, además de las funciones de correo electrónico tiene la misma función de chat que Skype. 
Para ver si aquí te funciona la webcam en el chat, entrás a Gmail, en el extremo superior derecho tenés un asterisco que clickeando te permite acceder a la configuración del correo; una vez allí entras a Chat y una una de las opciones es “comprueba tu configuración”.
Dentro de esta esta opción está “Cámara” y podés comprobar si te la reconoce o no. En mi caso instalé el plugin que me sugirió y anda perfecto.

---

### Post by drazhe on 2011-08-26
> **rojojuan said:**
> Hasta hace poco Skype me reconocía la webcam (logitech), pero desde que Microsoft compró esa compañía, dejó de funcionar.
Estuve viendo que Gmail, además de las funciones de correo electrónico tiene la misma función de chat que Skype. 
Para ver si aquí te funciona la webcam en el chat, entrás a Gmail, en el extremo superior derecho tenés un asterisco que clickeando te permite acceder a la configuración del correo; una vez allí entras a Chat y una una de las opciones es “comprueba tu configuración”.
Dentro de esta esta opción está “Cámara” y podés comprobar si te la reconoce o no. En mi caso instalé el plugin que me sugirió y anda perfecto.

si, es lo que estuve leyendo y es el error que me tira el amsn cuando quiero configurar una videollamada... así que habrá que esperar que la ingeniería inversa haga sus frutos para poder tener de nuevo el servicio... como siempre, el ptoblema es por los  $%$&%#%/ de micro$oft &@|(#$%&#!!!!!

---

