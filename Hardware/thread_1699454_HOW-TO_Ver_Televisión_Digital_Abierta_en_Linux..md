---
title: "HOW-TO: Ver Televisión Digital Abierta en Linux."
date: 2011-03-03
forum: Hardware
---

### Post by josecuervo86 on 2011-03-03
Hola a tod@s!! Hace tiempo que no paso por aca, pero hoy vengo a traerles este humilde "How to" para que aquellos que, como en mi caso, no tienen cable (sea por la razón que sea).

Como sabrán, hace unos cuantos meses se lanzó en el país lo que se llama [Televisión Digital Abierta]("http://www.tvdigitalargentina.gob.ar/"), que consiste en una transmisión de la señal de Tv por aire, pero a diferencia del viejo y conocido **aire**, este se transmite en forma digital en vez de analogicamente. 

El estándar que se utiliza se basa en el que usan los brasileros, y la gran mayoria de los paises de America del Sur, y se conoce como **SATVD-T** (Sistema Argentino de Televisión Digital Terrestre).

[IMG]http://i.imgur.com/Gk8l8.png[/IMG]
 
No voy a entrar en detalles de como es el sistema porque no soy la persona mas indicada para explicarlo, pero hay varias paginas dando vuelta donde se explica con lujo de detalles como funciona el sistema.

Lo que vengo a tratar de explicar es como hacer para recibir la señal de la televisión digital en su computadora en unos pasos muy sencillos. Este tutorial esta explicado para el modelo de sintonizador **PixelView PlayTV USB SBTVD** que es el que yo compre.

[IMG]http://i46.tinypic.com/1124cvq.jpg[/IMG]

Comencemos!!

**1.- lsusb**
Lo primero que hacemos es conectar el sintonizador y fijarnos que el sistema lo reconozca correctamente

```

$ lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 1554:5010 Prolink Microsystems Corp.** 
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

El que aparece en negrita es el sintonizador.

**2.- Bajar los drivers**
Primero que nada, desconectamos el sintonizdor (en caso de estar conectado) y en terminal ponemos:

```

$ hg clone http://www.linuxtv.org/hg/v4l-dvb 
$ cd v4l-dvb 
$ make 
$ sudo make rmmod 
$ sudo make install

```

**3.- Instalar firmware**

```

$ wget http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw 
$ cp dvb-usb-dib0700-1.20.fw /lib/firmware

```

Conectamos nuevamente el sintonizador.

**4.- Bajar las herramientas**
```

$ hg clone http://linuxtv.org/hg/dvb-apps 
$ cd dvb-apps 
$ make 
$ sudo make install 

```

**5.- Crear la lista de canales**
Para este paso creamos un documento en blanco al que llamaremos por ejemplo **channels.conf**

```

$ gedit channels.conf

```

le ponemos esta información dentro

```

# UHF channels 14 to 69
T 473142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 14
T 479142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 15
T 485142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 16
T 491142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 17
T 497142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 18
T 503142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 19
T 509142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 20
T 515142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 21
T 521142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 22
T 527142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 23
T 533142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 24
T 539142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 25
T 545142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 26
T 551142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 27
T 557142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 28
T 563142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 29
T 569142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 30
T 575142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 31
T 581142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 32
T 587142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 33
T 593142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 34
T 599142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 35
T 605142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 36
# channel 37 not used
T 617142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 38
T 623142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 39
T 629142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 40
T 635142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 41
T 641142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 42
T 647142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 43
T 653142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 44
T 659142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 45
T 665142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 46
T 671142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 47
T 677142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 48
T 683142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 49
T 689142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 50
T 695142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 51
T 701142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 52
T 707142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 53
T 713142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 54
T 719142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 55
T 725142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 56
T 731142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 57
T 737142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 58
T 743142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 59
T 749142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 60
T 755142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 61
T 761142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 62
T 767142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 63
T 773142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 64
T 779142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 65
T 785142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 66
T 791142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 67
T 797142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 68
T 803142857 6MHz 3/4 AUTO AUTO AUTO AUTO NONE # channel 69

```

y guardamos. Con esta información luego scannearemos cuales canales son los que estan disponibles en nuestra zona.

```

$ scan channels.conf > **canales.conf** 

