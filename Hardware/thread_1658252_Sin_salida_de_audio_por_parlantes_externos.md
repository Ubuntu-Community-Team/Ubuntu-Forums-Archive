---
title: "Sin salida de audio por parlantes externos"
date: 2011-01-02
forum: Hardware
---

### Post by mano negra on 2011-01-02
Buenas 
Les escribo porque no logro la salida de audio por medio de parlantes externos. Les paso la info de lo que tengo:
- notebook Dell Inspiron N5010, procesador intel i5 con audio y video integrado.
- Por lo que vi la tarjeta de sonido es STAC92XX Analog.
- los parlantes son edifier con una potencia.

Les cuento que probé de todo. Editar el archivo /etc/modprobe.d/alsa-base.conf, cambiando y/o agregando en la última línea instrucciones varias; ver en alsamixer la configuración; instalar paprefs y pavucontrol creyendo que por ahí configuraba algo del pulseaudio, pero me parecía redundante; probar distintas opciones en gstreamer-propierties. Nada. Solo me funcionan los parlantes internos.
TAmbién cambié la opción de "analog speaker" a "analog headfhone" y "analog output". Nada.

Saludos.

---

### Post by mano negra on 2011-01-02
Buenas,
  Pude solucionarlo. Aquí les paso lo que hice:
1- con "aplay -l" verifico el modelo de la placa de sonido.
2- se abre como root el archivo alsa-base.conf
3- en la última línea se agraga "options snd-hda-intel model=XXXX". En XXXX se completa de acuerdo al modelo de este listado [www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt). En mi caso para una Dell con chip STAC92XX se completa con "ref"
4- se reinicia alsa con "sudo alsa force-reload".

Por el momento si no hay nada enchufado, funcionan los parlantes internos. Sino los externos que se enchufen.

Salud!
PD: no se como se indica cuando está solucionado[COLOR=Black][COLOR=#CC9933][/COLOR][/COLOR]

---

