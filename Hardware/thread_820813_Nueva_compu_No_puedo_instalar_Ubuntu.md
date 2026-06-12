---
title: "Nueva compu No puedo instalar Ubuntu"
date: 2008-06-06
forum: Hardware
---

### Post by fedeavila on 2008-06-06
Buenas gente! Tengo un problemon...

Hoy hace aproximadamente 2 horas me trajeron mi nueva pc...

Estoy tratando de instalar Ubuntu 7.10 con el live cd que me vino a casa pero cuando termina de cargarse el SO me aparece el mismo cartelito de siempre...

OUT OF RANGE

Se escucha el sonido de cuando se inicia Ubuntu... Todo... Pero la pantalla se pone negra! 

Estoy segurisimo de lo que es...

Es el monitor patetico que tengo de 15'' Philips

Porque me compre solamente la compu... Una amd 4200 blabla

y viene onboard una GeForce6100PM-M2

y creo que la resolucion con la que se inicia es mayor a lo que mi monitor puede aguantar (1024*768)

Y el problema mayor es que sé como modificarlo... Pero al ponerse la pantalla en negro no puedo ver nada!

Con Windows XP no tuve problemas... Pero con Ubuntu como es el live cd no tengo otra forma de instalarlo salvo que encuentre alguna forma de "decirle" que se ejectute en una resolucion mas baja...

Intente ponerlo en modo normal y no puedo.
Intente ponerlo en modo graficos seguro, y tampoco puedo, me pasa lo mismo.

La verdad que no se que hacer... Supongo que con el Alternate CD podria hacerlo pero no tengo ni CD virgen ni ganas de descargarlo juaz

:(

Si alguien puede ayudarme se lo agradecere de por vida (o hasta que me compre un monitor como la gente jaja)

***GRACIAS***

---

### Post by Mister X on 2008-06-06
> **fedeavila said:**
> 
Y el problema mayor es que sé como modificarlo... Pero al ponerse la pantalla en negro no puedo ver nada!


Si apretas ctrl+alt+F1 cuando termina de cargar, pasás a la consola?

---

### Post by guillermolisi on 2008-06-06
El out of range aparece cuando alguno de los parametros de funcionamiento del monitor estan fuera de rango. Estos parametros son la frecuencia vertical y la horizontal y para saber que valores limites deben utilizarse hay que recurrir al manual (sea impreso o electronico) del monitor.

Claro que si alguien esta usando un monitor de la misma marca y modelo que el tuyo la cosa se facilita ya que puede pasarte como tiene configurados estos valores en el archivo /etc/X11/xorg.conf.

---

### Post by clasificado on 2008-06-06
> salvo que encuentre alguna forma de "decirle" que se ejectute en una resolucion mas baja...

Hasta GG habia una opción de "Resolucion" en el boot del CD. ¿No está ahi?

> **fedeavila said:**
> Supongo que con el Alternate CD podria hacerlo pero no tengo ni CD virgen ni ganas de descargarlo juaz

Si, con el alternate podrás.

clasificado

---

### Post by fedeavila on 2008-06-06
> **Mister X said:**
> Si apretas ctrl+alt+F1 cuando termina de cargar, pasás a la consola?
ehh?? y que se supone que tengo que hacer despues?? :S

yo se hacerlo como lo dijo el otro chico  con "etc/X11/xorg.conf"

pero eso es para cuando ya lo tenes instalado...

realmente no se que quisiste decir con lo de la consola...

lo hice pero... y ahora?

:S

gracias igual

---

### Post by fedeavila on 2008-06-06
> **clasificado said:**
> Hasta GG habia una opción de "Resolucion" en el boot del CD. ¿No está ahi?



Si, con el alternate podrás.

clasificado
no, la opcion que aparece en el menu con se inicia con el cd es apretando F6 y te aparece un menu con las distintas resoluciones (VGA, 640*320, 800*600, 1024*768) ya lo elegi desde ahi pero parece que no da bola...

ya ni ganas de instalarmelo igual (N)

---

### Post by matutetandil on 2008-06-06
para configurarlo, desde la conla (apretando Crtl+Alt+F1 ) te logueas como usuario, y luego escribis sudo dpkg-reconfigure xserver-xorg y seguis el asistente..

Saludos!!!!

---

### Post by faktorqm on 2008-06-06
3 cosas para hacer:

1) Arranca normalmente, cuando escuches el sonidito significa que teoricamente tenes la pantalla de login mostrandose, entonces como no ves nada, apreta directamente "CTRL + ALT + +" y eso te cambia la resolucion. Si seguis sin ver nada, volvelo a apretar. Despues agarra y empeza a apretar "CTRL + ALT + -" para volver hacia atras hasta que te muestre algo. Si no te muestra nada....

