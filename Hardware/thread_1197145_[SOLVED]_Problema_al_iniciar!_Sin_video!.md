---
title: "[SOLVED] Problema al iniciar! Sin video!"
date: 2009-06-25
forum: Hardware
---

### Post by tinoq3 on 2009-06-25
Gente, acabo de iniciar la pc en ubuntu y no tengo video. Pareciera que se me hubiese j****o la placa, pero no. Por lo visto el sistema inicia porque escucho el sonido luego de escribir el usuario y contraseña (a ciegas obviamente).

Inicie en modo recovery, ejecute una especie de video fixer pero nada. Alguna idea de como proceder???

Gracias de antemano. Saludos.

---

### Post by Fernando Gonzalo Pellico on 2009-06-25
Si puedes iniciar en modo recovery, no es un problema de Hardware, sino de software. Presumo que del driver. Si es así, necesito más datos: ¿cual es tu tarjeta gráfica? ¿qué hiciste si antes te funcionaba y ahora no?. Si es una Nvidia o Ati y usas los drivers propietarios, puedes bajártelos y pulsar control + alt + F1 al iniciar y desde ahí instalarlos.

Pero vamos, esa eso sólo una idea, necesito saber más. Lo más importante es ¿qué has podido tocar que haya hecho esto?

Un saludo y ya verás como lo solucionamos.

---

### Post by tinoq3 on 2009-06-25
Si, la placa funciona porque accedo a win.
Uso una ATI 4670 con drivers propietarios.
Lo último que recuerdo es un update del sistema. Había cosas de compiz, la verdad que no me acuerdo que decía exactamente.

Pruebo lo que me decís y te cuento.
Mil gracias!

---

### Post by guillermolisi on 2009-06-25
> **tinoq3 said:**
> Si, la placa funciona porque accedo a win.
Uso una ATI 4670 con drivers propietarios.
Lo último que recuerdo es un update del sistema. Había cosas de compiz, la verdad que no me acuerdo que decía exactamente.

Pruebo lo que me decís y te cuento.
Mil gracias!
Proba de instalar los drivers abieetos en lugar de los propietarios.

PS: Lo muevo a hardware porque esta relacionado con los drivers de un componente de la maquina, la placa de video.

---

### Post by Hei Ku on 2009-06-25
Los drivers abiertos no andan con esta placa. Proba reinstalando los drivers.

---

### Post by guillermolisi on 2009-06-25
> **Hei Ku said:**
> Los drivers abiertos no andan con esta placa. Proba reinstalando los drivers.
Que mareo !

Hay algun modelo de ATI que funcione con los abiertos y otros con los propietarios ?
(se nota que uso nVidia ?) :D

---

### Post by Hei Ku on 2009-06-25
Las HD, chipset R600 y R700, solo funcionan bien con los propietarios. El libre solo puede hacer modesetting, pero nada de aceleracion, por ahora.

El libre anda bien para los modelos viejos, modelos 9200, 9600, etc.

Es así, estan en medio de una transicion y se hace dificil.

Asi que en este caso, lo mejor seria intentar reinstalar el driver.

Podes probar con: aticonfig --initial -f

---

### Post by tinoq3 on 2009-06-27
Pude solucionarlo, inicie en recovery mode y de ahí a modo consola. Por suerte había bajado los drivers 9.6 de ATI y los instale desde ahí. Inicie y todo perfecto.

La combinación Ctrl+Alt+F1 no me funcionó, o al menos no pasaba nada...

Muchas gracias!

---

