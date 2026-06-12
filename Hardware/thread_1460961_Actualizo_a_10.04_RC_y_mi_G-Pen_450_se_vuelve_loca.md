---
title: "Actualizo a 10.04 RC y mi G-Pen 450 se vuelve loca"
date: 2010-04-23
forum: Hardware
---

### Post by Leelogarduk on 2010-04-23
¡Hola a todos! En primer lugar, quiero disculparme si éste no es el  lugar adecuado para este post, dado que también me considero bastante  novato en esto... Si es así, ruego a los moderadores que me disculpen y  muevan el post al lugar que le corresponda.
 Mi problema surge cuando, al actualizar mediante "update-manager -d"  desde un 9.10 al actual (a fecha de hoy) 10.04 RC, mi tableta  digitalizadora Genius G-Pen 450 pierde la compostura y empieza a hacer  básicamente lo que le da la gana. Esto es, resumiendo, que no reconoce  pulsación alguna, ni movimiento. En cuanto "siente" algo (sea pulsación o  movimiento), lo único que hace es colocar el puntero del ratón en la  parte superior izquierda de la pantalla y clicar (con lo que me abre el  menú "Aplicaciones").
Desde consola, he hecho un "lsusb", y me la sigue reconociendo como  antes de actualizar. He tipeado "sudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi" a ver si es que se había  perdido el archivo con la actualización, pero sigue en su sitio,  conservando sus valores... Y hasta ahí llegan mis conocimientos del  "consoleo". Así que os ruego que me echéis una manita, por favor, porque  yo solo me pierdo. Y googleando todavía no encuentro nada aplicable a  la 10.04 (apenas sí lo hay para la 9.10... imaginaos).
 Un saludo, ¡¡¡y mil gracias!!!
 PD: Disculpad si me he liado demasiado al redactar el post...

---

### Post by negora on 2010-05-04
Hola. Tengo otro modelo de tarjeta tipo "wizardpen" y estoy en una situación similar, aunque sí que me reconoce el movimiento. Sin embargo, tras la primera pulsación sobre la tableta, hay que mantener el lápiz pulsando para que me siga reconociendo el movimiento de éste.

**Leelogarduk:** Prueba a añadir el repositorio de DoctorMo para Ubuntu 10.04:

```
deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu lucid main
```

E instala el paquete "xserver-xorg-input-wizardpen". A ver si con eso mejora algo.

---