```

En ese nuevo archivo **canales.conf** quedara la lista definitiva de los canales disponibles luego de que el programa scannee que frecuencias hay disponibles.



Con esto concluimos la configuración en general. Ahora a ver la tele!!

Para eso abrimos un reproductor multimedia, donde yo recomiendo VLC por la simplicidad y potencia. Una vez ahi, vamos a **Medio** > **Abrir archivo avanzado** y una vez ahi seleccionamos el archivo **canales.conf** que se creo anteriormente.

Una vez ahi vamos a **Ver** > **Lista de Reproducción** o (Ctrl + L) y ahi deberian figurar los canales disponibles.

A mi en este momento y en La Plata me figuran los siguientes:

Encuentro
Paka Paka
TaTeTi
Incaa Tv
Encuentro Movil
TV Publica HD
TV Publica 
Encuentro
GolTV
Vivra
Suri TV
Video Exito
GolTV Movil
CN23
C5N
TeleSur
Turismo
CN23 Movil

O sea, un buen par de canales, totalmente gratis y con una calidad que me dejo asombrado. Se supone que a medida que pase el tiempo se sumen mas canales, así que es una buena opción para aquellos a los que les resulta caro el cable, quieren ver el fulbo' y no les importa un poco de publicidad oficial de tanto en tanto =).

[IMG]http://i.imgur.com/ytEYZl.jpg[/IMG]

Recomendación adicional: este dongle usb trae una antena externa cuya base esta imantada. Traten de ponerla sobre algun objeto metálico ya que esto mejora muchisimo la recepción.


Espero que les haya servido!!

Saludos!!

---

### Post by z37a on 2011-03-03
Che muy buena la data! Mis felicitaciones, la verdad andaba buscando algo así para ver que onda, igualmente lo que mas me interesa ahora a mi es conseguir una placa que me permita conectarle un hdmi o un componente y que me grabe en 1080p lo que le mande! Soy un afortunado usuario de HD MAX asi que tengo varias pelis en el hd del deco que no puedo sacar por las buenas!

---

### Post by biale on 2011-03-04
Mis felicitaciones por haberlo logrado. Te pregunto desde donde estas logrando la recepción y también a que altura estas ubicado.

La pregunta viene de que según leí la antena transmisora platense esta ubicada en calle 52 y 31. También me había comentado que los niveles eran deficientes, pero esto puede haber cambiado...

Edito: Es set top box o dongle USB? Como estas entrando a la compu?

---

### Post by josecuervo86 on 2011-03-04
Mira, yo estoy aca:

[IMG]http://i.imgur.com/oC3ap.png[/IMG]

O sea bastante lejos de la antena para mi gusto, pero la salida que obtengo, mirando en este caso la señal de **TV Publica HD**, cuando scaneo es esta:

```

$ femon -H
FE: DiBcom 8000 ISDB-T (DVBT)
status SCVYL | signal  58% | snr   0% | ber 0 | unc 0 | FE_HAS_LOCK

```

Donde:
**S:** señal detectada
**C:** señal digital detectada
**V:** detección y corrección de errores estable
**Y:** bits de sincronización encontrados
**L:** señal adquirida
**FE_HAS_LOCK:** señal adquirida!!

**signal:** potencia de la señal en %
**snr:** relación señal/ruido
**ber:** tasa de bits con error
**unc:** bloques incorregibles

que me parece que esta bastante bien para la distancia que tengo de la antena.

En cuanto a la altura, estoy en el 6to piso así que mas o menos estare a 20 metros de altura (aprox. 3 metros por piso + PB).


El aparatito es un dongle USB, que viene con un cable de alargue USB y una antena bastante modesta que se conecta por una ficha "de aire" (no se como de llaman pero son esas redonditas sin acanaladuras que tienen un palito en el medio -re tecnica la descripción-)

Es importante remarcar que la recepción varia bastante segun la posición (mejora cerca de la ventana) y sobre que superficie este apoyado (crease o no, cuando lo imantas sobre una superficie metalica recibe mucho mejor).

Creo que por todo esto, y considerando mi ubicación, calcularia que la señal se debe recibir de 10 en todo el casco centrico de La Plata, Los Hornos, y calcularia que la zona de quintas y Romero pueden recibirla bien (no me se muchos barrios, pero los que esten equidistantes a la antena comparados con mi ubicación deberia recibir igual cantidad de señal o mas aun debido a la interferencia de los edificios del centro).


PD: para los interesados, ese dondle USB ronda los 250 pesos.

---

### Post by biale on 2011-03-05
Mas que interesante. Guiandome por el dibujo, los datos técnicos del dongle aparecen aqui:

[http://www.pixelview.com.ar/sintonizador-digital-isdb-tb.html](http://www.pixelview.com.ar/sintonizador-digital-isdb-tb.html)

Siguiendo el plano encuentro que estas esquivando una parte importante de los edificios de la zona céntrica, y ademas la altura ayuda mucho. A su vez, al ubicar la miniantena sobre una superficie metálica, el metal puede hacer las veces de reflector y aumentar la intensidad de campo.

Te cuento que La Plata siempre fue un lugar muy complejo en cuanto a la recepción de señales abiertas. Supuestamente el sistema debería poder cubrir en forma sencilla toda el area de recepción primaria, pero estas cosas son muy empiricas. Y por lo poco que he leido, las experiencias Europeas con la TDT también han sido muy variadas.

---

### Post by hectorivand on 2011-03-05
> **josecuervo86 said:**
> Mira, yo estoy aca:

[IMG]http://i.imgur.com/oC3ap.png[/IMG]

O sea bastante lejos de la antena para mi gusto, pero la salida que obtengo, mirando en este caso la señal de **TV Publica HD**, cuando scaneo es esta:

```

