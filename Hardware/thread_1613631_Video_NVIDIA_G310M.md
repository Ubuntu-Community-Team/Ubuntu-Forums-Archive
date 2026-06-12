---
title: "Video NVIDIA G310M"
date: 2010-11-04
forum: Hardware
---

### Post by cristiaan3003 on 2010-11-04
Hola, queria saber si alguno tiene una de estas y funcionando bien en ubuntu 10.10 o kubuntu 10.10, no la puedo hacer andar, probe la manera facil  directamente desde el repositorio y la manera dificil bajando los driver de la pagina, los 260 y pico y no funciono de ninguna. El problema es que sin placa de video no me sirve el SO xq quiero programar opengl y no anda la placa no me anda opengl.  Bueno si alguno la pudo hacer andar y me puede tirar una mano. 
Bueno la idea es que  me gustaria funcione asi lo sigo usando sino lo voy a tener que borrar y seguir usando windows.
Pd.: No se ingles asi que expliquen  en castellano

---

### Post by atari130xe on 2010-12-25
> **cristiaan3003 said:**
> Hola, queria saber si alguno tiene una de estas y funcionando bien en ubuntu 10.10 o kubuntu 10.10, no la puedo hacer andar, probe la manera facil  directamente desde el repositorio y la manera dificil bajando los driver de la pagina, los 260 y pico y no funciono de ninguna. El problema es que sin placa de video no me sirve el SO xq quiero programar opengl y no anda la placa no me anda opengl.  Bueno si alguno la pudo hacer andar y me puede tirar una mano. 
Bueno la idea es que  me gustaria funcione asi lo sigo usando sino lo voy a tener que borrar y seguir usando windows.
Pd.: No se ingles asi que expliquen  en castellano

Hola, te cuento que yo tengo una Nvidia Geforce 8400GS PCIe 256MB y tengo exactamente el mismo problema como infinidad de usuarios (este es un problema más allá de Ubuntu, de echo el problema lo tengo con varias distros entre ellas: PcLinuxOS, Arch, Chakra Linux, etc.) es algo entre el driver propietario de Nvidia y Linux (en Win no ocurre) y específicamente los drivers de la serie 260.xx.xx lo que te queda es: instalar Ubuntu 10.04.1 (hasta esa versión se usan los drivers de la serie 195.xx.xx) y funciona perfecto. La otra opción sería que instales ubuntu 10.10 pero NO hagas "click" en el ícono que dice "instalar drivers propietarios" porque va a instalarle el de la versión 260.xx.xx que jústamente es el que tiene el problema. yo reporté este bug en launchpad de Ubuntu y todavía nada, tmb en el foro de Nvidia y estamos en veremos desde Octubre, solamente paciencia.

---

### Post by guillermolisi on 2010-12-27
Tengo un maquina con una 6200, Ubuntu 10.04.1 32 bits y drivers nVidia 260 que anda mejor que con los anteriores.

El tema es que los drivers 260 los instale a mano, usando la distribucion de nVidia (con la consecuencia de tener que reinstalarlos cada vez que cambia el kernel) asi que pareceria ser que el problema entre los 260 y la 10.10 viene por el lado del kernel 2.6.35 o superior (la 10.04.1 usa 2.6.32.XX)

---

