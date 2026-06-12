---
title: "[SOLVED] Problema con conexion a internet en 8.10 Intrepid Ibex"
date: 2008-11-03
forum: Hardware
---

### Post by emiliano_raso on 2008-11-03
Bueno, es mi primer thread en el foro Ubuntu.
Soy usuario de este sistema operativo y gracias a foros, blogs, etc. he ido solucionando cada problema que he tenido (que a proposito no fueron tantos como los que tuve en window$), pero esta vez no encontre solucion xD
Seguramente porque hace poco que II salio.

El problema es el siguiente:
Logro que la notebook conecte a la red local, pero no tengo conexion a internet. En Hardy Heron esto no pasaba.
Puedo acceder a la otra computadora, por lo tanto se conecta a la red, pero no a internet.

- Instale Intrepid Ibex un dia despues de haber salido. Antes tenia Hardy Heron. Lo instale desde CD formateando la particion. No actualize Hardy a la nueva version.
- Tengo una notebook Acer Aspire 5710-4900 conectada a una red inalambrica.
- Pasa tanto con Ubuntu (Gnome) como con Kubuntu (KDE4.1)
- He conseguido conectarme en Ubuntu (Gnome) luego de clickear reiteradas veces en la red wifi, es decir, desconectando y conectando muchas veces.

No es una buena solucion, y no siempre funciona. Que es lo que pasa? Si faltan datos diganme que los pongo.

Desde ya muchas gracias.

---

### Post by ramiro_md on 2008-11-05
Raso aca te dejo un thread donde hay un tema parecido: [http://ubuntuforums.org/showthread.php?t=970447](http://ubuntuforums.org/showthread.php?t=970447)

---

### Post by Hernán-Amaya on 2008-11-05
como tenes configurada la red? por lo que entendí tenes una pc que comparte internet a la wifi 

te fijaste si tenes bien puesta la dire de la puerta de enlace?
si tenes bien la dir de dns?

---

### Post by emiliano_raso on 2008-11-05
Dios mio! Que calor que hace!

Desde ya les agradezco las respuestas...

Bueno, volviendo al tema, la conexion es asi:
Tengo Speedy. Cuando compre la notebook en marzo vino un flaco, configuro el router y el modem (hizo magia) y en dos minutos ya tenia internet en la de escritorio y en la notebook.
De la pared va al modem Ethernet, de ahi se conecta al router WIFI. Y del router por cable de red esta conectada la PC de escritorio, y ese mismo router me da WIFI para la notebook.

La realidad es que no se realmente NADA de redes, es decir, toy como turco en la neblina cuando tengo este tipo de problemas.

Lo de la puerta de enlace no tengo idea :-P
Lo que si: En Window$ Vi$ta anda sin problema internet (en la notebook tengo Ubuntu 8.10, y Window$ Vi$ta).
Cuando tenia instalado Ubuntu 8.04, andaba perfectamente.

Ayer instale Edubuntu 7.10 y tampoco tuve problemas. Asi que definitivamente creo que no es problema de la maquina o de la red, sino problema de Ubuntu.

Ramiro: El thread ese que pasaste es un problema diferente, pero grax igual...

---

### Post by Hernán-Amaya on 2008-11-05
posteá la salida de este comando:

ifconfig -a 

sabes como tenes configurado el router wireless? que tipo de seguridad tenes wep wpa ?

---

### Post by emiliano_raso on 2008-11-05
Un amigo me los habia hecho tirar.

lspci: [http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/lspci.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/lspci.png)

if config: [http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/ifconfig.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/ifconfig.png)

---

### Post by emiliano_raso on 2008-11-05
Perdon, lo puse dos veces sin darme cuenta y no se como borrarlo.
Algun moderador que lo borre.

Un amigo me los habia hecho tirar.

lspci: [http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/lspci.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/lspci.png)

if config: [http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/ifconfig.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/ifconfig.png)

---

### Post by superjulin on 2008-11-06
Hola emiliano,podrias decirnos por favor cual es modelo del router que esta dando wi-fi.Segun lo que has posteado la IP entregada en la placa wi-fi es un rango raro el que esta entregando el router.
Proba con el siguiente comando para ver si llegara a cambiar el rango de IP
**ifconfig wlan0 down**(se va acortar la coneccion wi-fi)
**ifconfig wlan0 up**(levanta la placa wi-fi para volver a tener coneccion)

---

### Post by emiliano_raso on 2008-11-07
Tengo una muy mala noticia.
Pasó eso que a todo linuxero odia que le pase:
SE ARREGLÓ SOLO! ¬¬

Cuando botee la particion con Ubuntu para tirar los comandos que superjulin me dio, conecto sin problemas a internet.
Como  muy de vez en cuando eso pasaba, entonces reinicie la computadora, pero siguió andando bien.

Ahora tengo internet sin problemas. Realmente hubiera deseado saber que es lo que pasaba y habria preferido que no funcione.
Peeero bue... asi son las cosas xD

Cualquier problema vuelvo a postear.

Muchisimas gracias para los que me ayudaron de todas formas...

---

### Post by emiliano_raso on 2008-11-07
Bueno, me retracto de lo que digo, esta pasando de nuevo.

No se que es lo que pasa :-S

Prove los comandos que me pasaron y no funciono

---

### Post by ImplicitNone on 2008-11-07
Yo tuve exactamente el mismo problema (de hecho, tengo la misma placa wireless). Al parecer el conflicto viene por el lado del NetworkManger. Te digo como lo solucioné yo.

Primero eliminé el network-manager:

```
sudo aptitude remove network-manager
sudo aptitude purge network-manager

```
Reinicié y me conecté a la wifi por consola:

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid nombre_de_tu_red key tu_clave
sudo dhclient wlan0
```

Luego instalé un administrador de redes muy recomentado, denominado WICD:

Primero añadí el repositorio en orígenes del software:

```
deb http://apt.wicd.net intrepid extras
```

Ingresé la llave publica:
```

wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

Actualize apt-get:
```

sudo aptitude update
```

Luego lo instalé:
```

sudo aptitude install wicd
```

Reinicié y listo. El WICD me funciona de maravilla. En mi opinión personal es mucho mejor que el NetworkManager.

Espero que te sirva,
Saludos.

Actalización: No es necesario eliminar previamente el NetworkManager, obviamente las dependencias son resueltas por aptitude (es obvio pero se me pasó).

---

### Post by Apipote on 2008-11-09
> El WICD me funciona de maravilla. En mi opinión personal es mucho mejor que el NetworkManager.

Estoy de acuerdo, al menos por ahora.

Slds

---

### Post by emiliano_raso on 2008-12-03
Voy a hacer la prueba la semana que viene. Les agradezco mucho. Estoy complicado con la facultad.

Una pregunta: NetworkManager no es de KDE? Porque yo uso Ubuntu con Gnome.
Por las dudas pregunto. Capaz que estoy confundido.

De nuevo gracias.

---

### Post by Hei Ku on 2008-12-03
En KDE se llama KNetworkManager, como corresponde. :D

---

### Post by emiliano_raso on 2008-12-17
EXCELENTE IMPLICIT! FUNCIONÓ! MILES DE MILLONES DE GRACIAS!!!

Ademas aprendi como conectar por consola xD

---