$ femon -H
FE: DiBcom 8000 ISDB-T (DVBT)
status SCVYL | signal  58% | snr   0% | ber 0 | unc 0 | FE_HAS_LOCK

```

Donde:
**S:** señal detectada
**C:** señal digital detectada
**V:** detección y corrección de errores estable
**Y:** bits de sincronización encontrados
**L:** señal adquirida
**FE_HAS_LOCK:** señal adquirida!!

**signal:** potencia de la señal en %
**snr:** relación señal/ruido
**ber:** tasa de bits con error
**unc:** bloques incorregibles

que me parece que esta bastante bien para la distancia que tengo de la antena.

En cuanto a la altura, estoy en el 6to piso así que mas o menos estare a 20 metros de altura (aprox. 3 metros por piso + PB).


El aparatito es un dongle USB, que viene con un cable de alargue USB y una antena bastante modesta que se conecta por una ficha "de aire" (no se como de llaman pero son esas redonditas sin acanaladuras que tienen un palito en el medio -re tecnica la descripción-)

Es importante remarcar que la recepción varia bastante segun la posición (mejora cerca de la ventana) y sobre que superficie este apoyado (crease o no, cuando lo imantas sobre una superficie metalica recibe mucho mejor).

Creo que por todo esto, y considerando mi ubicación, calcularia que la señal se debe recibir de 10 en todo el casco centrico de La Plata, Los Hornos, y calcularia que la zona de quintas y Romero pueden recibirla bien (no me se muchos barrios, pero los que esten equidistantes a la antena comparados con mi ubicación deberia recibir igual cantidad de señal o mas aun debido a la interferencia de los edificios del centro).


PD: para los interesados, ese dondle USB ronda los 250 pesos.

Excelente la información, si en todas esas cuadras te da %58 de señal con la antenita que trae, es un golazo, tranquilamente puede andar de 10 con una antena UHF externa, que según las especificaciones del aparatito, se puede adaptar, con lo cual, el nivel de señal, aumentaría muchísimo.

Saludos.
Nacho

---

### Post by biale on 2011-03-05
Si, también hay antenas caseras que pueden mejorar el nivel de la señal. Pero lo bonito del sistema es justamente no llegar a necesitar de una antena por infraestructura, pensemos mas en la recepciones moviles.

Siendo transmisión digital tampoco es productivo llegar al 100% de la señal, por encima de un cierto nivel de señal y de relacion señal/ ruido ya uno esta hecho.

---

### Post by josecuervo86 on 2011-03-05
> **biale said:**
> Mas que interesante. Guiandome por el dibujo, los datos técnicos del dongle aparecen aqui:

[http://www.pixelview.com.ar/sintonizador-digital-isdb-tb.html](http://www.pixelview.com.ar/sintonizador-digital-isdb-tb.html)

Siguiendo el plano encuentro que estas esquivando una parte importante de los edificios de la zona céntrica, y ademas la altura ayuda mucho. A su vez, al ubicar la miniantena sobre una superficie metálica, el metal puede hacer las veces de reflector y aumentar la intensidad de campo.

Te cuento que La Plata siempre fue un lugar muy complejo en cuanto a la recepción de señales abiertas. Supuestamente el sistema debería poder cubrir en forma sencilla toda el area de recepción primaria, pero estas cosas son muy empiricas. Y por lo poco que he leido, las experiencias Europeas con la TDT también han sido muy variadas.

Si, el dongle es exactamente ese. Lo bueno de este, y lo que hay que fijarse si se va a comprar uno, es que sea **fullseg** que son los que pueden recibir la señal en **HDTV**

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/ISDB-T_CH_Seg_Prog_allocation.jpg/431px-ISDB-T_CH_Seg_Prog_allocation.jpg[/IMG]

Si en cambio compras uno que solo dice Oneseg, vas a recibir solo uno de los 13 fragmentos (s0 generalmente) y que tiene una resolución bastante baja, ya que se usa para los dispositivos moviles, por ejemplo celulares.

En cuanto a lo que decis de la recepción de señales abiertas,siempre tuve problemas para agarrar los canales de aire con el tele, y con toda la furia pude llegar a ver America y canal 7 (este ultimo bastante mal).


> **hectorivand said:**
> Excelente la información, si en todas esas cuadras te da %58 de señal con la antenita que trae, es un golazo, tranquilamente puede andar de 10 con una antena UHF externa, que según las especificaciones del aparatito, se puede adaptar, con lo cual, el nivel de señal, aumentaría muchísimo.

Saludos.
Nacho


Sabes que estaba viendo si conseguia una antena externa para ver que pasaba, voy a ver si me pongo en campaña jeje.

---

### Post by enzomatrix on 2011-03-26
Un par de detalles que actualizan la información.
En las versiones nuevas de Ubuntu (lo he probado con 10.10 en adelante) no hace falta descargar el firmware porque ya está incluido en el paquete linux-firmware.
El paquete dvb-apps esta en el repositorio universe, así que en caso de no estar instalado lo instalamos con apt-get y listo, tampoco hace falta compilar.
Con estos detalles, ese dongle funciona en Ubuntu prácticamente con conectarlo. Solamente tenemos que seguir las instrucciones desde el paso 5 en adelante.

---

### Post by biale on 2011-03-27
La duda que queda es hasta donde lo que se aplica a dvb-t también funciona con isdb-t. A eso sumo que de antemano tampoco se puede saber en todos los casos si los niveles de señal son los mínimos como para que la cosa funcione.

Por ejemplo, para las "dvb-apps" en synaptic dice "Applications and utilities geared towards the initial setup, testing and operation of an DVB device supporting the DVB-S, DVB-C, DVB-T, and ATSC standards."

---

### Post by TTDURING on 2011-06-05
Hola a todos, estoy en la zona de Liniers  y realmente se ve muy bien,tengo una pregunta, alguien pudo configurar el control remoto?en linux obvio 
Lo configuro con dpkg-reconfigure lirc y cat/proc/bus/input/devices y nada, me tira ok, pero nada.
Otra, solamente me sale sonido cuando utilizo vlc, en mplayer y me-tv tengo imagen pero no tengo sonido.
Saludos

---

### Post by anarko on 2011-06-09
Hola gente, me compre un dongle mygica ( [http://www.mygica.com/pa/s119.asp](http://www.mygica.com/pa/s119.asp) ) es half-segment, nada de 1080, pero para la netbook esta bien. 
El primer problema que tube es que el driver que viene con el kernel no es ISDBT y venia los canales de antina ( pero sin la codificación no se pueden ver ). Patchie el modulos del kernel y todo perfecto.

Ahora los problemas : 
Busco los canales y veo el listado de canales, pero el scan no puede identificar los pid de las señales. Para identificar los pid use el dvbsnoop. Y para sintonizar probe con TODOS los soft que soportan dvb y ninguno pudo, la unica forma de ver algo es con gnutv que puedo decirle que guarde el streaming a un archivo y abrirlo con el mplayer ( nigun otro lo puede abrir ). El problema es que el unico canal que se ve con este metodo es telefe.

Despues si uso el tzap para sintonizar y el dvbstrem para capturar el stream a un archivo puedo ver los otros canales usando el mplayer con la opcion -demuxer lavf pero no detecta el sonido.

¿A alguien le paso algo parecido? ¿Porque telefe si sabe transmitir y el resto de los canales K no?

El VLC no abro ninsiquiera el video bien capturado con el gnutv, no se porque pero no va ni para atras el VLC en esto me dejo apata.

PD: JoseCuervo podrias postear como te quedo el archivo canales.conf?
Yo use otra lista de frecuencias, esa la encontraste para brasil no? Los drivers de windows traia una lista para argentina.

```

