---
title: "[SOLVED] problemas para capturar el sonido con un Inspiron 1545"
date: 2009-08-07
forum: Hardware
---

### Post by donmatas on 2009-08-07
Holanda ubunteros:

tengo un Dell Inspiron 1545 con Jaunty (9.04) pero no puedo capturar sonido.  Modifiqué el alsa-base.conf del modo que señala este foro pero no me funcionó ([http://ubuntuforums.org/showthread.php?t=1222371](http://ubuntuforums.org/showthread.php?t=1222371)). Lo necesito porque trabajo con skype.

Además el volumen del equipo está muy bajo aunqeu lo ponga a toda potencia

antes usaba 8.04 y funcionaba el sonido perfecto, pero tenía problemas al suspender el equipo y aveces se quedaba pegado.

agradezco orientación

salud
M

---

### Post by josecuervo86 on 2009-08-07
proba poniendo 
```
alsamixer
```
en una terminal y fijate si en **capture** no esta silenciado. Ademas proba subiendo las que estan en **playback** (para ver si sube el volumen)

---

### Post by donmatas on 2009-08-07
gracias compa por la respuesta
el problema es que nunca había visto eso de un programa incrustado en la terminal. No puedo hacer nada más que subir y bajar el volumen en el master (con la rueda del ratón) y lo mismo con el mic tras presionar tab.

le ajunto pantallazos del asunto a ver si me puede seguir horientando

saludos
DM

---

### Post by josecuervo86 on 2009-08-07
Te doy las configuraciones del teclado:

```
**[TAB]**: para pasar de Playback > Capture > All
**[Flechas Izq y Der]**: Para moverte entre todas las opciones de cada seccion [los cosos verdes y rojos :P]
**[Flechas Arriba y abajo]**: Para subir y bajar el volumen de cada uno
```

Espero que haya quedado claro, sino decime ;)

Fijate que en Capture tenes, valga la redundancia, Capture en 0,0 trata de subir ese y fijate que pasa

---

### Post by donmatas on 2009-08-08
gracias compa. 
he podido subir el volumen de captura en el alsamixer sin problemas gracias a sus indicaciones. luego reinicié, verifiqué que el alsamixer estuviera como lo dejé e intenté capturar sonido con el programita de grabación que viene por defecto, pero el problema continúa. Le adjunto como quedó el alsamixer y el el control de volumen, que persiste porfiadamente en quedar en mute (si le saco el mute, vuelve a aparecer muteado)

---

### Post by josecuervo86 on 2009-08-08
En el control de volumen (2da foto) intenta meterte en donde dice preferencias y elegí otra opción para la grabación de sonidos. A mi me paso que lo tenia en la opción **micrófono** y la correcta era **line in**

---

### Post by donmatas on 2009-08-12
Gracias compa:

habilité todas y las entradas de "grabación" pero continua el problema de que quedan en "mute" pese a que intente lo contrario (adjunto pantallazo). Parece claro que el problema es el driver de la tarjeta de audio Intel Corporation 82801I (ICH9 Family) HD Audio Controller

alguna sugerencia?

salud
M

---

### Post by luks911 on 2009-08-12
> **donmatas said:**
> Gracias compa:

habilité todas y las entradas de "grabación" pero continua el problema de que quedan en "mute" pese a que intente lo contrario (adjunto pantallazo). Parece claro que el problema es el driver de la tarjeta de audio Intel Corporation 82801I (ICH9 Family) HD Audio Controller

alguna sugerencia?

salud
M

¿Probaste cambiando las opciones de captura en gstreamer-properties? Ejecutá
```
gstreamer-properties
``` en una terminal y fijate.

---

### Post by donmatas on 2009-08-12
nuevamente gracias
probé todas las combinaciones posibles y sigue todo igual. En todo caso cambié y probé sin reiniciar ¿crees que sería necesario?

adjunto foto de como estaba originalmente el gstreamer-properties

saludos
M

---

### Post by luks911 on 2009-08-12
> **donmatas said:**
> nuevamente gracias
probé todas las combinaciones posibles y sigue todo igual. En todo caso cambié y probé sin reiniciar ¿crees que sería necesario?

adjunto foto de como estaba originalmente el gstreamer-properties

saludos
M

Mmmm... no hace falta que reinicies. ¿Estás probando con un micrófono externo, verdad? Tengo la misma máquina, pero hace muy poco y todavía no traté de usar esa funcionalidad. Mañana voy a probar a ver si logro algo.

---

### Post by donmatas on 2009-08-12
sips, es un micrófono externo que está bueno, pues funciona ocn ubuntu 8.04 en esta misma máquina. (no te recomiendo hardy, pues se queda pegado de cuando en cuando y al suspenderlo se deshabilitan los puertos usb)

Ojalá tengas novedades con el Mic

salud
M

---

### Post by luks911 on 2009-08-13
Bien, parece que tengo buenas noticias. Después de probar varias opciones logré capturar sonido desde la entrada del micrófono. Lo que hay que hacer:
1) Ejecutas gstreamer-properties y en el apartado de "Entrada predeterminada" pones para "Complemento": ALSA, y "Dispositivo", Predeterminado.
2) Vas al applet de control de volumen, le das un click izquierdo y luego al botón "Control de volumen" para acceder a las distintas opciones de audio. Allí en "Dispositivo" pones "HDA Intel (Alsa mixer)" y haces click en el botón "Preferencias" que hay abajo en el cuadro de diálogo. Vas a tener un nuevo cuadro de diálogo de "Preferencias de control de volumen". Ahí busca la opción "Digital Input Source" y tilda su casilla. Al hacerlo en el cuadro diálogo previo (Preferencias) va a aparecer una nueva pestaña con el título "Opciones", vas a ella y en el desplegable (hay uno solo) eliges "Analog Inputs"(Si aquí, en cambio, seleccionas "Digital Mic 1", entonces se habilita la captura por medio del micrófono incorporado, el que viene con la cámara web). Y listo. Hice la prueba con un mic externo y gstreamer-properties, y funcionó.
El volumen de la captura puedes manejarlo en la pestaña Grabación con el deslizable Capturar.
Espero que sirva.
Algo más: no le hice ninguna modificación a mi alsa-base.conf respecto de como quedó tras la instalación, así que tal vez debas volver a atrás las que hayas hecho. Y uso Ubuntu 9.04 actualizado.

