---
title: "Video y placa de video Intel 865G"
date: 2009-08-14
forum: Hardware
---

### Post by viper3k on 2009-08-14
Hola , tengo un problemon terrible , la cosa es asi tengo una 

pentium 4 con 512 de ram ddr1 y placa tmb intel con grafica integrada de 64 mb

bueno el problema aparece que , en windows obviamente tengo que instalarle los drivers para la placa grafica integrada , pero en ubuntu no me los pide ni me los detecta cuando me fijo en Controladores de Hardware.

y no puedo reproducir ningun video ya sea mp4 avi mkv etc , tengo todos los codecs de todo, me baje el vlc y el mplayer pero ninguno me deja reproducirl videos , se cierran al toque en menos de 1 segundo los videos

yo pienso que deve ser problema de los drivers de video xq ademas en windows con esa placa puedo por ejemplo juegar al World of Warcraft lo mas bien pero aca apenas si puedo jugar al quake 2 que se me traba todo

Por favor , si alguien puede ayudarme se lo agradeceria eternamente :S
:(:(:(:(:(:(:(:(

pd la placa es Intel(R) 865G Chipset

---

### Post by rafaelca on 2009-08-14
Yo tengo ATI RADEON 9250 128 MB PCI.

No uso Driver's.

A decir verdad no los necesito.

Tu problema es el mismo que lo que me pasaba.

**SOLUCIÓN:** [http://ubuntuforums.org/showthread.php?t=1240431](http://ubuntuforums.org/showthread.php?t=1240431)

**TE ARRECOMIENDO TAMBIEN:** [http://ubuntuforums.org/showthread.php?t=1240434](http://ubuntuforums.org/showthread.php?t=1240434)

Onjala se solucione!:)

PD: Si puedes agregame: [email]se-rafaxulo@hotmail.com[/email]

salu2 ;)

---

### Post by krakc on 2009-08-14
A mi me pasaba exactamente lo mismo cuando entraba al ubuntu con mi monitor pegado a la board, todo se soluciono cuando pude configurar mi aceleradora.

prueba bajando los drivers de esa placa directamente de la pagina de intel y veras como se te soluciona. son drivers no te a reproducir ni medio video.

---

### Post by viper3k on 2009-08-14
> **rafaelca said:**
> Yo tengo ATI RADEON 9250 128 MB PCI.

No uso Driver's.

A decir verdad no los necesito.

Tu problema es el mismo que lo que me pasaba.

**SOLUCIÓN:** [http://ubuntuforums.org/showthread.php?t=1240431](http://ubuntuforums.org/showthread.php?t=1240431)

**TE ARRECOMIENDO TAMBIEN:** [http://ubuntuforums.org/showthread.php?t=1240434](http://ubuntuforums.org/showthread.php?t=1240434)

Onjala se solucione!:)

PD: Si puedes agregame: [email]se-rafaxulo@hotmail.com[/email]

salu2 ;)

ya probe esa solucion pero no me funciono ya lo tenia instalado el ubuntu-restricted , igual prober reinstalandolo y nada 

asiq ahora estoy buscando los drivers para isntalarlos y configurarlos

igual , muchas gracias por la molestia

---

### Post by rafaelca on 2009-08-14
> **viper3k said:**
> ya probe esa solucion pero no me funciono ya lo tenia instalado el ubuntu-restricted , igual prober reinstalandolo y nada 

asiq ahora estoy buscando los drivers para isntalarlos y configurarlos

igual , muchas gracias por la molestia
OK mucha suerte ! ;)

Ami los ati catalyst los instale y reinicie y tube que formatear por que nose que trasteo jue :D

---

### Post by josecuervo86 on 2009-08-14
Podes hacer lo siguiente: en una terminal ejecuta

```
vlc
```

y trata de reproducir un video. Cuando aparezca el mensaje de error en la terminal, copialo y pegalo aca para tener alguna pista de que puede estar pasando

---

### Post by viper3k on 2009-08-14
> **josecuervo86 said:**
> Podes hacer lo siguiente: en una terminal ejecuta

```
vlc
```

y trata de reproducir un video. Cuando aparezca el mensaje de error en la terminal, copialo y pegalo aca para tener alguna pista de que puede estar pasando

buena idea me aparece esto

```

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
viper@viper-pc:~$ 

```

supongo que el "insufficient resources for operation" sera recursos graficos o algo asi :P

toy tratando de instalar los drivers me los baje estaban en tar.bz2 los descomprimi y ahora voya ver si puedo compilarlos

gracias por el tiempo

---

### Post by josecuervo86 on 2009-08-14
Mira, fijate por aca [0] que comentan que tipo de error es el que te aparece. Resumidamente, y como bien interpretaste vos, esta relacionado con la placa de video. Una posible solución para de cualquier modo poder ver los videos es correr vlc del siguiente modo:

```
vlc --vout x11
```

De cualquier manera, esperemos a ver que pasa una vez compilado el driver

[0] [http://forums.fedoraforum.org/showthread.php?t=104445]("http://forums.fedoraforum.org/showthread.php?t=104445")

---

### Post by viper3k on 2009-08-14
> **josecuervo86 said:**
> Mira, fijate por aca [0] que comentan que tipo de error es el que te aparece. Resumidamente, y como bien interpretaste vos, esta relacionado con la placa de video. Una posible solución para de cualquier modo poder ver los videos es correr vlc del siguiente modo:

```
vlc --vout x11
```

De cualquier manera, esperemos a ver que pasa una vez compilado el driver

[0] [http://forums.fedoraforum.org/showthread.php?t=104445]("http://forums.fedoraforum.org/showthread.php?t=104445")

aaa con eso los reproduce con pocos fps pero por lo menos andan!! gracias por el dato!

sigo viendo como compilar xq soy bastante noob

pd: segun estube leyendo esto le pasa a casi todos q usan linux y placa on board intel

---

### Post by pablo.s on 2009-08-14
En [este post]("http://ubuntuforums.org/showpost.php?p=7517680&postcount=1") se habla
de tu problema.

---

### Post by josecuervo86 on 2009-08-14
Depende que placa, yo tenia (en realidad tengo) una intel que realmente se comporto como una señorita, hasta que me compre una nVidia, aunque hay sobrados threads sobre las placas intel y su bajo desempeño. Esperemos que una vez compilado el driver este problema se solucione.

---

### Post by EnriqueK on 2009-08-14
Tu problena no es de drivers por que de ser así, ni siquiera tendrías entorno gráfico, estimo que lo que falta es instalar el pack de codecs 

1.- Habilita los repositorios de Medivuntu  
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
2.- Luego instala el metapaquete **non-free-codecs**

---

### Post by viper3k on 2009-08-14
> **EnriqueK said:**
> Tu problena no es de drivers por que de ser así, ni siquiera tendrías entorno gráfico, estimo que lo que falta es instalar el pack de codecs 

1.- Habilita los repositorios de Medivuntu  
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
2.- Luego instala el metapaquete **non-free-codecs**

gracias por la respuesta 
pero me surgio otro problema cuando intento instalarlo luego de agregar el repositorio me aparece esto

```

E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿está otro proceso usándolo?

```

alguna idea? 

Gracias a todos por el tiempo , se aprecia mucho

---

### Post by rafaelca on 2009-08-15
Pues no sé pero ahora que me acuerdo hablaban en un blog de las placas INTEL en 'ubuntu'.

En la nueva versión creo que habian problemas o algo así.

Igualmente intentare ayudarte buscando por la red :D

---

### Post by Hei Ku on 2009-08-15
> **viper3k said:**
> gracias por la respuesta 
pero me surgio otro problema cuando intento instalarlo luego de agregar el repositorio me aparece esto

```

E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿está otro proceso usándolo?

```

alguna idea? 

Gracias a todos por el tiempo , se aprecia mucho

Si, que tenes otro programa de instalacion de paquetes abierto, Cerralo.

---

### Post by viper3k on 2009-08-15
trantado de compilar driver aca

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

me dice que tengo q bajar 4 cosas y me imagino q ponerlas en una misma carpeta para compilarlas? 

y dice que se bajan del git repository

"git ://...."

hmm como hago eso ? :X

---

### Post by Hei Ku on 2009-08-15
git clone <direccion>

Tenes que instalar git antes, con sudo apt-get install git

No hay instrucciones mas detalladas?

---