T 93143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 105143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 173143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 473143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 479143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 485143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 491143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 497143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 503143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 509143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 515143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 521143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 527143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 533143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 539143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 545143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 551143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 557143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 563143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 569143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 575143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 581143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 587143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 593143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 599143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 605143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 617143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 623143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 629143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 635143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 641143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 647143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 653143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 659143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 665143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 671143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 677143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 683143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 689143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 695143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 701143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 707143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 713143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 719143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 725143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 731143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 737143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 743143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 749143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 755143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 761143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 767143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 773143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 779143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 785143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 791143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 797143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE
T 803143000 6MHz 2/3 NONE QAM64 8k 1/8 NONE

```

---

### Post by TTDURING on 2011-06-10
Hola anarKo, te paso mi archivo channels.conf. lo tengo copiado en .mplayer en mi home y en /home/#####/.local/share/vlc/,
en VLC anda de lujo, pero en mplayer con la  opcion -demuxer lavf sale video sin sonido, tengo entendido que hay problemas con el reconocimiento de los pid de audio pero no se como repararlo, espero que te sea util.

El archivo channels.conf lo genere si no recuerdo mal con $scan freq.conf > channels.conf

Tambien mira este link [http://osiux.com/tv/tv-digital-geniatech-usb-mygica-s87-dibcom-stk8096gp](http://osiux.com/tv/tv-digital-geniatech-usb-mygica-s87-dibcom-stk8096gp)

saludos

Encuentro:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2624
Paka Paka:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2625
TaTeTi:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2626
Incaa Tv:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2627
Encuentro Movil:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2628
TV Publica :527142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:59224
TV Publica HD:527142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:59201
Construir:527142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:59202
GolTV:533142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2624
Vivra:533142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2625
Suri TV:533142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:304:305:2626
Video Exito:533142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:320:321:2627
GolTV Movil:533142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:336:337:2628
CN23:539142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2624
C5N:539142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2625
TeleSur:539142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2626
Turismo:539142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2627
CN23 Movil:539142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:2628
C5N HD:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:273:274:23456
VESVI HD:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:289:290:23457
C5N Movil:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:529:530:23480
Telefe HD PRUEBA:593142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57408
Telefe SD:593142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57409
Telefe Movil:593142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:529:530:57432
America HD Prueba:605142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57440
America SD:605142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57441
A24 Prueba:605142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57442
America 1 seg:605142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:57464

---

### Post by anarko on 2011-06-10
Gracias por la info, tenes el mismo problema que yo. 

```
Encuentro:521142857:INVERSION_AUTO:BANDWIDTH_6_MHZ :FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO: GUARD_INTERVAL_AUTO:HIERARCHY_NONE:[COLOR="Red"]VIDEOPID[/COLOR]:[COLOR="Red"]AUDIOPID[/COLOR]:2624
```

Fijate que ahi marque en rojo donde deberia estar el pid de video y audio, el problem que tenes vos es el mismo que el mio, no te reconoce los pids de los canales y pone 0 y 0, a mi solo el de telefe movil me vio. 

Instala el dvbsnoop ( en esta en los repositorios ) con eso te dice que pid esta transmitiendo cada cosa. Si no también podes usar el dvbtraffic que te muestra tambien los pids que estas viendo.
Antes tenes que sintonizar el canal con 
```
tzap -r -c channles.conf "Nombre del canal"
```
```
dvbtraffic
```
o
```
dvbsnoop -s pidscan
```

También habiendo sintonizado el canal con tzap podes habrirlo con mplayer poniendo : mplayer /dev/dvb/adapter..... 


A mi usando el femon me dice que tengo demasiados errores, estoy probando con la antena que viene con el dongle, voy a probar con una antena UHF externa mas grande.

Aca estan las instrucciones para hacer una antena homemade que anda 10 puntos, yo en vez de perchas usa alambre galvanizado y anda muy bien testeada con una TV con ISDBT y se ven los canales 1080 con una exelente calidad. 

[http://vimeo.com/2931902](http://vimeo.com/2931902)

En el link que me pasas dicen como hacer con la mygica s870, la que tengo yo usa otro chipset, pero el problema del driver ya lo solucione patcheando el codigo del modulo antes de compilarlo y anda en ISDB-T.

---

### Post by josecuervo86 on 2011-06-10
[quote=anarko]PD: JoseCuervo podrias postear como te quedo el archivo canales.conf?
Yo use otra lista de frecuencias, esa la encontraste para brasil no? Los drivers de windows traia una lista para argentina.[/quote]

Anarko, justo en este momento no estoy en casa, el lunes recien llego asique te debo por ahora el canales.conf. Correcto, esa lista de frecuencias las saque de una pagina brasilera, pero anda de 10, la probaste? Yo despues pruebo esa y me fijo como anda. El lunes cuelgo el channels.conf

Saludos!!

---

### Post by josecuervo86 on 2011-06-10
> **anarko said:**
> 
Ahora los problemas : 
Busco los canales y veo el listado de canales, pero el scan no puede identificar los pid de las señales. Para identificar los pid use el dvbsnoop. Y para sintonizar probe con TODOS los soft que soportan dvb y ninguno pudo, la unica forma de ver algo es con gnutv que puedo decirle que guarde el streaming a un archivo y abrirlo con el mplayer ( nigun otro lo puede abrir ). El problema es que el unico canal que se ve con este metodo es telefe.


Yo sigo sin entender algo, si scaneas el archivo con frecuencias y creas un channels.conf no podes abrirlo con vlc?

---

### Post by anarko on 2011-06-10
> **josecuervo86 said:**
> Yo sigo sin entender algo, si scaneas el archivo con frecuencias y creas un channels.conf no podes abrirlo con vlc?

El scan no me da los numeros de pid, los tengo que buscar con el dvbtraffic o dvbsnoop. Pero igual si se los agrego al channles.conf tampoco anda el VLC. La unica forma en la que puedo ver un canal 100% ( audio y video ) es sintonizando con el gnutv telefe movil, diciendole al gnutv que guarde el stream en un archivo y ese archivo abrirlo con el mplayer sin opciones de demuxer ni nada (Nisiquiera asi anda el VLC ).

Probe las 2 listas de frecuencia y en las 2 me pasa lo mismo, me encuentra todos los canales pero sin pid, el unico que encuentra el pid es el de telefe movil, puede ser por un problema en la recepcion estoy probando con la antena del dongle, mañana voy a probar con una antena casera que anda muy bien en TV's con sinto isdb-t. ( la que postie el link de vimeo )

---

### Post by josecuervo86 on 2011-06-10
Ok, fiajte con este comando:
```
femon -H
``` una vez que hayas sintonizado un canal (sintonizar nomas, no importa que no lo veas) y fiajte que valores te devuelve, probablemente si es problema de la antena tendras o bien poca potencia de las señal o muchos errores. Postea el resultado de un par de lineas para ver que onda.

---

### Post by anarko on 2011-06-10
Aca te dejo unos screenshot de mi situacion :

En el scan se ve que no puede conseguir fijar el pid en algunos canales pero en la red de Telefe si, incluso los HD, solo que despues no puede recibirlos porque la plaka es half-segment.

El Femon, sin importar que canal sintonice hace siempre los mismo

Con el Gnutv puedo sintonizar Telefe Movil y se ve 10 puntos.

Despues sintonzando por ejemplo Encuentro Movil con el tzap y haciendo un cat /dev/dvb/adapter0/dvr0 > arhivo.ts y poniendo en otra consola el mplayer se ve el canal pero sin sonido y tengo que decirle que use el demuxer livaudiovideo en vez de mpegts que es el correcto.

Demas esta aclarar que la plaka en windows anda como es debido, yo me tiro mas a que esten pifiando en la transmision y que la plaka sea demaciado sensible a ese pifie.

El driver que estoy usando es la ultima version de linuxtv.org patcheado para que sea ISDBT, la plaka es ISDBT pero el modulo oficial para siano aparentemente no tiene soporte 100% ISDBT, tambien puede venir por ese lado, pero me llama la atencion que 1 canal anda perfecto y los demas no.


PD EDIT : Ya descubri el problema, pero no la solucion.
El problema es que en todas las redes menos en telefe el PID 0 es inestables, va y viene y aparentemente ese PID 0 es bastante importante, ese y los 2 de audio y video son los unicos que son estables en la red de telefe.

Sintonizando un canal cualquiera 
```
 
anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:    8 (0x0008)  [unknown]
PID found:   16 (0x0010)  [SECTION: Network Information Table (NIT) - actual network]
PID found:  336 (0x0150)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  337 (0x0151)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
PID found: 8136 (0x1fc8)  [SECTION: Program Map Table (PMT)]
PID found: 8191 (0x1fff)  [stuffing]
anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:  336 (0x0150)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  337 (0x0151)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
PID found: 8136 (0x1fc8)  [SECTION: Program Map Table (PMT)]
PID found: 8191 (0x1fff)  [stuffing]
anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:  336 (0x0150)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  337 (0x0151)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
PID found:  769 (0x0301)  [unknown]
PID found: 8136 (0x1fc8)  [SECTION: Program Map Table (PMT)]
PID found: 8191 (0x1fff)  [stuffing]

```

Sintonzando Telefe :
```

anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:    0 (0x0000)  [SECTION: Program Association Table (PAT)]
PID found:  529 (0x0211)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  530 (0x0212)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:    0 (0x0000)  [SECTION: Program Association Table (PAT)]
PID found:  528 (0x0210)  [unknown]
PID found:  529 (0x0211)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  530 (0x0212)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
PID found: 8136 (0x1fc8)  [SECTION: Program Map Table (PMT)]
anarko@anarka-mobile:~/isdbt$ dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------
PID found:    0 (0x0000)  [SECTION: Program Association Table (PAT)]
PID found:   16 (0x0010)  [SECTION: Network Information Table (NIT) - actual network]
PID found:  529 (0x0211)  [PS/PES: ITU-T Rec. H.262 | ISO/IEC 13818-2 or ISO/IEC 11172-2 video stream]
PID found:  530 (0x0212)  [PS/PES: ISO/IEC 13818-3 or ISO/IEC 11172-3 audio stream]
PID found: 8136 (0x1fc8)  [SECTION: Program Map Table (PMT)]

