---
title: "problema con TV OUT"
date: 2009-01-03
forum: Hardware
---

### Post by tatousb3 on 2009-01-03
hola, mi nombre es ariel y no conozco mucho de linux es mas recien ayer intale el ubuntu 8.10 en mi PC. Todo iba bien hasta que quise conectar el Tv out de la placa, (Nvidia 5200) el driver lo instale y esta habilitado nvidia 173, probe con 1000 configuraciones distintas del xorg.conf y no logro que me lo reconozca al TV (problema similar tuve en WinXP pero logre que funcione), el cable que uso es de svideo en una punta y rca en la otra, el tema es que cuando le cambio el xorg.conf en el booteo del ubuntu me tira un error que me dice que tengo que iniciar en "Low graphics" y me desconfigura el driver... y tengo que reinstalarlo para que vuelva a funcionar... ¿a alguien le paso algo como esto? ¿como lo puedo solucionar? gracias

---

### Post by staar on 2009-01-03
primero que nada, es muy importante prender el tv antes que la pc, para que lo reconozca en el booteo...

segundo, proba con el NVIDIA X Server Settings (esta en Sistema->Administracion), activando la twin view...

sino instala el nvtv, buscalo por Synaptic, creo recordar que sirve especificamente para lo que queres...

saludos

---

### Post by tatousb3 on 2009-01-04
gracias por responder, el tv esta prendido siempre antes de arrancar la pc pero no me lo reconoce, intente desde el panel de nvidia pero no me da esa opcion, aca pongo una captura
[[IMG]http://img387.imageshack.us/img387/1984/capturanvidialv5.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img387.imageshack.us/img387/capturanvidialv5.jpg/1/w1280.png[/IMG]](http://g.imageshack.us/img387/capturanvidialv5.jpg/1/)

lo que no probe fue eso del nvtv... voy a ver si busco como se instala... es que todavia no entiendo mucho...

saludos

---

### Post by tatousb3 on 2009-01-04
bueno instale el nvtv lo configure pero sigue sin mandar señal al Tv... :evil:

---

### Post by alejandro.mc on 2009-01-05
Buenas, ya lei que probaste mil configs del xorg.conf pero bueno por ahi esto ayuda. Te paso la config que le pongo yo cada vez que conecto la laptop a traves del puerto S-Video Out (TV Out). Obviamente de esta manera:

1 Prendes la PC
2 Conectas el cable de TV Out de la PC a la TV
3 Prendes la TV
4 Pones la TV en S-VHS
5 Abris el xorg.conf: en la consola:

su
contraseña
cd /
cd etc
cd X11
nano xorg.conf
en la Section "Device" le pegas esto al final:

Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "TV"



De modo que queda esto en total:

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "RightOf"
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
        Option "UseDisplayDevice" "TV"
EndSection


6 Apretas Ctrl + O
7 Apretas Enter (es para grabar la config)
8 Apretas Ctrl + X (para salir)
9 Log Out de la sesion
10 Log In (puede demorar unos segundos y hacer algunas imagenes extrañas pero deberia aparecer la imagen en menos de 30 segundos)




Muchas suerte!

---

### Post by tatousb3 on 2009-01-06
estuve

---

### Post by tatousb3 on 2009-01-06
estuve tocando varias cosas y ahora el nvidia-settings me da las opciones para configurar el tv pero sigue la pantalla negra sin señal... voy a probar esa configuracion en el xorg.. (una mas, una menos) el problema es que cuando cambio las configuraciones me salta el cartel que me dice que tengo que iniciar el ubuntu en modo low graphics :confused: peero en una de esas la pego y anda... esta tarde pruebo y les comento como me fue

gracias

---

### Post by tatousb3 on 2009-01-06
ahora anda, pero con el twin view me queda el escritorio dividido pero ya es mucho mas facil de solucionar... muchisimas gracias por tomarse un tiempo para ayudarme...

saludos

---

### Post by totolinux on 2009-01-07
Hola yo lo uso siempre en mi pc tenes que usar modo "clone" en lugar de "TwinView" de esa manera te clonara el escritorio y luega guardar la conf.
eso es para  esa sesión en la proxima deberas volver a configurar.
para que recuerde la config. hay que iniciar desde terminal 
$ sudo nvidia-settings
luego le pones la clave. configuras y guardar la configuración de esa manera te edita en forma autom. "xorg.conf" como lo hace (alejandro.mc) suerte.
pd :si no te queda claro cuando mire la otra pc te digo todo "paso por paso"

---

