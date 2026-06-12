---
title: "Ubuntu no inicia en modo Live"
date: 2009-06-29
forum: Hardware
---

### Post by atari130xe on 2009-06-29
Hola gente, intento instalar Ubuntu 9.04 o la 8.10 (dual boot con XP) a una amiga y resulta que ni siquiera puedo iniciar en modo Live cd, llega a la parte de la gráfica y "muere" ahí, le instalé una nueva placa una Gforce 6200 256MB y en XP funciona perfecto pero cuando intento iniciar Ubuntu al llegar a la parte de inicio de las X simplemente s:confused:e detiene el CD y queda así. Elegí con F4 el modo grafico seguro pero tampoco inicia, alguien tiene una idea de que puede ser?
gracias!

PD en el apuro postee en cualquier lado mil disculpas, a moverlo sr moderador a la sección Hardware.

---

### Post by guillermolisi on 2009-06-29
> **atari130xe said:**
> Hola gente, intento instalar Ubuntu 9.04 o la 8.10 (dual boot con XP) a una amiga y resulta que ni siquiera puedo iniciar en modo Live cd, llega a la parte de la gráfica y "muere" ahí, le instalé una nueva placa una Gforce 6200 256MB y en XP funciona perfecto pero cuando intento iniciar Ubuntu al llegar a la parte de inicio de las X simplemente s:confused:e detiene el CD y queda así. Elegí con F4 el modo grafico seguro pero tampoco inicia, alguien tiene una idea de que puede ser?
gracias!
Probaste de ir a una consola con CTRL+ALT+F1 ?
Que motherboard es ?
Hiciste la comprobacion de integridad del CD ?

---

### Post by atari130xe on 2009-06-29
> **guillermolisi said:**
> Probaste de ir a una consola con CTRL+ALT+F1 ?
Que motherboard es ?
Hiciste la comprobacion de integridad del CD ?

Es un Asrock 775i65G de una CPU generica de la marca Tonomac.

El CD es orginal de Shipit es el que usé en varias PC´s y funciona perfecto.

---

### Post by atari130xe on 2009-06-30
Alguna idea?

---

### Post by pablo.s on 2009-06-30
Se me ocurre que instales
con el Alternate CD.
Ventajas: Te va a permitir
instalar.
Desventajas: Es probable
que debas descargarlo, no
es nada vistoso en 
comparación con el LiveCD.

---

### Post by guillermolisi on 2009-06-30
Insisto, probaste de ir a una consola con CTRL+ALT+F1 ?

Cuanta RAM tiene la maquina ?
Para menos de 384Mb apoyo la sugerencia de Pablo S.

---

### Post by atari130xe on 2009-06-30
Guillermo no me dice nada que me haga dar cuenta de que se trata el problema, solo que si hago un dmesg sale algo asi como X server fatal error, o sea como que no inicia el servidor de X. La tarjeta es una XFX Geforce 6200 AGP 8X 256MB estoy Googleando como loco, le hablé tanto de Ubuntu a esta amiga que cuando vio que estuve 2 horas sin siquiera poder iniciar el servidor grafico me quedé onda loquito jejeje
Nunca de las docenas de veces que instalé Ubuntu en las diferentes versiones, me pasó esto, que ni siquiera arranque el live CD, ella compro una de esas Tonomac que vienen con partes de baja calidad, entre ellos el chip intel integrado con casi 0 memoria, compramos esa placa (la Geforce 6200 AGP X8) que erá lo unico disponible en ese momento y se la instalé, antes con el chip integrado, arrancaba y se veia muy mal pero arrancaba bien, luego le instalé la placa nueva y en XP (la idea era eliminarle XP por los virus que siempre la vuelven loca) y dejarle solo Ubuntu 9.04 (probé con 8.10 y tampoco arrancó), asi que bueno supongo que es algo de la gráfica.

---

### Post by atari130xe on 2009-06-30
> **guillermolisi said:**
> Insisto, probaste de ir a una consola con CTRL+ALT+F1 ?

Cuanta RAM tiene la maquina ?
Para menos de 384Mb apoyo la sugerencia de Pablo S.

Tiene 1GB de RAM que se la instale yo el año pasado. (tenia 256)

---

### Post by guillermolisi on 2009-06-30
Mi insistencia con lo de la consola era particularmente por este comentario tuyo:
> resulta que ni siquiera puedo iniciar en modo Live cd, llega a la parte de la gráfica y "muere" ahí
Ahora que parece que tenes acceso a las consolas, podrias mostrar el contenido de /var/log/Xorg.0.log ?

Deshabilitaste el video on-board o te aseguraste de que se deshabilite cuando incorporaste la 6200 ?

---