```

---

### Post by TTDURING on 2011-06-11
Anarko, gracias voy a probar, pero lo raro es que con el vlc funciona perfectamente, imagen y sonido pero con en mplayer o me-tv o kaffeine solamente imagen, sera algún problema de codec?

Saludos

Josecuervo lograste hacer andar el control remoto ?

---

### Post by anarko on 2011-06-11
> **TTDURING said:**
> Anarko, gracias voy a probar, pero lo raro es que con el vlc funciona perfectamente, imagen y sonido pero con en mplayer o me-tv o kaffeine solamente imagen, sera algún problema de codec?

Saludos

Josecuervo lograste hacer andar el control remoto ?

Los codecs no creo que sean ... son h264 generico y mpeg2 audio. Son bastante comunues. 

Proba haciendo como hago yo con el gnutv y despues abriendo el archivo que genera el gnutv con el mplayer. Por ahi tenes algun problema parecido al mio que los pids no son los suficientemente estables, proba eso con el dbvtraffic ahi ves todos los pids como aparecen y desaparecen.

---

### Post by josecuervo86 on 2011-06-11
Anarko, hay algo que me llama la atencion en la salida de femon y es que marca que la potencia de la señal es 0. Eso me resulta rarisimo, porque en si, por la salida que da recibe bien todos los canales.

Otra cosa, si usas el channels.conf crudo (sin PID's) que pasa? no los abre? solo podes ver telefe? se ven sin sonido?

[quote=TTDURING]Josecuervo lograste hacer andar el control remoto ?[/quote]
La verdad que todavia no probe de acomodarlo. Andar anda, pero los botones estan desconfigurados, o por lo menos no hacen lo que se supone que deberian hacer jeje. Despues me voy a poner a ver si lo hago andar.

---

### Post by josecuervo86 on 2011-06-13
Aca va el channels.conf! (en forma de .txt)

---

### Post by anarko on 2011-06-13
Gracias por la lista de canales, queria comprobar si los pid que estaba obteniendo yo eran los mismos que los de alguien que si le andaba. Y si son los mismo. 

Estos 3 canales se ven? 
```

