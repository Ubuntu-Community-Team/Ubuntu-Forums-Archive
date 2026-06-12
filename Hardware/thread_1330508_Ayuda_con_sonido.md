---
title: "Ayuda con sonido"
date: 2009-11-18
forum: Hardware
---

### Post by Orly01 on 2009-11-18
A veces ubuntu no reconoce el sonido en mi notebook. Lo raro es que es súper random a veces si lo pesca y a veces no suena nada. Si me meto a preferencias de sonido cuando no suena nada no aparece nada en hardware de entrada y de salida. Uso ubuntu 9.10 y tengo todas las actualizaciones al día.

Algún consejo?... estoy chato de tener que reiniciar el pc hasta que me pesque el sonido.

---

### Post by Carlos C on 2009-11-19
Estimado, faltan datos. Lo importante sería que dieras más información sobre tu hardware. Una opción es que pruebes usando [FUCH]("http://ubuntuforums.org/showthread.php?t=1211568"), otra, que al menos corras el siguiente comando en el terminal:
```
lspci
```

Saludos.

---

### Post by AlexDDR on 2009-11-22
es actualizacion o instalacion limpia?? tiene separa el home?? lo reusaste par ala instalacion??

te lo pregunto porque yo he tenid problemas tambien con el sonido al actualizar

Podrias probar creando otra cuenta en el gestor de usuarios y entrar con ese usuario a ver si tienes el mismo problema.

total si no funciona se borra el usuario nomas

saludos

---

### Post by moreback on 2009-11-22
A mi a veces me parte el sonido en mute, así que tengo que subirle el volumen para escuchar.

---

### Post by AlexDDR on 2009-11-22
> **moreback said:**
> A mi a veces me parte el sonido en mute, así que tengo que subirle el volumen para escuchar.


a mi tambien me pasa lo mismo con una instalacion limpia  y cuenta limpia, antes co nla actualizacion era peor.

Por suerte ya arreglar en reporte de crash que salia constantemente.

todo esto entre otros dos  bugs que he detectado

saludos

---

### Post by xtremox on 2010-01-19
ami me pasa que en virtualbox se escucha saltado el 9.10 no se como arreglarlo uso virtualbox en windows por que no me dejan instalar ubuntu en el hd

---

### Post by KrushKid on 2010-08-23
Estimados amigos:
Hace un par de días saqué de cuajo windows y me involucré con UBUNTU 10.04.
Todo excelente. Tengo un Packard Bell portátil con 512MB de ram, los que corre como si fueran 1GB. Todo bien hasta que se me ocurrió conectarle unos audífonos y el micrófono.
Hay que mencionar que los parlantes del equipo si funcionan. El compu no trae micrófono incorporado. El problema es con las cosas externas.
 
¿Qué puedo hacer?
 
Agradeceré a quien responda, que considere que se está dirigiendo a un "usuario" ya que he investigado en montones de foros y todos se hablan casi de "programador a programador" 
Por favor, sean comprensivos.
Muchas gracias de antemano por su ayuda.
Cordiales saludos.

---

### Post by AlexDDR on 2010-08-23
hola, puedes probar con la configuración del applet de sonido que esta al lado del reloj. En la configuración de sonido en , salida, ahi cambia abajo headphone, o tambien probar con los otros valores.


Si eso no resulta, probar con "alsamixer" en lan cosola y ver que los volumenes esten arriba, y cambiar esas opciones dcomo HP o algo asi

Yo repetidas veces tengo estos problemas ya que todas las placas de snido que he tenidos en PCs no funciona bien el cambio automatico entre REAR y Front(tanto en win como en LIN), y tal vez sea el caso.

Saludos

PD: te recomiendo abrir un nuevo topic, por orden(normas) y complejidad o posible solucion, mas acertada

---

### Post by Kurouro on 2010-09-25
Hola [KrushKid]("http://ubuntuforums.org/member.php?u=1135765"): :)

Yo también soy Usuario de Ubuntu y no Programador. Así que trataré de ayudar.

El tema del sonido lo puedes ver de la siguiente manera:

Paso 1

En una terminal o consola escribe el siguiente comando:

**alsamixer**

Con ésta orden puedes regular el volumen de tu dispositivo de audio.

Otro paso a tener en cuenta.

Paso2

Sobre el icono de **Sonido** con el botón derecho del mouse accede a **Preferencias** y reviza las entradas y salidas del audio que estén activadas como también que controlador de audio puedas estar usando.

Y por último el paso que menos nos gusta

Paso 3

Reinstalar los controladores de **ALSA**

Los paso son:

Primero- Descarga de la página [www.**alsa**]("http://www.%3Cb%3Ealsa%3C/b%3E")-project.org los últimos Drivers-Librerías-Utilidades-OSS

Segundo- Guárdalos en una carpeta y descomprimélos ahí.

Tercero- En una terminal regístráte como Root:

[B]su
contraseña[/B]

Cuarto- Navega hasta la carpeta creada que almacena lo descargado y descomprimido 
anteriormente.

Quinto- Escribe: 
[B]
/etc/init.d/alsa-utils stop[/B]

Con ésto detienes el servicio de **Alsa**

Sexto- Entra en cada carpeta en éste orden:

[B]Driver
Librería
Utilidades
OSS[/B]

Y en cada ella escribirás:

Primero:

**./configure**

Segundo:

**make**

Tercero:

**make install**

Séptimo- Ya con eso **reinicias** y deberías tenerlo resuelto.

Espero que alguno de éstos 3 Métodos te sirvan.

Suerte amigo.

---

