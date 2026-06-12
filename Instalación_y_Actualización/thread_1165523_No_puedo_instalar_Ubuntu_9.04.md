---
title: "No puedo instalar Ubuntu 9.04"
date: 2009-05-20
forum: Instalación y Actualización
---

### Post by obedlink on 2009-05-20
hola a todos

he decidido instalar ubuntu 9.04 32bit en la vieja PC, pero es imposible.

al iniciar el liveCD despues de la cargar aparece el logo distorcionado en la parte superior y la PC se bloquea completamente, al entrar en modo Grafico seguro, despues de la carga la pantalla se pone en negro y otro bloqueo seguro.
con APCI apagago, creo que asi se llama, tampoco funciona.
intente tambien instalarlo desde windows con wubi, pero despues de reiniciar, carga y aparece el fondo de pantalla, pero ahi se queda, no muestra ninguna ventana, y otro bloqueo seguro.

cuando digo bloqueo seguro es solo con el boton reset se puede reiniciar la maquina, reisub no funciona.

mi maquina es 
Intel Pentium 4 2.66Mhz
Tarjeta de Video ATI Radeon 7000 64MB
Motherboard Biostar P4TPT
Disco Duro Western Digital 200GB

---

### Post by Carlos C on 2009-05-20
Ante situaciones como esta muchas veces resulta hacer una instalación con la versión alternate. La diferencia es que usa un instalador en modo texto. Es menos amigable, pero no es para nada difícil de instalar. Una vez que tengas ubuntu instalado ya podrás tratar de arreglar cualquier problema de video que tengas.

Antes de que hagas algo me gustaría saber si tu equipo cuenta con mas de 384 Mb de ram. Ese es el mínimo necesario para correr ubuntu desde el LiveCD y puede ser causal de cuelgues durante la instalación que no tengas el mínimo. El alternate requiere 256.

Saludos.

---

### Post by obedlink on 2009-05-20
> **Carlos C said:**
> Ante situaciones como esta muchas veces resulta hacer una instalación con la versión alternate. La diferencia es que usa un instalador en modo texto. Es menos amigable, pero no es para nada difícil de instalar. Una vez que tengas ubuntu instalado ya podrás tratar de arreglar cualquier problema de video que tengas.

Antes de que hagas algo me gustaría saber si tu equipo cuenta con mas de 384 Mb de ram. Ese es el mínimo necesario para correr ubuntu desde el LiveCD y puede ser causal de cuelgues durante la instalación que no tengas el mínimo. El alternate requiere 256.

Saludos.
mi maquina tiene 1GB de Ram

probaré la version con instalador alternate a ver que tal con esta.

---

### Post by kamus on 2009-05-25
> **obedlink said:**
> mi maquina tiene 1GB de Ram

probaré la version con instalador alternate a ver que tal con esta.

Has probado con alguna versión anterior de ubuntu?
Puede ser que haya que pasarle algún parámetro adicional al kernel para solucionar la distorsión del splash (quizás la placa madre es algo mañosa), y lo otro!sabes que controlador esta usando tu tarjeta gráfica?

;)

---

### Post by obedlink on 2009-05-25
> **kamus said:**
> Has probado con alguna versión anterior de ubuntu?
Puede ser que haya que pasarle algún parámetro adicional al kernel para solucionar la distorsión del splash (quizás la placa madre es algo mañosa), y lo otro!sabes que controlador esta usando tu tarjeta gráfica?

;)
ya que preguntaso esto, debo decirte que las unicas versiones que me funcionan en esa PC son las version 8.04 hacia atras, la 8.10 y 9.04 dan el mismo problema.

como mi tarjeta es una ATI Radeon 7000 series 64MB pues al menos con la 8.04 automaticamente instala los driver libres de ATI, ya que no me tira ningun mensaje de tener hardware con drivers privativos, y puedo tener los efectos compiz activos.

la version alternate no la he podido bajar, por cuestiones de tiempo, pero les estaré informando.

---

### Post by AlexDDR on 2009-05-26
Que tipo de monitor tienes? que salidas de video tiene tu tarjeta? tiene conectado la TV? ya que si aparece imagen y es un monitor CTR puede que se vea distorcioada por una mala tasa de refresco de pantalla

Estas seguro que deja de responder el sistema?, funcionan las luces del teclado (bloq MAyuculas, Num)

Puedes apretar CTRL+ALT+F1 o F2 para verificar que aun puedes acceder a la consola

Ademas en la bios de tu pc en el Apatado de configuracion del AGP, verifica que tienes desactivado el fast write o cualquier opcion extra del AGP desactivala 

SAludos

---

### Post by kamus on 2009-05-26
> **obedlink said:**
> ya que preguntaso esto, debo decirte que las unicas versiones que me funcionan en esa PC son las version 8.04 hacia atras, la 8.10 y 9.04 dan el mismo problema.

como mi tarjeta es una ATI Radeon 7000 series 64MB pues al menos con la 8.04 automaticamente instala los driver libres de ATI, ya que no me tira ningun mensaje de tener hardware con drivers privativos, y puedo tener los efectos compiz activos.

la version alternate no la he podido bajar, por cuestiones de tiempo, pero les estaré informando.

Puede que sea con las nuevas versiones del kernel, de todas maneras si  funciona bien la versión 8.04 quizás deberías usar esa versión si no es un tema critico tener paquetes un poco mas antiguos (aparte tiene soporte LTS).

Saludos

---