2) Arranca con el live cd, monta la particion de la instalacion, edita el archivo /etc/X11/xorg.conf y busca en la seccion Display que aparezca algo asi (si no esta ingresalo vos)

```
SubSection "Display"
        Modes        "1024x768" 
        Virtual      1024 768
    EndSubSection
```

y en la seccion monitor

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30.0 - 50.0
        VertRefresh     50.0 - 90.0
        Option         "DPMS"
EndSection
```

y ahi tendrias que ver algo. Si esto no va....

3) Bajate el alternate CD de 8.04 32 bits y reinstala.

Espero que te haya servido. Salu2!

---

### Post by Mister X on 2008-06-06
> **fedeavila said:**
> ehh?? y que se supone que tengo que hacer despues?? :S

yo se hacerlo como lo dijo el otro chico  con "etc/X11/xorg.conf"

pero eso es para cuando ya lo tenes instalado...

realmente no se que quisiste decir con lo de la consola...

lo hice pero... y ahora?

:S

gracias igual

Te lo dije porque desde la consola podes hacer absolutamente TODO, por mas que no esté instalado, en memoria crea un sistema de archivos virtual con la misma estructura que el disco.
Como vos pusiste "Y el problema mayor es que SE como modificarlo... Pero al ponerse la pantalla en negro no puedo ver nada!"...
Igualmente ya despues te dijeron que hacer

saludos

---

### Post by fedeavila on 2008-06-06
> **faktorqm said:**
> 3 cosas para hacer:

1) Arranca normalmente, cuando escuches el sonidito significa que teoricamente tenes la pantalla de login mostrandose, entonces como no ves nada, apreta directamente "CTRL + ALT + +" y eso te cambia la resolucion. Si seguis sin ver nada, volvelo a apretar. Despues agarra y empeza a apretar "CTRL + ALT + -" para volver hacia atras hasta que te muestre algo. Si no te muestra nada....

2) Arranca con el live cd, monta la particion de la instalacion, edita el archivo /etc/X11/xorg.conf y busca en la seccion Display que aparezca algo asi (si no esta ingresalo vos)

```
SubSection "Display"
        Modes        "1024x768" 
        Virtual      1024 768
    EndSubSection
```

y en la seccion monitor

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30.0 - 50.0
        VertRefresh     50.0 - 90.0
        Option         "DPMS"
EndSection
```

y ahi tendrias que ver algo. Si esto no va....

3) Bajate el alternate CD de 8.04 32 bits y reinstala.

Espero que te haya servido. Salu2!
Mil gracias!

Fue re simple... Puse Ctrl+Alt+ "+/-" y lo fui cambiando hasta llegar a 1024*768

Era un ***** :P

---

### Post by niko_3100 on 2008-06-08
Con ese micro y esa placa de video no tendria que darte mayores problemas ubuntu, anda de 10 con esa configuracion. La mother es la ecs 6100-m2 o algo asi? esa que esta super barata?

---

### Post by fedeavila on 2008-06-08
> **niko_3100 said:**
> Con ese micro y esa placa de video no tendria que darte mayores problemas ubuntu, anda de 10 con esa configuracion. La mother es la ecs 6100-m2 o algo asi? esa que esta super barata?

no sé... es una que me recomendaron por acá que me compre x?

---

