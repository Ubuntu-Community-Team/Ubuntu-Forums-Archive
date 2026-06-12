---
title: "No funciona microfono integrado en portátil C751LA"
date: 2009-06-22
forum: Hardware
---

### Post by dnovai on 2009-06-22
Hola amigos!
Como puedo configurar correctamente el microfono integrado de mi portátil (c751la)?
Alguna idea o sugerencia?

Saludos!

---

### Post by josecardenasvejar on 2009-06-22
Hola! dirígete a Aplicaciones - sonido y video - control de volumen ( si no lo tienes ahí puedes agregarlo desde sistema - preferencias - menú principal y seleccionas sonido y lo agregas).

una vez que estás en control de volumen, fíjate que esté como predeterminado el HDA Nvidia (Alsa Mixer) en mi caso.


Click en preferencias y asegúrate que esté habilitado el dock mic
Una vez que lo hayas hecho tienes que cerciorarte que no esté muteado.


Cuéntame que pasa
:D

---

### Post by dnovai on 2009-06-22
Hola gracias por tu respuesta.
Hice lo que me dijiste y efectivamente el "mic internal" esta habilitado con el dispositivo HDA Intel (Alsa mixer).

El problema esta cuando quiero utilizarlo, por ejemplo con una aplicación sencilla como el grabador de sonidos, se cuelga el programa.

Alguna otra idea o sugerencia?

Agradezco tu paciencia.
Saludos!

---

### Post by josecardenasvejar on 2009-06-23
Usas la versión 8.10 de ubuntu? has pensado en actualizar a 9.04?

reinstala alsa mixer en la consola 
sudo apt-get install alsamixer

Saludos

---