### Post by EnriqueK on 2010-12-28
Si bien lo explicado en el siguiente enlace es para la 10.04,  pienso que es aplicable pata la 10,10
[http://www.distrotest.es/?p=5349](http://www.distrotest.es/?p=5349)

---

### Post by atari130xe on 2011-01-03
> **EnriqueK said:**
> Si bien lo explicado en el siguiente enlace es para la 10.04,  pienso que es aplicable pata la 10,10
[http://www.distrotest.es/?p=5349](http://www.distrotest.es/?p=5349)

Por algún motivo tu recomendación en mi caso no funciona, ya lo había visto allá por Octubre a este método pero bueno no hubo caso, es muy frustrante porque no hay solución aparente que no sea cambiar la GPU (medio un disparate debido a que esta es una placa decente para lo que la uso yo) o mantener los drivers "viejos", en resumen: un misterio :confused:

---

### Post by EnriqueK on 2011-01-03
Una vez me pasó qie luego de recompilar un kernel a la Debia, no podía instalar el controlador Nvidia por que al parecer el linux-headers  generado no era capaz de compilar el móduilo, lo que hice fue usar el linux-source  que lo había eliminado luego de la compiiación.
Resumiendo, instala ·"linux-source" además de "build-essential" y "dkms" , seguidamente ponés
sudo nautilus /usr/src
de allí descomprimís el linux-source que estará en tar.gz , cumplidasa estas etapas, probá de nuevo en instalar el driver Nvidia

---

### Post by atari130xe on 2011-01-04
> **EnriqueK said:**
> Una vez me pasó qie luego de recompilar un kernel a la Debia, no podía instalar el controlador Nvidia por que al parecer el linux-headers  generado no era capaz de compilar el móduilo, lo que hice fue usar el linux-source  que lo había eliminado luego de la compiiación.
Resumiendo, instala ·"linux-source" además de "build-essential" y "dkms" , seguidamente ponés
sudo nautilus /usr/src
de allí descomprimís el linux-source que estará en tar.gz , cumplidasa estas etapas, probá de nuevo en instalar el driver Nvidia

Gracias Enrique, espero sirva, no lo habia intentado de esa manera, lo "raro" es que habiendo tanta gente con este problema no aparezca una solución al respecto por parte de Nvidia porque es evidente que es un tema de incompatibilidad, instalo el driver en una instalación ya séa nueva o no y zás la pantalla negra al inicio con el cartel en pantalla "no input signal"... nunca me había ocurrido antes con esta placa y ahora me ocurre con cualquier distro que actualice a la versión 260.xx de los drivers de Nvidia :confused:

---

### Post by guillermolisi on 2011-01-04
El mensaje "no input signal" resulta  porque la señal de video llega al monitor en frecuencias fuera de rango ( ya sea ambas o solo la horizontal o la vertical).

Una forma de adecuar eso es generando o utilizando un archivo /etc/X11/xorg.conf con esos valores dentro del rango operativo del monitor en uso.

---

### Post by atari130xe on 2011-01-04
> **guillermolisi said:**
> El mensaje "no input signal" resulta  porque la señal de video llega al monitor en frecuencias fuera de rango ( ya sea ambas o solo la horizontal o la vertical).

Una forma de adecuar eso es generando o utilizando un archivo /etc/X11/xorg.conf con esos valores dentro del rango operativo del monitor en uso.

Gracias por la info Guillermo, tenía una idea al respecto pero lo que me resulta "raro" por así llamarlo es que me pasa con muchas distros no solo con Ubuntu y precisamente con la serie 260.xx de Nvidia...

---

### Post by guillermolisi on 2011-01-04
Adjunto screenshot y parte del /etc/X11/xorg.conf como prueba de lo que dije mas arriba.
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 TurboCache(TM)"
EndSection
```

---

### Post by atari130xe on 2011-01-06
> **guillermolisi said:**
> Adjunto screenshot y parte del /etc/X11/xorg.conf como prueba de lo que dije mas arriba.
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 TurboCache(TM)"
EndSection
```

Cosa e Mandinga Guillermo, estoy usando PCLInuxOS y con una actualización del sistema (es Rolling release) que acabo de hacer, se instaló el driver 260.19.29 y mi pc funciona perfecto, no comprendo porque justamente hice esta misma actualización hace una semana y me dejó sin X, por alguna razón (es muy probable que se hayan actualizado algunos paquete más) justamente habia echo hace 1 hora un back up del xorg. que tenía en funcionamiento y lo estaba por usar por si al actualizar se rompian las X nuevamente acá dejo un Screenshot con la prueba, gracias :KS 

[IMG]http://img708.imageshack.us/img708/7642/snapshot1y.png[/IMG]

---