---

### Post by donmatas on 2009-08-14
Compañero:

¡asunto solucionado maestro! Probé además skype y funcionó perfecto con las siguientes preferencias en opciones/dispositivos de sonido: 
Sonido Entrante: hda intel (hw:intel0)
Sonido Saliente:  pulse
Llamada entrante: pulse

Le agradezco muchísimo su dedicación desinteresada para ayudarme a resolver este problema. Realmente es conmovedor saber que podemos hacer las cosas simplemente por amor a hacerlas y no movidos por el lucro. 

¡otro mundo es posible!

¡Linux o Barbarie!

pd: mi laptop no tiene cámara ni mic integrado... ¿raro no?

---

### Post by luks911 on 2009-08-14
> **donmatas said:**
> Compañero:

¡asunto solucionado maestro! Probé además skype y funcionó perfecto con las siguientes preferencias en opciones/dispositivos de sonido: 
Sonido Entrante: hda intel (hw:intel0)
Sonido Saliente:  pulse
Llamada entrante: pulse

Le agradezco muchísimo su dedicación desinteresada para ayudarme a resolver este problema. Realmente es conmovedor saber que podemos hacer las cosas simplemente por amor a hacerlas y no movidos por el lucro. 

¡otro mundo es posible!



¡Linux o Barbarie!

pd: mi laptop no tiene cámara ni mic integrado... ¿raro no?

