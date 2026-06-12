---
title: "Uso excesivo de CPU"
date: 2010-08-26
forum: Hardware
---

### Post by paix_seule on 2010-08-26
[[IMG]http://img72.imageshack.us/img72/1807/pantallazoeu.th.png[/IMG]](http://img72.imageshack.us/i/pantallazoeu.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
[SIZE=3]
TENGO CENTRINO DUAL CORE 2 sistema de 64bits . EL CPU0 esta casi siempre entre 90% y 98% el CPU1 Siempre entre 0% y 30% y el CPU2 Siempre esta hasta atras osea en el 100% sospecho que algo pasa, mis efectos compiz como quemar funcionan re mal y se pega un poco a veces, antes de instalar ubuntu usaba wubi y funcionaba siempre mi tarro bajo el 50%y ahora que instale desde el live cd pasa esto... 

Que podria ser ? [/SIZE]:(

---

### Post by Carlos C on 2010-08-26
Hola. Por favor, cuando publiques una consulta preocúpate de que el título del thread haga referencia al problema por el que realizas tu consulta. La idea es que sea fácil de encontrar por alguien que tenga tu mismo problema. Antes de volver a publicar en el foro te pido que leas lo siguiente:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

También es recomendable que en el momento de compartir una imagen lo hagas a través de un thumbnail. Si te fijas, imageshack te proporciona el código necesario para ello, donde dice "Embed thumbnails of this image". 

Respecto a tu problema, creo que lo más fácil es que en el panel superior te dirijas a Sistema>Administración>Monitor del sistema. En la pestaña "procesos" podrás ver cuál de todos es el que está consumiendo tantos recursos. Puede ser que tengas algún problema con tu tarjeta de video o su driver.

Saludos.

---

### Post by nechus on 2010-10-19
Hola,

También tengo un Centrino 64 bits y hace unas semanas tuve que pedir ayuda por problemas con el video. Los efectos de Compiz se veían entrecortados, pero lo peor eran las películas porque casi no se podían ver.

Alguien propuso una solución y a algunos se nos arregló el problema. Otros informaron que seguían teniendo problemas con el sonido. Pero lo interesante es que otros, como Philetjosie y Telescopic Trout informaron que su uso de CPU, que casi llegaba al 100%, había bajado drásticamente.

Como te digo, a mí se me arregló el problema. Tengo un Acer Aspire 5738 con Centrino Dual Core, 64 bits, 3Gb RAM.

La solución fue:

En la terminal:
sudo gedit /etc/pulse/default.pa

En el archivo que se abre, busca la línea:
load-module module-udev-detect
(Está medio escondida, así que tienes que fijarte bien)

Y añades tsched=0 al final de esa línea, de modo que quede:
load-module module-udev-detect tsched=0

Guarda el archivo y reinicia el computador.

Ojalá te sirva, pero tú decides si lo aplicas. No me responsabilizo por daños, pérdidas, quemaduras ni explosiones.

El link al hilo donde pedí ayuda es [http://ubuntuforums.org/showthread.php?t=1592120&page=4](http://ubuntuforums.org/showthread.php?t=1592120&page=4)

---

