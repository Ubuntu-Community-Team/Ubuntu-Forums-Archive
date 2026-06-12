---
title: "Consulta Realtek alc888 7.1 High Definition"
date: 2007-04-13
forum: Hardware
---

### Post by Gideon26 on 2007-04-13
Hola a toda la gente linuxera bueno mi consulta si alguien logro hacer andar el sonido integrado que tiene la motherboard Asrock AM2NF6G, el chipset es Realtek alc888 7.1 High Definition. Si alguien lo pudo hacer andar puede explicarme ya que intente con el paquete que se puede bajar en Realtek que por lo que pude ver es de alsa pero no me funciono para nada. bueno saludos espero respuesta.

---

### Post by Gideon26 on 2007-04-14
Hola Bueno queria avisar que pude resolver lo del audio tengo mi audio funcionando en 7.1 de lujo. Bueno ahora les explico que fue lo que hice.

1 baje estos archivos 

alsa-driver-1.0.14rc3.tar.bz2
alsa-lib-1.0.14rc3.tar.bz2
alsa-utils-1.0.14rc2.tar.bz2

2 cree el directorio alsa en /usr/src/

sudo mkdir -p /usr/src/alsa

3 Luego copie todos los archivos que baje a /usr/src/alsa/

sudo cp /home/nombrede usurio mio/Desktop/alsa* 

4 procedi a descomprimir los archivos 

sudo tar xjf alsa-driver-1.0.14rc3.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc3.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc2.tar.bz2

5 prepare para poder copilar los drivers

sudo apt-get install linux-headers-`uname -r` build-essential ncurses-dev

6 procedi a copilar e intalar los archivos
cd alsa-driver-1.0.14rc3
sudo ./configure
sudo make
sudo make install

cd alsa-lib-1.0.14rc3
sudo ,/configure
sudo make
sudo make install

cd alsa-utils-1.0.14rc2
sudo ./configure
sudo make
sudo make install


7. sudo reboot

y cuando volvi a iniciar quedo funcionando el audio de diez. 

saludos espero que les sirva

---

### Post by kowal on 2007-04-14
Gracias totales por postear la solución y no dejar el post inconcluso, asi le sirve a otro que venga buscando algo para el mismo problema.

Saludos!

---

### Post by Gideon26 on 2007-04-15
Hola pues de nada, un placer ayudar y contribuir aparte creo que postear soluciones a problemas concuerda con la filosofia de software libre.




Saludos :popcorn:

---

### Post by Darth Trix on 2007-06-09
Tengo la misma placa de sonido, probé con tu guía y no me anduvo.
No me tira ningún error ni nada, el alsamixer carga perfecto, pero sigo sin tener audio.

Alguna otra idea?

---

### Post by Gideon26 on 2007-06-10
Entra a Alsa [http://www.alsa-project.org/](http://www.alsa-project.org/) y bajate los ultimos  que son rc4 copilando esos deberian andarte, 
con ubuntu feisty que es el que tengo ahora puesto no tengo problemas con el sonido, es mas ni tuve que bajar de nuevo las cosas en alsa directamente instale fresh y anduvo sin hacer nada. proba de ultima con feisty (fresh) que seguramente va a hacer funcionar tu alc888. Saludos

---

### Post by octaedro7 on 2007-07-24
Gideon26, dices que te Funciona el audio, pero has logrado grabar desde un microfono o línea?
Te lo pregunto ya que a mi el audio se escucho a penas instalado Feisty, sin embargo, hasta el día de hoy, 3 meses despues der mi primera instalación de Ubuntu, luego de haber pasado por Kubuntu y actualmente Ubuntu Studio, luego de compilar los ultimos alsa y todo, aún no puedo grabar audio ni usar skype.  Es muy raro por que se puede oir el microfono (monitoreo) pero no lo graba.
Ojalá puedas ver este post y contestarlo, si tu tienes el audio 100% operativo, será una luz de esperanza.

---

### Post by MeduZa on 2007-07-24
> **octaedro7 said:**
> Gideon26, dices que te Funciona el audio, pero has logrado grabar desde un microfono o línea?
Te lo pregunto ya que a mi el audio se escucho a penas instalado Feisty, sin embargo, hasta el día de hoy, 3 meses despues der mi primera instalación de Ubuntu, luego de haber pasado por Kubuntu y actualmente Ubuntu Studio, luego de compilar los ultimos alsa y todo, aún no puedo grabar audio ni usar skype.  Es muy raro por que se puede oir el microfono (monitoreo) pero no lo graba.
Ojalá puedas ver este post y contestarlo, si tu tienes el audio 100% operativo, será una luz de esperanza.

tenes que ir a la configuracion de auido (doble click en el volumen) y en la parte de grabacion abilitar de donde queres que grabe
a mi me paso en un soft que tenia como entrada la salida de linea y los demas escuchaban los que salia por los parlantes en vez de escuchar lo que entraba por el mic

---

### Post by Gideon26 on 2007-07-24
Hola mira yo tengo el audio 100% operativo asi que lo mas probable es lo que te decia meduza que tengas que configurar en el alsa mixer como tiene la entrada de el microfono para que no lo tome solamente como monitoreo
Saludos!

---

### Post by octaedro7 on 2007-07-25
estas en lo correcto.  En las opciones de grabación, tenía puesto capture->mic y capture1->line.  Cambié los dos a mic y ahora funciona.  Voy a seguir probando a ver si me funciona la captura de linea.  Una última pregunta, ¿tienes alguna opción de darle 20db al mic?
En mi laptop con sonido AC-97 tengo Ubuntu studio y en las opciones del mixer me aparece una casilla para habilitar este boost que en mi desktop no me aparece.

Muxas gracias

---

### Post by Adicted on 2007-09-15
realmente muchas pero muchas gracias, estube días y días luchando para ver que le pasaba a mi sonido, y caise vos desde ele cielo xD =) muuuuuuchisimas gracias

---

### Post by Darth Trix on 2007-10-21
Acabo de instalar Gutsy y tuve otra vez problemas con la maldita placa de sonido. 
Lo que pasa es que por alguna razón Ubuntu viene sin alsaconf además tampoco podía compilar alsa-utils (donde viene alsaconf), así que lo que hice fue compilar alsa-driver y alsa-lib y después bajarme el paquete alsa-utils de los repositorios de Debian:

[http://packages.debian.org/sid/alsa-utils]("http://packages.debian.org/sid/alsa-utils")

Y así si poder ejecutar alsaconf.

---

### Post by Catalonian on 2008-07-19
Hola!
Estoy intentando hacer funcionar el dichoso alc888..he intentado hacer lo que dijiste pero me encuentro con esto cuando intento hacer el make de los alsa-utils:

Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17rc2/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17rc2/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17rc2/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17rc2/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsaconf/po'
mv: ha fallat stat() sobre «t-ja.gmo»: No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17rc2/alsaconf'
make: *** [all-recursive] Error 1

Esos ultimos errores no me dejan continuar. No he tenido ningun problema con los otros dos (driver y lib). He bajado los tres de [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Qué estoy haciendo mal?! gracias :D

---

### Post by Bhiexito on 2008-08-30
Gracias Gideon26, no podia hacer andar el audio del Ubuntu 8.04 y con tu consego sobre Alsa, volví a la vida, ya etsba pensando en reinstalar todo.

Ci vediamo
Bhiexito:D

---

