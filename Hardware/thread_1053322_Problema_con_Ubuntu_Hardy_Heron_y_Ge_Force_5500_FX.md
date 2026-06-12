---
title: "Problema con Ubuntu Hardy Heron y Ge Force 5500 FX"
date: 2009-01-28
forum: Hardware
---

### Post by guidito73 on 2009-01-28
Buenas gente, soy demasiado nuevo en esto de Ubuntu, recien acabo de instalarlo y ya tengo problemas con la placa de video.

Resulta que ni bien entré al SO, tenia la resolucion restringida a 800x600. Automaticamente Ubuntu me dio un mensaje para instalar los drivers privativos, lo hice y la resolucion quedo en... 640x480!

Mi placa es una Nvidia GeForce 5500 FX de 256 MB. Estuve leyendo en otros posts y foros, pero ninguna de las respuestas termina de convencerme y todavia no me doy tanta maña con Ubuntu.

Instale a través de Synaptic el envyngcore y envyng-gtk pero tampoco pude solucionarlo ya que la terminal me da un error cuando quiero hacer la ejecucion de los drivers.

Asi que si me pueden ayudar la verdad me vendría muy bien porque me gusta muchisimo Ubuntu.

Gracias!

Guido

---

### Post by guillermolisi on 2009-01-28
> **guidito73 said:**
> Buenas gente, soy demasiado nuevo en esto de Ubuntu, recien acabo de instalarlo y ya tengo problemas con la placa de video.

Resulta que ni bien entré al SO, tenia la resolucion restringida a 800x600. Automaticamente Ubuntu me dio un mensaje para instalar los drivers privativos, lo hice y la resolucion quedo en... 640x480!

Mi placa es una Nvidia GeForce 5500 FX de 256 MB. Estuve leyendo en otros posts y foros, pero ninguna de las respuestas termina de convencerme y todavia no me doy tanta maña con Ubuntu.

Instale a través de Synaptic el envyngcore y envyng-gtk pero tampoco pude solucionarlo ya que la terminal me da un error cuando quiero hacer la ejecucion de los drivers.

Asi que si me pueden ayudar la verdad me vendría muy bien porque me gusta muchisimo Ubuntu.

Gracias!

Guido
Fijate si podes correr en consola el siguiente comando ```
sudo nvidia-settings
```

Este programa deberia permitirte modificar la resolucion grafica del escritorio.

---

### Post by guidito73 on 2009-01-28
sudo: nvidia-settings: command not found

Ese es el error que me da...

Vi que mucha gente tiene el mismo problema, no logro subir de 800x600 la resolucion, aunque cuando me limita a 640.480 (es decir, con el driver privativo activado) tiene los efectos activados (el fade de las ventanas, los iconos, etc)

No se que puede ser :(

---

### Post by guillermolisi on 2009-01-28
> **guidito73 said:**
> sudo: nvidia-settings: command not found

Ese es el error que me da...

Vi que mucha gente tiene el mismo problema, no logro subir de 800x600 la resolucion, aunque cuando me limita a 640.480 (es decir, con el driver privativo activado) tiene los efectos activados (el fade de las ventanas, los iconos, etc)

No se que puede ser :(
Abri Synaptic, busca nvidia-settings e instalalo.

Despues repeti el paso anterior y comenta que tal te fue.

---

### Post by guidito73 on 2009-01-28
Ahi pude ingresar al programa que provee Nvidia (supongo que es el mismo que me diste el codigo para la terminal) y tampoco puedo pasar de 640*480 (esto siempre con los drivers privativos de Nvidia). Los efectos funcionan pero las resoluciones son bajisimas, la verdad que ya agote todas las instancias que se me ocurren.

Gracias por la ayuda igual!

Voy a seguir buscando...

---

### Post by staar on 2009-01-28
hace una cosa, apreta Alt+F2 y ejecuta ```
gksudo displayconfig-gtk
``` ahi configura bien tu monitor y tu placa, guarda y reinicia el servidor grafico (Ctrl+Alt+Backspace)

saludos

---

### Post by Kojotex on 2009-01-29
Guidito, tene en cuenta que actualmente existen dos versiones de Envy: Envy Legacy y EnvyNG. Fijate en la siguiente tabla para saber cual tenes que utilizar:

EnvyNG

    * Ubuntu Hardy Heron 8.04 (arquitecturas: x86, x86_64) 

Envy Legacy

    * Ubuntu Gutsy Gibbon 7.10 (arquitecturas: x86, x86_64)
    * Ubuntu Feisty Fawn 7.04 (arquitecturas: x86, x86_64)

SI estas con tiempo pegate una vuelta por esta pagina [http://doc.ubuntu-es.org/Envy](http://doc.ubuntu-es.org/Envy) que te van a explicar como instalar correctamente cualquier version de Envy.
Suerte

[CENTER]Kojotex[/CENTER]

---

### Post by guidito73 on 2009-01-29
Muchisimas gracias por la ayuda, despues de toquetear un poco el Envy y xorg.conf, pude lograr que reconozca todo (estoy a 1024*768 con efectos!!!).

El SO se muestra perfecto, pero a la izquierda y a la derecha hay bandas negras, es decir que no ocupa la pantalla entera la ventana...

Que podrá ser???

EDIT: No paso de los 24 bits de profundidad de color, en windows llegaba a 32... ¿?

---

### Post by staar on 2009-01-29
lo de la profundidad de colores se explico el otro dia en este post:

[http://ubuntuforums.org/showthread.php?t=1050561]("http://ubuntuforums.org/showthread.php?t=1050561")

saludos

---

### Post by guidito73 on 2009-01-29
Ahhh... si, perdon por la novatada XD

Bueno, quedaria ese problema de las bandas negras a los costados de la pantalla...

---

### Post by guillermolisi on 2009-01-29
> **guidito73 said:**
> Ahhh... si, perdon por la novatada XD

Bueno, quedaria ese problema de las bandas negras a los costados de la pantalla...

Eso puede deberse a que tenes que reajustar la imagen con los controles del monitor, por ejemplo.

---

### Post by guidito73 on 2009-01-30
No no, si ajusto desde el monitor las bandas tambien se mueven (como si fueran parte del escritorio)..

Otra cosa mas: cuando ingreso a ubuntu, en la pantalla para colocar usuario y contraseña, se ve enorme y cortada, veo unicamente la caja de texto para ingresar mi usuario, pero no las opciones ni lo demas porque queda fuera de pantalla...

---

### Post by guillermolisi on 2009-01-30
> **guidito73 said:**
> No no, si ajusto desde el monitor las bandas tambien se mueven (como si fueran parte del escritorio)..

Otra cosa mas: cuando ingreso a ubuntu, en la pantalla para colocar usuario y contraseña, se ve enorme y cortada, veo unicamente la caja de texto para ingresar mi usuario, pero no las opciones ni lo demas porque queda fuera de pantalla...

Sera que no detecto adecuadamente marca, modelo y caracteristicas del monitor, particularmente las frecuencias de barrido horizontal y vertical ?

Te fijaste como te quedo el contenido del archivo /etc/X11/xorg.conf para verificar esto ?

---