C5N HD:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:23456
VESVI HD:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:23457
C5N Movil:551142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:0:0:23480
```

Por otro lado podrías hacerme el favor de ver si a vos te pasa lo mismo de que el PID 0 aparece y desaparece todo el tiempo, porque por ahi es un problema del driver de mi plaka y si a vos te pasa lo mismo puedo mirar el driver de la tuya para ver cono lo corrigen. No seria la primera vez que meta mano en un modulo del kernel.

Saludos.

---

### Post by josecuervo86 on 2011-06-13
[quote=anarko]Estos 3 canales se ven?[/quote]

No, esos canales no se ven, y como vos bien me lo haces notar, esos tienen PID 0:0 asique calculo que por ahi anda el problema.

Dejame que haga unas pruebas y te contesto lo de los PID

---

### Post by josecuervo86 on 2011-06-13
[quote=anarko]Por otro lado podrías hacerme el favor de ver si a vos te pasa lo mismo de que el PID 0 aparece y desaparece todo el tiempo, porque por ahi es un problema del driver de mi plaka y si a vos te pasa lo mismo puedo mirar el driver de la tuya para ver cono lo corrigen. No seria la primera vez que meta mano en un modulo del kernel.
[/quote] Queres que pruebe con dvbsnoop los canales que tienen el PID 0 o queres saber si en otros channels.conf aparecen los demas canales con PID 0??

---

### Post by anarko on 2011-06-13
> **josecuervo86 said:**
> Queres que pruebe con dvbsnoop los canales que tienen el PID 0 o queres saber si en otros channels.conf aparecen los demas canales con PID 0??


Fijate si podes hacerme el favor con el dvtraffic o el dbvsnoop si el pid 0 aparece y desaparece ( se ve mejor con el dvbtraffic en el otro directamente no lo muestra por inestable )

---

### Post by josecuervo86 on 2011-06-14
Che, sintonizo cualquiera de los canales, pero dvbtraffic no me devuelve absolutamente nada, se supone que debe mostrarte las PID de los canales que estas sintonizando no?

---

### Post by anarko on 2011-06-14
La salida del dvtraffic deberia ser algo asi : 
```

0000    24 p/s     4 kb/s    37 kbit
0010    20 p/s     3 kb/s    31 kbit
0011    20 p/s     3 kb/s    31 kbit
0012    70 p/s    12 kb/s   106 kbit
0015     1 p/s     0 kb/s     2 kbit
0080    26 p/s     4 kb/s    40 kbit
0082    26 p/s     4 kb/s    40 kbit
0087    25 p/s     4 kb/s    38 kbit
0100    25 p/s     4 kb/s    38 kbit
0101    25 p/s     4 kb/s    38 kbit
0102    24 p/s     4 kb/s    37 kbit
0200  8567 p/s  1572 kb/s 12885 kbit
0201  4708 p/s   864 kb/s  7081 kbit
0205   926 p/s   170 kb/s  1392 kbit
0240    49 p/s     8 kb/s    75 kbit
0241    49 p/s     8 kb/s    75 kbit
028b   261 p/s    47 kb/s   393 kbit
0294   174 p/s    31 kb/s   262 kbit
0295   130 p/s    23 kb/s   196 kbit
02bc    75 p/s    13 kb/s   113 kbit
1fff    87 p/s    15 kb/s   131 kbit
2000 15329 p/s  2814 kb/s 23055 kbit
-PID--FREQ-----BANDWIDTH-BANDWIDTH-

