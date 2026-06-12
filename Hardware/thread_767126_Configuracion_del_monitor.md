---
title: "Configuracion del monitor"
date: 2008-04-25
forum: Hardware
---

### Post by benzema on 2008-04-25
Bueno tengo un monitor medio viejito que ubuntu me lo detecta como plug and play,hasta la version pasada podia ir a sistema/administracion/pantalla y graficos creo que era pero en esta nueva version ya no esta ,recuerdo que ponia otros monitores y estaba el mio "aoc 4v no se cuanto" pero ahora no se como ponerlo,alguna idea, aa no comente el problema cual es que no puedo usar resolucion mayor a 800x600 y yo normalmente uso 1024x768 eso espero sus respuestas Muchas Gracias

---

### Post by undiaperfecto on 2008-04-25
si ya instalaste el driver de tu placa de video, lo que tenes que hacer es instalar nvidia-settings, esta en synaptic
despues lo ejecutas con nvidia-settings desde un terminal, y ahi, en la pestaña X SERVER DISPLAY CONFIGURATION seleccionas la resolucion que quieras.
cualquier cosa preguntá

---

### Post by benzema on 2008-04-26
mira instale el nvidia-setting,cambie la resolucion y todo pero cuando pongo
"save to x configuration file" que supongo que es el que hace que los cambios hechos queden para siempre me sale esto:(imagen)

[IMG]http://img178.imageshack.us/img178/6610/pantallazoia1.png[/IMG]


capaz que pongo mal donde se guarda o algo,yo lo dejo por defecto...

[IMG]http://img294.imageshack.us/img294/1557/pantallazo1yv2.png[/IMG]

---

### Post by InsektO on 2008-04-26
> **benzema said:**
> mira instale el nvidia-setting,cambie la resolucion y todo pero cuando pongo
"save to x configuration file" que supongo que es el que hace que los cambios hechos queden para siempre me sale esto:(imagen)

capaz que pongo mal donde se guarda o algo,yo lo dejo por defecto...



No. Pasa que para que pueda guardar los cambios, debés correrlo así:

```
sudo nvidia-settings
```

Con eso te va a guardar sin ningún tipo de problema.

Saludos!

---

### Post by undiaperfecto on 2008-04-26
a mi me anduvo sin el sudo, pero proba asi.
y cuando hice el cambio, le hice click en Apply, no en save to...
despues puse salir y se cambio de toque.
igualmente con sudo te tiene que si o si salvar

---

### Post by Flechagorda on 2008-04-27
Me pasa exactamente lo mismo...
La resolucion mas grande es 1024*768, pero estoy acostumbrado a 1280*960.

Con sudo nvidia settings, puedo cambiar sin problemas la resolucion, me deja guardar y todo bien, pero cada vez que reinicio la maquina o las X, se me vuelve a la resolucion anterior.....

Alguna idea?

---

### Post by benzema on 2008-04-27
Muchas Gracias con el sudo adelante me funciono lo mas bien

---

### Post by srmantis on 2008-04-29
Existe otra opcion y es la de modificar Pantallas y graficos, claro que en hardy no aparece en el menu, asi que hay que ir:
comando para ejecutar pantallas y graficos
gksu displayconfig-gtk

o ir a la carpeta /usr/share/applications y hacer doble click sobre pantallas y graficos.

Ahora solo deben configurar su monitor y tarjeta de video. Despues de reiniciar apareceran otras resoluciones en resoluciones de pantalla.

---

### Post by FlyerDie on 2008-06-19
Perdon que reviva este thread, pero lo hago para no abrir otro con un tema similar.

Yo tengo un AOC 7E-BLK (17" de carcaza negra).

Ahora bien, tambien me aparece como Plug&Play... con el nvidia-settings (tengo placa nvidia) me va a aparecer dentro del listado de monitores? ya que como a benzema, mi monitor "desaparecio" del listado de una version a otra :confused:

Pregunto esto tambien porque no es solo un tema de resolucion, sino tambien de refresh, ya que lo tengo a 60hz y la verdad que me produce mareos al estar a tan bajo ciclos, necesito ponerlo minimo a 70hz y asi no me molesta.

Gracias por la respuesta ;)

---

### Post by FlyerDie on 2008-06-19
Bueno, recien llegue a casa y lo hice atravez del nvidia-settings
Anduvo de maravillas :)
Gracias!

---

