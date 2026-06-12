---
title: "Notebook MSI VR 630"
date: 2009-07-16
forum: Hardware
---

### Post by herninob88 on 2009-07-16
Hola, tengo una notebook MSI VR630 y quisiera saber si presenta conflictos de drivers a la hora de instalar Ubuntu, porque ando con ganas de cambiar a linux pero como MSI no probee drivers para el pinguino, quiero asegurarme de que ande todo antes de mandarme y empezar a renegar y parchear todo para que ande... Estuve buscando en Google, pero no encontré comentarios sobre este modelo, por eso pregunto que si conocen a alguien que tenga este modelo o que sepa que andubo o conoce de donde descargar los drivers me sera de mucha ayuda... gracias :D

Hernán

---

### Post by Mauro22 on 2009-07-16
Bajate la .iso de la pagina oficial de ubuntu en el sabor que quieras: ubuntu, kubuntu, xubuntu (gnome, kde, xfce en el mismo orden)

Una vez que la bajar, la quemas en un cd con la opcion de "quemar imagen de cd" y luego booteas con el cd.


Te va a aparecer un menu de ubuntu, y elegis la opcion "probar sin instalar" y ahi te vas a dar cuenta que anda y que no, proba audio, red, etc etc. 

De una puede no andar la placa de video, pero eso se arregla si pones la marca y modelo, aca te van a decir si anda o no...


Drivers no necesitas, por lo general ubuntu levanta el 90% del hardware sin meter nada.



PD: Quema el cd bien lento, para evitar errores!
PD2: Baja la iso usando torrent que ganas velocidad!!

---

### Post by staar on 2009-07-16
la mejor forma de saberlo es descargando el livecd y probándolo vos mismo, solo bajarlo desde la página, grabarlo, e iniciar la notebook con el cd puesto, ahí podés probar el SO, totalmente funcional, sin instalarlo, y testear los diferentes componentes para ver si funcionan bien, prestale especial atención a cosas como el video y el wifi...

en linux, la mayoría de los drivers no se instalan aparte, sino que están incluidos en el kernel (el nucleo del SO) y funcionan por autodetección, aunque hay excepciones (porque son drivers no libres), como son las placas nvidia, algunas ati, y algunas wifi, pero igual es muy fácil instalarlos, el sistema tiene una herramienta especial para ello en Sistema > Administración > Controladores de hardware...

saludos

---

### Post by sartrejp on 2009-07-19
Yo uso una MSI vr340x y reconoció todo sin problemas, (para la aceleración gráfica tuve que agregar un script al inicio y nada más, si lo llegás a necesitar te lo paso.
Igual lo más recomendable es, como te decían, probar un livecd.

---

### Post by herninob88 on 2009-07-21
Gracias a todos, lo voy a probar ;) se nota que son una comunidad comprometida =D>... Les comento como me fue...

Saludos...

---

### Post by Guineapig1 on 2009-07-30
Hola.

Yo tengo la misma notebook e instalé Ubuntu 9.04 y al reiniciar por primera vez anduvo todo bien. Pero la segunda vez a no anduvo el video. Seguro es un problema de drivers.

Yo voy a seguir buscando la solución. Si tenés el mismo problema, avisá. Si llego a encontrar la solución te la paso.

---

### Post by sartrejp on 2009-07-30
Para la aceleracion grafica yo tuve que hacer lo siguiente
un script con lo siguiente
```

#!/bin/sh
SKIP_CHECKS=yes compiz --replace

```

Ese script está guardado como micompiz.sh, le di permisos de ejecución, y está entre las aplicaciones al inicio.
Por ahí te sirve, mi placa es Intel Corporation Mobile GM965/GL960

---

### Post by Guineapig1 on 2009-08-01
Gracias por tu ayuda.
Voy a probar este script.
Lo que pasa es lo siguiente: instalo el sistema con el live cd y cuando me pide reiniciar, lo hago. La primera inicia bien el sistema pero el programa para habilitar los drivers privativos de Nvidia no me detecta la "placa de video" (digo "placa" porque es una notebook). Asi es que los instalo manualmente, lo cual se realiza con éxito, incluso funcionan los efectos como Compiz y toda la gilada. Pero cuando reinicio no funciona Gnome por lo que solo puedo entrar a la consola.
Probé instalar el sistema sin instalar los drivers manualmente pero sigue el problema. Otro dato que puede servir es que cuando pruebo el sistema en modo livecd, éste sí detecta la GPU.
Esta notebook tiene una GPU Nvidia 9100M G.

De todas maneras voy a probar el script.

---

### Post by pol666 on 2009-08-01
El administrador de drivers no te reconoce la placa o no te instala los driver? por que la barra de carga del programa no funciona pero instala los driver igual, solo tenes que esperar y despues te da un aviso.

---

### Post by Guineapig1 on 2009-08-01
> **pol666 said:**
> El administrador de drivers no te reconoce la placa o no te instala los driver? por que la barra de carga del programa no funciona pero instala los driver igual, solo tenes que esperar y despues te da un aviso.

Estoy casi seguro de que no la reconoce porque cuando abro el adiministrador de drivers privativos solamente reconoce el dispositivo wifi pero solamente eso.
Lo que me parece raro es que, como dije en el post, cuando pruebo el livecd y abro el administrador sí me da la opción de instalar los drivers. Pero cuando abro el sistema instalado, no lo hace.
Recuerdo que tuve un problema similar con Ubuntu 7.10 pero este me instaló los drivers al toque pero no estaba usando esta notebook, sino que era un PC de escritorio con una GPU Nvidia 6800.

---

