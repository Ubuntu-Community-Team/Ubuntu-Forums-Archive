---
title: "auxilio actualice el 8.04 por el 8.10 y no arranca"
date: 2008-11-06
forum: Hardware
---

### Post by aleittte on 2008-11-06
hola! la cosa es asi lo actualice y desde ese dia que lo unico que veo es la pantalla de entrada y ni siquiera puedo poner el usuario ni la contraseña ya que no reconoce el teclado ni el mouse.....
ya no se que hacer...ayuda por favor!!!

---

### Post by guillermolisi on 2008-11-07
> **aleittte said:**
> hola! la cosa es asi lo actualice y desde ese dia que lo unico que veo es la pantalla de entrada y ni siquiera puedo poner el usuario ni la contraseña ya que no reconoce el teclado ni el mouse.....
ya no se que hacer...ayuda por favor!!!

Para tener una nocion de lo que esta pasando, si tecleas Ctrl+Alt+F1 no hace nada o te muestra la consola ?

La pantalla de entrada es la que te pide usuario y contraseña o es otra ?

Que placa de video tenes ?

Estas con Gnome ?

Teclado y mouse PS/2 o USB ?

---

### Post by aleittte on 2008-11-07
la pantalla es la de entrada placa de video es on board a la consola puedo acceder y logearme pero no en el modo grafico el teclado y el mouse no se que es ps/2 pero se conectan comun y no se supone que si es ubuntu es gnome y si es kubuntu es kde? no se soy bastante nueva en esto asi que disculpa mi ignorancia.

---

### Post by guillermolisi on 2008-11-07
> **aleittte said:**
> la pantalla es la de entrada placa de video es on board a la consola puedo acceder y logearme pero no en el modo grafico el teclado y el mouse no se que es ps/2 pero se conectan comun y no se supone que si es ubuntu es gnome y si es kubuntu es kde? no se soy bastante nueva en esto asi que disculpa mi ignorancia.

Seria de mucha ayuda que pases que marca y modelo es la placa de video integrada porque si podes ir a la consola el problema no es de hardware sino de drivers de video, por eso no te muestra el escritorio grafico.

La interface PS/2 es un conector mini DIN, circular, de 6 pines si no recuerdo mal.
Los que son USB tienen la ficha clasica USB plana.

Podes tener Ubuntu con KDE, con Gnome, con Enlightement, con una variedad de escritorios y windows managers distintos, mas alla de que se distribuyan copias especificas. En la base operativa todos son Ubuntu.

Podes haber instalado Kubuntu y como no te gusto el nuevo KDE le instalaste Gnome e inicias sesion con este escritorio grafico, y se podria decir que instalaste Kubuntu de todas formas.

Personalmente instalo Ubuntu con el Alternate y luego el escritorio grafico que quiero usar, sea cual sea.

Como te decia, el problema que tenes es que el software que soporta la ejecucion del escritorio grafico, Xorg-11 se llama, no puede comunicarse con la placa de video porque no esta usando el driver adecuado.

Para saber cual va hay que saber que marca/modelo/procesador tiene la placa de video (aunque este integrada, en el manual de la mother esta informado este dato).

---

### Post by sajnox on 2008-11-07
Si antes andaba y ahora no, podes probar un par de cosas

1) Cuando arranca vas a la terminal ctrl + alt + f1 y te logueas con tu user y pass (recorda que cuando ingresas el password la pantalla no muestra nada). Una vez logueado escribis

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Te pide la contraseña y listo, luego escribis

```
startx
```

Si no funciona vas a la opcion 2

2) Trata de bootear con el kernel anterior, eso lo haces cuando arranca (donde pregunta que SO vas a arrancar) y elegis la tercer linea (la primera es el kernel actual, la segunda es para modo seguro y la tercera deberia ser el kernel anterior)

Aunque te funcione esta solucion por favor pasanos los datos que te pidio guillermo

Saludos

---

### Post by aleittte on 2008-11-07
hola gracias por responder. me fije y en el manual no dice nada de la placa de video. lo que si tengo son los datos del equipo en si es una commodore ke 2140dual core y el mother es biostar ( p4m900). el teclado y el mouse son ps/2. ahora voy a probar lo que me dijo sajnox y veo que onda. besos y deseenme suerte

---

### Post by aleittte on 2008-11-07
bueno a ver hice lo que dijo sajnox y me tiroun par de cartelitos paso a ponerlos
xauth: /home/alejandra/.Xauthoriti file not writable, changes will bi ignored
xauth: error in locking authority file /home/alejandra/.Xauthority 
fatal server error  server is already active for display 0 if this server is no longer running, remove /tem/.XO-lock and start again
no protocol specified 
giving up
xinit: resource temporarilly unavailable(errno 11): unable to conect to xserver
xinit: no such process(errno3) server error
xauth: error in locking authority file /home7alejandra/.Xauthority


y sigo sin poder entrar.
probe buscar lo del kernel anterior pero solo figura ubuntu 8.10 y tengo 4 opciones dos de la cuales son iguales a las dos primeras..........
que hago?

---

### Post by sajnox on 2008-11-09
> **aleittte said:**
> probe buscar lo del kernel anterior pero solo figura ubuntu 8.10 y tengo 4 opciones dos de la cuales son iguales a las dos primeras..........
que hago?

Si te figuran 4 opciones opta por la tercera, la diferencia puede ser muy sutil.

---

### Post by sajnox on 2008-11-09
Probemos con lo siguiente:

Arrancas y vas a la terminal con ctrl + alt + f1, loguin y password y adentro

1) Paramos el entorno grafico por que dice que esta corriendo
```

sudo /etc/init.d/gdm stop
```

2) Borramos el archivo que dice que molesta (si bien no lo conozco entiendo que te genera un archivo temporal, y algo me dice que es el que molesta)

```
sudo rm /temp/.XO-lock
```

3) Reconfiguramos nuevamente el x server
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Contanos si asi funciona

---

### Post by guillermolisi on 2008-11-09
> **aleittte said:**
> hola gracias por responder. me fije y en el manual no dice nada de la placa de video. lo que si tengo son los datos del equipo en si es una commodore ke 2140dual core y el mother es biostar ( p4m900). el teclado y el mouse son ps/2. ahora voy a probar lo que me dijo sajnox y veo que onda. besos y deseenme suerte
Esa motherboard viene con la siguiente placa/chip de video:

INTEGRATED VIDEO                    
<li class="SpecList">VIA Chrome9 HC IGP, On Board Graphic Max. Memory Share Up to 256MB

Desde ya te cuento que hacer funcionar la aceleracion 3G con esas placas Via es todo un problema. La mayoria opto por poner una nVidia o una ATI en su lugar (anulas la integrada al poner la discreta).

Te animas a postear el contenido del archivo /etc/X11/xorg.conf ?

Para ello abris una consola y escribis
```
less /etc/X11/xorg.conf
```Pintas todo lo que salga, copias al clippboard y lo pegas en el mensaje.

---

### Post by aleittte on 2008-11-09
hola soy feliz tengo otra vez mi maquina y saben lo que hice le di apt-get dist-upgrade y estuvo mil horas y salio y ya esta andando..... si les parece una pavada les pido perdon pero como se daran cuenta soy novatisima.........
muy agradecida por la ayuda!!!!!
alejandra

---

