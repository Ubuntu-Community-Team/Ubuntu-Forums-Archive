---
title: "Realteck AC'97 drivers en ubuntu x64"
date: 2008-05-23
forum: Hardware
---

### Post by Barasuishou on 2008-05-23
hola bueno como dice el titulo existen esos drivers, por que en la web de realteck hay unos drivers para linux pero ninguno que diga ubuntu o debian, y menos x64, alguien me puede ayudar???,

---

### Post by UBUjuan on 2008-05-25
Yo tengo esa placa y linux me la reconoció y configuró bien no tuve que tocar nada. ¿qué problemas con el sonido tenés? , por ahí es otra cosa.

---

### Post by Barasuishou on 2008-05-25
a mi me la reconocio, pero yo tengo un parlante que es "parte" del monitor y otro que es un 2.1 conectado a la pc, pero solo tengo sonido por el que es del monitor, los otros nada, no suenan, ya sea en juegos, o cuando escucho musica

---

### Post by UBUjuan on 2008-05-25
Si los parlantes del monitor funcionan entonces no es problema de la placa de sonido (o de ubuntu).
si tenes windows ¿te sucede lo mismo? En la mayoría de las PC's la placa de sonido es integrada y tiene una sola salida para los parlantes, otra para el microfono y otra mas que no recuerdo para que es, en las que tiene 6 entradas es para parlantes con subwoofers que tienen varios "satelites" se usa para sonido 3d (o sea podes tener un solo "juego de parlantes".

---

### Post by faktorqm on 2008-05-25
Revisa los volumenes de cada salida. Salu2!

---

### Post by Barasuishou on 2008-05-26
bueno mira el volumen ya lo revise, y paso a contar los parlantes estan "conectados" al monitor, y el monitor a la cpu pero no tiene como algunos monitores un cable aparte que es de los parlantes, en cambio en la ficha de la cpu de los parlantes tengo conetado el 2.1, en windows en casi, aclaro casi todo me sale audio por todos los parlantes, cuando escucho musica no importa el programa siempre sale el audio por todos, pero cuando abro un vid en youtube solo me sale audio por el parlante del monitor, y en algunos juegos (ej: counter strike) casi no sale audio por los 2.1, sale mas que nada por el parlante del monitor, por eso cuando quize probar si estaba bien el audio puse musica y no youtube, si no son los drivers supongo que me debe tomar el parlante del monitor como un juego y el 2.1 como otro y no ambos como uno solo :S, nose, ahora cuando yo hago doble click sobre el parlantito en la barra de arriba, y pongo cambiar dispositivo esta puesto nvidia(algo mas no me acuerdo), y cuando entro por medio de sistema preferencia sonido, tampoco en ningun lugar está puesto realteck, esto puede tener que ver o no tiene nada que ver???(ya probe de cambiarlo y o no anda, o en caso del parlante de la barra si lo cambio me pone volumens para grabar y no para reproducir) :S

---

### Post by ariel on 2008-05-27
> **Barasuishou said:**
> bueno mira el volumen ya lo revise, y paso a contar los parlantes estan "conectados" al monitor, y el monitor a la cpu pero no tiene como algunos monitores un cable aparte que es de los parlantes, en cambio en la ficha de la cpu de los parlantes tengo conetado el 2.1, en windows en casi, aclaro casi todo me sale audio por todos los parlantes, cuando escucho musica no importa el programa siempre sale el audio por todos, pero cuando abro un vid en youtube solo me sale audio por el parlante del monitor, y en algunos juegos (ej: counter strike) casi no sale audio por los 2.1, sale mas que nada por el parlante del monitor, por eso cuando quize probar si estaba bien el audio puse musica y no youtube, si no son los drivers supongo que me debe tomar el parlante del monitor como un juego y el 2.1 como otro y no ambos como uno solo :S, nose, ahora cuando yo hago doble click sobre el parlantito en la barra de arriba, y pongo cambiar dispositivo esta puesto nvidia(algo mas no me acuerdo), y cuando entro por medio de sistema preferencia sonido, tampoco en ningun lugar está puesto realteck, esto puede tener que ver o no tiene nada que ver???(ya probe de cambiarlo y o no anda, o en caso del parlante de la barra si lo cambio me pone volumens para grabar y no para reproducir) :S

no veo que menciones que version de linux estas usando, y si estas usando pulseaudio o no.

Si usas 8.04 con los defaults, googlea "/etc/pulse/default.pa", y pavucontrol y padevchooser.

---

### Post by Barasuishou on 2008-05-28
si estoy con ubuntu 8.04 hardy heron x64(instalación wubi), por lo demas disculpa pero hace 2 semanas que tengo el ubuntu y no entendí bien lo del pulseaudio y lo que sige del pavucontrol y padevchooser, por lo que se es algo que se ve en terminal no?, pero realmente nose como lo "veo" :S,

---

