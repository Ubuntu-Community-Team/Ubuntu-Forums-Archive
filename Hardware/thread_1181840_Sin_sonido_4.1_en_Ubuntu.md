---
title: "Sin sonido 4.1 en Ubuntu"
date: 2009-06-08
forum: Hardware
---

### Post by gasto40 on 2009-06-08
Bueno, me pase finalmente a Ubuntu. El tema es que no tengo sonido 4.1 en mis parlantes. Solo puedo escuchar los dos parlantes frontales, mientras que en los parlantes traseros y el subwoofer, no se escucha nada.

Ya me fije que estuvieran todos los canales con volumen, e incluso hice eso de editar el archivo daemon.conf, y poner que se escuchara en 5 canales, pero no hay caso..

El chip de audio de mi maquina es el de la placa madre Gigabyte P35C-DS3R, el Realtek ALC889A, y por lo que he visto, no se ha podido hacer funcionar en Ubuntu aun...


Alguno tiene alguna idea de que puedo hacer?
Gracias

---

### Post by pablo.s on 2009-06-08
¿Como tenes conectados los
parlantes a la tarjeta de
sonido? Directos, salida
optica o mediante amplificador?

---

### Post by gasto40 on 2009-06-08
Los tengo conectados directamente. Un cable verde, conectado a la fichita verde de la placa madre, y un cable negro, conectado a la fichita negra de la placa madre.

No creo que sea problema de conexion de cables, ya que hasta hace 1 dia, que era cuando tenia Windows XP, el sonido funcionaba 100% sin problemas.

---

### Post by pablo.s on 2009-06-08
Fijate en el mezclador
que hay mas canales para
habilitar, como Front,
Center, Side, etc, etc.

---

### Post by josecuervo86 on 2009-06-08
Estuve buscando en Google y hay un problemita con esa placa de sonido para linux por falta de drivers apropiados. 
Probaste bajando la última version del driver de ALSA? Parece que corrigieron el driver para que use el Path de 883 que supuestamente anda con 889

[http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18]("http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18")

---

### Post by gasto40 on 2009-06-08
Ya me fije. Como dije en mi primer post, me he fijado que todos los canales esten habilitados, y con volumen. Me fije en alsamixer, y todo parece estar bien.

---

### Post by gasto40 on 2009-06-08
> **josecuervo86 said:**
> Estuve buscando en Google y hay un problemita con esa placa de sonido para linux por falta de drivers apropiados. 
Probaste bajando la última version del driver de ALSA? Parece que corrigieron el driver para que use el Path de 883 que supuestamente anda con 889

[http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18](http://www.alsa-project.org/main/index.php/Changes_v1.0.17_v1.0.18)

mmm, el tema es que no se bien que es lo que tengo que bajar de esa pagina, y esas cosas como compilar y eso, no entiendo muy bien aun como hacerlo!

---

### Post by josecuervo86 on 2009-06-08
Aca [0] te dejo la direccion del ultimo driver. Una vez que lo descargues, lo descomprimis y en el archivo que dice install te da los pasos para compilar. Como regla general siempre son 3:

```
./configure
make
make install
```

[0] [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")

---

### Post by staar on 2009-06-08
acá: [http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/]("http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/") hay un tutorial detallado para compilar la última version de alsa, solo seguí los comandos de a uno, y chiflá si tenés algún problema...

saludos

---

### Post by gasto40 on 2009-06-08
edit: Bueno, me fijo ahi y cualquier cosa les digo. Gracias!!

---

### Post by gasto40 on 2009-06-08
No hubo caso :(

Pude compilar e instalar los drivers de Alsa, pero todo sigue igual. Aca les muestro como tengo configurado todo en alsamixer. [http://i41.tinypic.com/33l2o02.jpg](http://i41.tinypic.com/33l2o02.jpg)

---

### Post by josecuervo86 on 2009-06-08
> **gasto40 said:**
> No hubo caso :(

Pude compilar e instalar los drivers de Alsa, pero todo sigue igual. Aca les muestro como tengo configurado todo en alsamixer. [http://i41.tinypic.com/33l2o02.jpg](http://i41.tinypic.com/33l2o02.jpg)

Hace una cosa, apreta con el botn derecho del mouse sobre el parlante del panel. Anda a donde dice **Abrir el control de volumen** y una vez ahi anda a preferencias y marca todas las opciones. Proba subiendole el sonido a todos o con diferentes conbinaciones y fijate si cambia algo

---

### Post by gasto40 on 2009-06-08
SI. Acabo de probar y nada todavia. No se que mas hacer

edit: De todos modos, me habia fijado, y tenia los drivers de Alsa 1.0.18, por lo tanto, los problemas con el chip alc889a supuestamente ya deberian haber estado solucionado para esa version

---

### Post by gasto40 on 2009-06-08
Si alguno tiene alguna otra idea, se lo voy a agradecer!

---

### Post by sebastianabate on 2009-06-08
Mirá, justo el otro día buscaba lo mismo que vos y encontré la solución en los foros de Ubuntu-es; pero la verdad que no guardé el link y ahora no lo encuentro. Te paso lo que hice yo y fijate si te sirve:

Para mi placa (una ALC883) hay que agregar al archivo /etc/modprobe.d/alsa-base.conf la línea

```
options snd-hda-intel model=3stack-6ch

```que habilita 6 canales usando los tres conectores miniplug que tiene mi mother. Hay muchas variables para la línea model= pero los únicos que me acuerdo ahora son

```
3stack
3stack-6ch
3stack-dig
6stack-dig
6stack

```Después tenés que elejir ALSA en todas las opciones de System->Preferences->Sound
Reiniciás la máquina, le das click al ícono del parlante al lado del reloj, y click a "Volume Control". click en Options y allí elejís la configuración de parlantes que querés usar (en tu caso 4ch)

Para testear podés usar desde consola el comando

```
speaker-test -Dplug:surround51 -c4 -l1 -twav
```que hace sonar en cada parlante su configuración (front right, front left, rear right, etc)

Googleá un poco algunas de estas palabras clave y seguro que encontrás el mensaje de donde saqué la data, que estaba muy completo y tenía todas las opciones de modules= para cada modelo de placa. Voy a seguir buscando, y si lo encuentro lo posteo para futuras búsquedas.

PD: Puse los nombres de las entradas del menú y otras cosas en inglés porque así tengo mi Ubuntu. Si alguien puede poner las mismas opciones como aparecen en un Ubuntu en castellano sería ideal. No quise traducir "a ojo" para no confundir.

Edit: Obviamente voy a encontrar el link unos minutos después de postear. Acá está el mensaje del foro Ubuntu-es con el listado largo de opciones para cada placa/modelo:
[http://www.ubuntu-es.org/?q=node/103227](http://www.ubuntu-es.org/?q=node/103227)
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by gasto40 on 2009-06-09
Gracias Sebastian!!!!!

Segui los pasos que me dijiste, y ahora lo tengo andando! Gracias!!! 

edit: Y gracias a todos tambien por las demas sugerencias :)

---