### Post by atari130xe on 2009-06-30
> **guillermolisi said:**
> Mi insistencia con lo de la consola era particularmente por este comentario tuyo:

Ahora que parece que tenes acceso a las consolas, podrias mostrar el contenido de /var/log/Xorg.0.log ?

Deshabilitaste el video on-board o te aseguraste de que se deshabilite cuando incorporaste la 6200 ?


No estoy en la PC de mi amiga esta a 30 mins de mi casa pero en cuanto pueda posteo la info que me pedis,. lo que si me volvi loco es para saber como se deshabilita el video on board que el manual no lo dice. supongo que al insertar la placa se deshabilita la onboard automaticante como en otros mothers... sino alguien que me ilumine un poco, no conozco ese mother.

---

### Post by staar on 2009-06-30
en la mayoría de las mothers, cuando se pone una placa, la onboard se desativa sola, aunque Asrock es una caja de sorpresas, nunca se sabe las cosas a las que puede llegar con esa marca...

pregunta, con la onboard sola, arrancan las X?

saludos

---

### Post by atari130xe on 2009-07-01
> **staar said:**
> en la mayoría de las mothers, cuando se pone una placa, la onboard se desativa sola, aunque Asrock es una caja de sorpresas, nunca se sabe las cosas a las que puede llegar con esa marca...

pregunta, con la onboard sola, arrancan las X?

saludos

Si arrancan las X con la onboard (Me permito una groseria: la marca sería ASSrock) :lolflag:

---

### Post by guillermolisi on 2009-07-01
> **atari130xe said:**
> Si arrancan las X con la onboard (Me permito una groseria: la marca sería ASSrock) :lolflag:
Haria la siguiente comprobacion:
Con la placa 6200 instalada y con el monitor conectado en ella iniciaria la PC.

Cuando quede la pantalla negra, cambiar el monitor de placa conectandolo a la placa on board. 

Si vuelvo a tener video (grafico) entonces el problema es que la on board sigue activa y mete conflicto con la 6200 (o no detecta como activa a la 6200, cosa que se podria verificar en consola leyendo la salida del lspci, lshw, etc.)

---

### Post by staar on 2009-07-01
bueno, en todo caso, arrancando con la nvidia, posteate el contenido del archivo /var/log/Xorg.0.log, como lo vas a tener que hacer por consola en un livecd, primero vas a tener que montar algún disco o un pendrive donde copiarlo, y después con un ```
 cat /var/log/Xorg.0.log > */disco/montado/archivo.txt*
``` todo esto para que podamos darnos una idea de porqué corno no levantan las X...

saludos

---

### Post by atari130xe on 2009-09-16
> **staar said:**
> bueno, en todo caso, arrancando con la nvidia, posteate el contenido del archivo /var/log/Xorg.0.log, como lo vas a tener que hacer por consola en un livecd, primero vas a tener que montar algún disco o un pendrive donde copiarlo, y después con un ```
 cat /var/log/Xorg.0.log > */disco/montado/archivo.txt*
``` todo esto para que podamos darnos una idea de porqué corno no levantan las X...

saludos

Bueno luego de meses, vuelvo a ir a la casa de mi amiga porque me pide a gritos que le instale Ubuntu (no podia por el trabajo y la facultad) asi que espero tener suerte y poder encontrar el problema, voy a seguir sus consejos, me llevo un pen drive y veremos que onda, ayer me dijo: Jose venite el Jueves porque ya me harté de Windows XP se me llena de Virus con antivirus y todo y me deja de funcionar la computadora, así que vereé que me sale de todo esto... cualquier cosa re posteo...

---

### Post by atari130xe on 2010-01-04
Bueno empecé bién el año y cerrando este viejo post que quedó truncado porque había "resuelto" el problema instalando Ubuntu 9.04 mediante Wubi pero sin aceleración 3D. Mi amiga me llamó este sabado diciendo que habia echo una actualización de sistema y que no le arrancó más la PC, cuando fuí habia echo el upgrade de la 9.04 a la 9.10 pero como tenia ese grave problema con la gráfica no levantó mas el escritorio.
Llevé discos de la 9.10, de Mandriva 2010 (Ninguno funcionó, se "colgaron" con pitidos continuos) y de Linux Mint 9.10 que finalmente terminé instalando porque funcionó muy bién en modo live con la opcion "Modo compatibilidad" que tiene el Live cd, eliminé la particion de XP hice las nuevas particiones de / y /home y le instale Linux Mint con Compiz activado y funcionando a la perfección, resultado mi amiga feliz y yo tranquilo, se acostumbro desde Junio hasta ahora a usar Ubuntu y aprendió bastante y ahora tiene solo Linux. Gracias a todos!

---