```

Proba sintonizando el canal con tzap -r -c en vez de con el vlc porque el vlc toma exclusivo el dispositivo.

---

### Post by josecuervo86 on 2011-06-14
sisi, probe con tzap pero no sale nada de nada o_O

---

### Post by anarko on 2011-06-17
> **josecuervo86 said:**
> sisi, probe con tzap pero no sale nada de nada o_O

Sori la desaparecida, estoy en epoca de parciales y mi vida se puso en pausa unas semanas, en cuanto termine veo que paso con el driver haber si se puede solucionar el problema del pid 0.

Salutes

---

### Post by josecuervo86 on 2011-06-17
che, pero el channels.conf que te pase, si lo pones en el vlc no anda?

---

### Post by anarko on 2011-06-18
Con el channles.conf que me pasaste vos el VLC dice esto que se ve en el screen, es esactamente lo mismo que dice con el channles que cree yo.

---

### Post by TTDURING on 2011-06-20
Hola, les paso mi archivo channels.conf se ven todos los canales con audio y video en vlc en mplayer solamente video

Saludos

---

### Post by anarko on 2011-06-20
Che gente con suerte... hjajaja
Yo me estoy rompiendo los cuernos como un beduino. Incluso se ve un canal que en el channles.conf tiene 0 en los pids. 
Estaría bueno saber que version de VLC, que version de kernel y de dvb-tools.
Fijate si podes postear el log del VLC, abri una consola y ejecuta "vlc -vvv" con eso sale todo el debug.
Esto me dice a mi cuando le doy al vlc con telefe movil, es el unico canal que detecta bien el pid y que se puede sintonizar pero solo con el gnutv


PD: Cuanta cantidad de chucherias que tenes en el escritorio :p

---

### Post by josecuervo86 on 2011-06-20
VLC: 1.1.3
kernel: 2.6.32-5
dvbap:1.1.1+rev1355-1

Vos instalaste siguiendo mi tutorial o con otro?

---

### Post by TTDURING on 2011-06-20
Ubuntu 10.10 x86_64
VLC: 1.1.4
kernel: 2.6.35-28
dvbap:1.1.1+rev1355-1

Saludos

---

### Post by anarko on 2011-06-20
Gracias a ambos, yo tengo todo mas nuevo ( ubuntu 11.04 ), salvo el dvb apps. 
VLC : 1.1.9
Kernel : 2.6.38-algo
DVB-apps : 1.1.1+rev1335-algo

Voy a ver si bajo y compilo un vlc mas viejo o si directamente bajo un ubuntu 10.10 y lo instalo en la netbook. 

JoseCuervo, lo instale de otra manera, igual hace nada mas que 12 años que uso linux, aveces no necesito seguir tutoriales, cuando llegue acá es porque estaba buscando info por el problema que tengo. 

Saludos.

---

### Post by josecuervo86 on 2011-06-21
[quote=anarko]Gracias a ambos, yo tengo todo mas nuevo ( ubuntu 11.04 )[/quote] Yo estoy en debian squeeze jeje, asi que imaginate.

[quote=anarko]igual hace nada mas que 12 años que uso linux, aveces no necesito seguir tutoriales[/quote]
Toda una vida ehh, yo apenas 3, pero no me muevo mas!

---

### Post by anarko on 2011-06-23
Bueno, probe con un ubuntu 10.10 y me hace exactamente lo mismo, el problema esta en el patch ( o tambien en el driver ) para que el dongle sea ISDB-T, ya que usando el driver sin patchar funciona perfecto, pero al ser solo DVB-T no veo los canales de aire sino antina. Y como los mala onda de antina encriptan las señales solo veo el canal de la programacion y las radios.

Cuando termine de rendir voy a ver si reviso el driver por si encuentro en que le estan pifiando.

Saludos

---

### Post by YAFU on 2011-06-23
Hola, que tal?

Quería saber si alguien pudo hacer funcionar el control remoto del dongle USB MyGica s870, en Natty (o cualquier versión en realidad). Veo que por ahí hablan de un parche, otros mencionan que conocen a alguien que pudo hacerlo funcionar pero no hay nada cierto, y quienes dicen que en Natty no sería necesario el parche, con ir-keytable. También los que comentan que no pudieron hacer funcionar controles similares en Natty por algún problema en Lirc. En fin, no encontré ninguna guía precisa de como hacer funcionar el control remoto. 
Sería interesante que los que tenemos este dongle veamos de hacerlo funcionar y crear una guía, quizás abriendo un hilo y discutiendo allí.
Yo llegué hasta mapear las teclas copiadas del parche con ir-keytable. Después Lirc un desastre. Por malas experiencias anteriores, leo la palabra Lirc y tiemblo...
Saludos.

---

