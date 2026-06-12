---
title: "High definition problema NVIDIA"
date: 2008-12-20
forum: Hardware
---

### Post by katon on 2008-12-20
hola gente que tal , queria consultarles al reproducir peliculas en alta definicion por ejemplo archivos MKV de los que andan por la red (series de television)  no se ve muy bien , a que me refiero "hay unas lineas" al pasar los frames rapidamente.
He leido que NVIDIA estan trabajando en los drivers BETA para aceleracion por hardware (lo que en windows seria PUREVIDEO ahora en linux. 

Mi pregunta es como se llama en INGLES esto de las lineas que aparecen mas que nada en escenas de accion rapidas.

Por otro lado mi PC es Quad core Q6600 tendria que probar de configurar el MPLAYER que utilze todos los procesadores ? como se haria esto? o el problema es de todas maneras de la placa de video?

---

### Post by katon on 2008-12-20
olvidaba decir gracias !

---

### Post by KrossX on 2008-12-20
Puedes ver este video correctamente con otros reproductores ( u otro OS ) ?

Quizá el video fue grabado como entrelazado (scanlines), o quizá no se le aplicó un buen filtro para desentrelazar cuando se re-encodeó. Prueba utilizar un filtro de desentrelazado en el reproductor, si ya hay uno seleccionado... prueba con uno distinto.

---

### Post by katon on 2008-12-20
he probado con otros ....pasa lo mismo..

---

### Post by KrossX on 2008-12-20
Con otros?... Otros reproductores, otros Sistemas Operativos, otros filtros de desentrelazado?

---

### Post by katon on 2008-12-20
he probado en Windows Vista funcionan correctamente las high definition...
otros programas en ubuntu el VLC.

---

### Post by KrossX on 2008-12-20
Bien! Si funciona bien en algún lugar... significa que el video o está bien (entrelazado y no mal encodeado) o el filtro usado es muy agresivo. XD

Bajo Vista, qué codec usa? Y qué método de desentrelazado usa?

Esos datos te pueden server a la hora de elejir el filtro de desentrelazado en mplayer y VLC.

---

### Post by katon on 2008-12-21
Gracias por las respuestas krossx, lo que entiendo de leer en muchas paginas es que linux no soportaba hasta ahora PUREVIDEO osea reproducir high definition, osea que no importa con cual programa lo hagas ...
vos podes ver bien estos videos?
[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1)

---

### Post by KrossX on 2008-12-21
[COLOR="Navy"]Te puedo decir que bajo Windows puede ver videos HD sin problemas (Media Player Classic Home Cinema, sin DXVA), y sin necesidad de PUREVIDEO.
No he probado videos HD en Linux que hayan estado entrelazados.

PUREVIDEO simplemente permite la decodificación via hardware, lo cual también aplica filtros automáticos como desentrelazado y corrección de gamma. Esto, sin cargar el CPU.

Como dije, debes probar con filtros de desentrelazado y las líneas no se deberían notar.[/COLOR]

---

### Post by katon on 2008-12-22
gracias nuevamente, 
lo que no entiendo es donde me fijo el entrelazado? en cada archivo que video que abro con Mplayer? 
y como podria agregar esos filtros?

gracias

---

### Post by KrossX on 2008-12-22
[color="Navy"]Si por MPlayer te refieres al Totem.... entonces no.

De lo contrario, si usas SMPlayer (GUI para MPlayer) tienes en Preferencias => General => Video; y ahí encontrarás opciones de desentrelazado.

**man mplayer** si no usas un GUI y verás todas las opciones que tiene.[/color]

---

### Post by katon on 2009-01-18
ahi estoy usando el Mplayer pero no se que opciones deberia tocar.
las lineas siguen estando....ojo no son muchas, solo en escenas de accion y rapidez de movimiento.

---

### Post by rvm4000 on 2009-01-18
Pues por ejemplo:
```
mplayer -vf yadif video
```

yadif da muy buena calidad pero también consume bastante CPU. Si eso es un problema podrías probar -vf pp=l5 en su lugar.

Si usas smplayer, tienes varios filtros de desentrelazado en el menú vídeo.

---

### Post by katon on 2009-01-18
no che,,,lo mejorsito que anda es sin ninguna opcion de esas...
que raro...ustedes ven perfecto las peliculas ?

---