No hay de qué :) Me alegro de que haya servido.
Lo de la cámara depende del modelo. De hecho hay Inspiron 1545 con diferencias de procesador, memoria, disco, etc.

---

### Post by donmatas on 2009-08-14
otra cosa, no te parece que sale muy despacio el sonido?

salud
DM

---

### Post by luks911 on 2009-08-14
> **donmatas said:**
> otra cosa, no te parece que sale muy despacio el sonido?

salud
DM

Sí, es cierto. Creo que por debajo del 60% del volumen o tal vez más deja de escucharse. La captura iba bien subiendo el volumen del micrófono y de la salida. 
Pero sí, es bastante bajo el sonido. 
Tal vez mejore con Karmic. En mi máquina anterior, una Compaq, al instalarle 8.04 se escuchaba por los parlantes y por los auriculares a la vez. Con 8.10 ya los parlantes se silenciaban al enchufar los auriculares.

---

### Post by donmatas on 2009-08-14
> **luks911 said:**
> Sí, es cierto. Creo que por debajo del 60% del volumen o tal vez más deja de escucharse. La captura iba bien subiendo el volumen del micrófono y de la salida. 
Pero sí, es bastante bajo el sonido. 
Tal vez mejore con Karmic. En mi máquina anterior, una Compaq, al instalarle 8.04 se escuchaba por los parlantes y por los auriculares a la vez. Con 8.10 ya los parlantes se silenciaban al enchufar los auriculares.

Lo que describes es exactamente lo que me pasa a mi. Igual, con la captura habilitada me doy por pagado...

salud y aguante
DM

---

### Post by donmatas on 2009-11-03
compa:

actualicé a Karmic Koala y se resolvió el problema del volumen pero ahora no capturo sonido. te mando pantallazos del alsamixer.

saludos
DM

---

### Post by luks911 on 2009-11-03
> **donmatas said:**
> compa:

actualicé a Karmic Koala y se resolvió el problema del volumen pero ahora no capturo sonido. te mando pantallazos del alsamixer.

saludos
DM

También hice la actualización y mejoró el volumen. La captura todavía no la probé, pero sí vi que en las preferencias de sonido hay varios perfiles, es probable que haya que tocar algo ahí.
Supongo que mañana podré fijarme. Si logro algo, escribo.

Saludos

PD: vi el PM

---

### Post by luks911 on 2009-11-05
Otra vez, perdón por la demora.
Esta vez me costó bastante más encontrar la combinación correcta, uf.
En gstreamer-properties tiene que quedar tanto Salida (Default Output) como Entrada (Default Input) en PulsaAudio Sound Sevrver, la opción Plugin, y en Predeterminado, la opción Device.
Luego, vas al ícono del parlante, donde manejas el volumen, das click derecho y seleccionas Preferencias de Sonido. En la pestaña Hardware tienes un menú desplegable que dice Perfil, ahí seleccionas Analog Stereo Duplex. Luego vas a la pestaña Entrada. Ahí te fijas que abajo de todo, en "Elegir un dispositivo para la entrada de sonido", quede marcada la única opicón que hay. Más arriba hay un menú desplegable de Conector: ahí la opción Microphone 1 es para el mic externo que conectas a la notebook t Microphone 2 para el mic que viene incluido al lado de la webcam. Y, claro, el control de más arriba es para manejar el volumen de la entrada.
Y eso es todo. Probé los dos micrófonos con el test de gstreamer-properties y funcionaron bastante bien. Si le subis el volumen de la captura puede llegar a saturar un poco, pero eso revisalo a ver qué te parece.
Espero que sirva.
Saludos

---

