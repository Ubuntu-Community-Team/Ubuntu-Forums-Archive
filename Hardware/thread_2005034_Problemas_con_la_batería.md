---
title: "Problemas con la batería"
date: 2012-06-16
forum: Hardware
---

### Post by aledruetta on 2012-06-16
Hola Comunidad!

En las últimas versiones de Ubuntu tengo problemas con la batería de la notebook (tres notebooks diferentes). El problema se ha ido agravando con cada nueva versión. Una batería que antes duraba 2 horas y media, ahora dura menos de 1 hora. El indicador de carga parece completamente loco; ahora lo estoy mirando, está con la carga al 100%, es sólo desconectar el cargador que baja a 29%, lo conecto nuevamente y vuelve al 100%. Eso es un ejemplo, pero en realidad no da para entender, en cinco minutos pasa de una autonomía de, no sé, 40 minutos a una de 13 minutos; matemáticamente no me da la resta...

Alguien tiene alguna sugerencia para darme?

Gracias!

---

### Post by gmunioz on 2012-06-19
Prueba el applet jupiter

sudo su
add-apt-repository ppa:webupd8team/jupiter
apt-get update
apt-get install jupiter

---

### Post by dirty fingers on 2012-06-20
Quizas el problema y la solución viene por el tema que hablan acá
[http://www.muylinux.com/2012/02/09/kernel-3-2-5-aspm-solucion-portatiles-linux/](http://www.muylinux.com/2012/02/09/kernel-3-2-5-aspm-solucion-portatiles-linux/)

---

### Post by aledruetta on 2012-06-21
> **gmunioz said:**
> Prueba el applet jupiter

sudo su
add-apt-repository ppa:webupd8team/jupiter
apt-get update
apt-get install jupiter

Ya lo estoy usando, supongo que sin el applet sería peor, pero igual la duración de la batería es demasiado baja.

---

### Post by aledruetta on 2012-06-21
> **dirty fingers said:**
> Quizas el problema y la solución viene por el tema que hablan acá
[http://www.muylinux.com/2012/02/09/kernel-3-2-5-aspm-solucion-portatiles-linux/](http://www.muylinux.com/2012/02/09/kernel-3-2-5-aspm-solucion-portatiles-linux/)

Bueno, ojalá que se solucione en algún problema. Es algo demasiado importante como para que siga en ese estado.

---

### Post by mustafa1990 on 2013-01-08
Hola aledruetta, ya solucionaste el problema de la bateria? yo tengo que mismo problema con una hp portatil. Es la misma locura que describes tu con la bateria.

---

### Post by aledruetta on 2013-01-14
> **mustafa1990 said:**
> Hola aledruetta, ya solucionaste el problema de la bateria? yo tengo que mismo problema con una hp portatil. Es la misma locura que describes tu con la bateria.

No, mustafa, no lo resolví. Creo que la batería caducó... Tal vez haya sido un defecto de fábrica, pero de todas formas creo que las últimas versiones de Ubuntu no ayudaron con las baterías de las notebooks que pasaron por mis manos...

---

### Post by asterix77 on 2013-01-17
Para saber es estado de una bateria, en una terminal se debe escribir lo siguiente:


  $cat /proc/acpi/battery/BAT0/info


 En mi caso el resultado fue el siguiente:
 [INDENT]$  cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      2408 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 120 mAh
design capacity low:     84 mAh
capacity granularity 1:  36 mAh
capacity granularity 2:  2288 mAh
model number:            Primary
serial number:           
battery type:            LION
OEM info:                Hewlett-Packard
 [/INDENT] Lo interesante son las lineas:
 design capacity:         4400 mAh
last full capacity:      2320 mAh


La primera  línea es el valor de fábrica y la segunda es la capacidad actual. La diferencia es la capacidad que ha perdido nuestra batería.

---

### Post by aledruetta on 2013-01-18
Gracias Asterix por el código!

La mía está al 25%. Yo ya leí en algún lado que Ubuntu estropeaba las baterías de las notebook. No sé si será cierto o es un bulo de las comunidades "rivales", pero la verdad es que hace unas tres o cuatro versiones que tengo problemas con la batería. Y, en el caso de mi actual notebook, la batería estaba liquidada al año de comprar la máquina... me di cuenta justo después de vencer la garantía...

Saludos!

---

### Post by hectorivand on 2013-01-23
Siempre tuve bardo con la batería en Ubuntu, no importa la versión pero por mi lado viene por la gestión de energía de la Toshiba que con Linux no se llevan para nada bien, de hecho, mi maquina calienta que da miedo!

Salud!
Nacho

---

