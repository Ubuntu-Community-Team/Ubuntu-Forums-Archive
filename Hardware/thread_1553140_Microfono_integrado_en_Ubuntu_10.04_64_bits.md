---
title: "Microfono integrado en Ubuntu 10.04 64 bits"
date: 2010-08-14
forum: Hardware
---

### Post by Applelnx on 2010-08-14
Hola, tengo el siguiente problema. No me funciona el microfono integrado de mi notebook, con Ubuntu 10.04 64 bits. Tengo una HP Pavilion dv4-1225dx. El sonido me funciona bien, tanto de parlantes como de auriculares. El microfono que se conecta tambien funciona. El que no funciona es el integrado. El modelo de la tarjeta es HDA ATI SB, Chip IDT 92HD71B7X.

La verdad es que busque por todas partes solucion para el problema pero no la encontre. Probe editando la configuracion de alsa (/etc/modprobe.d/alsa-base.conf), con diferentes modelos, siguiendo este manual [http://www.ubuntu-es.org/node/115147](http://www.ubuntu-es.org/node/115147), pero sin resultados positivos.

Si alguien me puede ayudar, le agradeceria mucho. 
Dejo una captura de pantalla de alsa mixer, por si les sirve:

[ATTACH]166453[/ATTACH]

Si necesitan algun otro dato, no duden en consultarme.
Saludos

---

### Post by josecuervo86 on 2010-09-12
Applelnx, probaste en el editor de sonido con otra entrada que no sea **Microfono**? te digo, en mi caso tuve que probar un par de opciones antes de encontrar la correcta. Otra opción es fijarte ejecutando

```
gstreamer-properties
``` cambiando las opciones de entrada

---

### Post by Applelnx on 2010-09-13
> **josecuervo86 said:**
> Applelnx, probaste en el editor de sonido con otra entrada que no sea **Microfono**? te digo, en mi caso tuve que probar un par de opciones antes de encontrar la correcta. Otra opción es fijarte ejecutando

```
gstreamer-properties
``` cambiando las opciones de entrada

Hola josecuervo86, mi salida para el comando gstreamer-properties es la siguiente:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
```

Igualmente me abre la ventana donde puedo elegir el complemento y dispositivo. Probe rapidamente un par de combinaciones, pero ninguno funciona. Despues cuando tengas mas tiempo me fijo mejor. Muchas gracias!

---

### Post by Applelnx on 2010-12-04
Bueno, aparentemente di con la solucion. Reinstale ALSA y PULSEAUDIO (a costa de perder el indicador de volumen integrado al de Rhythmbox).

Una vez hecho esto, edite el archivo **/etc/modprobe.d/alsa-base.conf** agregando la siguiente linea:

```
options snd-hda-intel model=dell-m4-1
```

Por ultimo, reinici ALSA:

```
killall pulseaudio
sudo alsa force-reload
pulseaudio -D

```
Por si a alguno le sirve...
Saludos

---

