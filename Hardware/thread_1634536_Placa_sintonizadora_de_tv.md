---
title: "Placa sintonizadora de tv"
date: 2010-11-30
forum: Hardware
---

### Post by synyster696 on 2010-11-30
Hola gente! soy nuevo por aca... y vengo a traer un problema que tengo

me compre una placa sintonizacora encore enltv fm3 y no puedo ver tv... osea busque por ahi algunos pasos los segui pero nada... no me sintoniza y no me deja cambiar la norma.. para hacerlo tengo que desinstalar el programa e instalarlo otra vez pero no cambia nada

siempre queda en "default" y no puedo cambiar de canal ni nada


alguno sabe que puedo hacer? en la caja dice que soporta linux con kernel v2.6.18 o mas alto... y yo uso ubuntu 10.04

espero respuesta! gracias por adelantado un saludo!

---

### Post by Applelnx on 2010-12-02
Hola Synyster, probaste el siguiente instructivo? Fijate que en las respuestas al mismo articulo muchas veces se encuentran errores o diferencias.

[http://xoloescuintle.wordpress.com/2010/11/10/instalar-tarjeta-de-tv-encore-enltv-fm3/](http://xoloescuintle.wordpress.com/2010/11/10/instalar-tarjeta-de-tv-encore-enltv-fm3/)

Contanos bien que es lo que haces y que paso.
Saludos

---

### Post by synyster696 on 2010-12-10
Seguí todos los pasos de ahi y fue un poco mejor... ahora puedo elegir canales y no dice mas default sino television.... pero se me queda en una pantalla azul y en el medio dice Sin señal

que podría ser?

---

### Post by Applelnx on 2010-12-11
> **synyster696 said:**
> Seguí todos los pasos de ahi y fue un poco mejor... ahora puedo elegir canales y no dice mas default sino television.... pero se me queda en una pantalla azul y en el medio dice Sin señal

que podría ser?

Primero, asegurate que tengas la norma PAL-Nc que se usa en Argentina.

Si eso no funciona, fijate que en los comentarios hay un par de cambios que aplicaron algunas personas, quizas te puedan ayudar.

---

### Post by Don King on 2010-12-11
Tengo el mismo problema. 

Me parece que el problema radica en que los numeros de card y tuner en el saa7134 varian segun el pais. Habria que ver cuales corresponden a argentina.

---

### Post by mama21mama on 2010-12-11
aquí tengo mi[ guía]("http://mamalibre.text0.tk/?q=content/tv-tuner-pro-enltv-fm-con-chip-saa71304") que funca.

```
sudo gedit /etc/modprobe.d/options

```
y se se abrira el editor...
poner en la ultima linea
```
options saa7134 card=3 tuner=37 i2c_scan=1 ir_debug=1
```
Luego Reiniciar

---