### Post by donmatas on 2009-11-05
> **luks911 said:**
> Otra vez, perdón por la demora.
Esta vez me costó bastante más encontrar la combinación correcta, uf.
En gstreamer-properties tiene que quedar tanto Salida (Default Output) como Entrada (Default Input) en PulsaAudio Sound Sevrver, la opción Plugin, y en Predeterminado, la opción Device.
Luego, vas al ícono del parlante, donde manejas el volumen, das click derecho y seleccionas Preferencias de Sonido. En la pestaña Hardware tienes un menú desplegable que dice Perfil, ahí seleccionas Analog Stereo Duplex. Luego vas a la pestaña Entrada. Ahí te fijas que abajo de todo, en "Elegir un dispositivo para la entrada de sonido", quede marcada la única opicón que hay. Más arriba hay un menú desplegable de Conector: ahí la opción Microphone 1 es para el mic externo que conectas a la notebook t Microphone 2 para el mic que viene incluido al lado de la webcam. Y, claro, el control de más arriba es para manejar el volumen de la entrada.
Y eso es todo. Probé los dos micrófonos con el test de gstreamer-properties y funcionaron bastante bien. Si le subis el volumen de la captura puede llegar a saturar un poco, pero eso revisalo a ver qué te parece.
Espero que sirva.
Saludos

compadre:

como siempre, te pasaste. El fin de semana instalaré limpiamente 9.10 (no recomiendo el upgrade, a mi me dio puros problemas), probaré la solución y reportaré los resutlados

salud
DM

---

### Post by donmatas on 2009-11-08
> **donmatas said:**
> compadre:

como siempre, te pasaste. El fin de semana instalaré limpiamente 9.10 (no recomiendo el upgrade, a mi me dio puros problemas), probaré la solución y reportaré los resutlados

salud
DM

Compa:

probé la solución en modo "live cd" y no me funcionó. Más tarde lo instalaré y veré qué pasa, pero me gustaría saber algo antes. Dices que probaste el mic con el test de gstreamer-properties, pero ¿probaste grabar algo con el grabador de sonido que viene instalado por defecto o con otro programa?

salud
DM

---

### Post by luks911 on 2009-11-08
No sé si habrá diferencia entre el modo Live e Instalado. De todos modos, acabo de probar grabar con un micrófono externo en el Grabador de Sonidos, y funcionó.
Cualquier cosa me avisas.

---

### Post by donmatas on 2009-11-08
> **luks911 said:**
> No sé si habrá diferencia entre el modo Live e Instalado. De todos modos, acabo de probar grabar con un micrófono externo en el Grabador de Sonidos, y funcionó.
Cualquier cosa me avisas.

gracias compa. haré unas cuestiones pendientes y luego intentaré la instalación y le cuento como me fue

salud
M

---

### Post by guillermolisi on 2009-11-08
Recien lei en la lista de soporte de Ubuntu-ar que alguien soluciono su problema de sonido en una notebook HP 530 siguiendo las recomendaciones que se dan en:

[http://tecnotravel.com.ar/2009/11/02/solucionar-problemas-de-sonido-en-ubuntu-9-10-karmic-koala/](http://tecnotravel.com.ar/2009/11/02/solucionar-problemas-de-sonido-en-ubuntu-9-10-karmic-koala/)

Basicamente habria que instalar Alsa desde el repositorio de backports (linux-backports-modules-alsa-karmic-generic). Luego se reinicia y listo.

---

### Post by donmatas on 2009-11-08
> **guillermolisi said:**
> Recien lei en la lista de soporte de Ubuntu-ar que alguien soluciono su problema de sonido en una notebook HP 530 siguiendo las recomendaciones que se dan en:

[http://tecnotravel.com.ar/2009/11/02/solucionar-problemas-de-sonido-en-ubuntu-9-10-karmic-koala/](http://tecnotravel.com.ar/2009/11/02/solucionar-problemas-de-sonido-en-ubuntu-9-10-karmic-koala/)

Basicamente habria que instalar Alsa desde el repositorio de backports (linux-backports-modules-alsa-karmic-generic). Luego se reinicia y listo.

gracias compa!
hice lo que señaló luca911 y luego instalé los backports y reinicié y funcionó!!!

salud
DM

---

