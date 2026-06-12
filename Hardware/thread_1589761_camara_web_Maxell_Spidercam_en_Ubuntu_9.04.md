---
title: "camara web Maxell Spidercam en Ubuntu 9.04"
date: 2010-10-06
forum: Hardware
---

### Post by topito2 on 2010-10-06
Hola a todos

Saben donde puedo hallar el driver para una una webcam Maxell SpiderCam para Ubuntu 9.04? gracias de antemano

---

### Post by hectorivand on 2010-10-07
Hola Topito, te la reconoció?

Postea el resultado del comando lsusb. para saber si la reconoce.

Saludos
Nacho

---

### Post by topito2 on 2010-10-07
gracias por responder, corri el comando que recomendaste y me devuelve esto
----------------------------------------------------------
alejandro@alejandro-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 093a:2620 Pixart Imaging, Inc. 
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
------------------------------------------------------------
supongo que la parte que dice Pixart Imaging, Inc. indica que me reconoce la webcam, pero no consigo hacer que funcione con wxcam,

intente un software que se llama Cheese, pero la imagen sale con una calidad muy mala, por eso investigo si hay un driver especifico de este  modelo de webcam para Ubuntu 9.04

---

### Post by topito2 on 2010-10-07
OK, he progresado algo

me puse a revisar las preferencias de wxCam 1.0.6 y ahora por lo menos no me salen mensajes de error. Ajuste el frame format a RGB24 y el driver a Video4Linux2, pero solo me sale una imagen negra en lo que deberia ser la imagen que muestra mi webcam

En el cuadro de Info--Webcam me sale lo siguiente:
---------------------------------------
Name: USB Camera (093a:2620)
Channels: 1
Audio: No
Min resolution: 48x32
Max resolution: 640x480
---------------------------------------
No se si la solucion es instalar un driver especifico para esta webcam o usar otra aplicacion

gracias por el apoyo

---

### Post by hectorivand on 2010-10-07
Si te aparece en negro, me parece y ojala alguien pueda confirmarlo o corregirme. Pero el codec de video no esta laburando.

De todos, para que vayas leyendo... segui las instrucciones de acá.

[http://diegosamuel.blogspot.com/2007/04/instalar-una-camara-web-en-ubuntu.html](http://diegosamuel.blogspot.com/2007/04/instalar-una-camara-web-en-ubuntu.html)

Driver, de la misma manera que hay en Win, no vas a encontrar, entonces, Si no te funca con lo de arriba, lee todo esto y anda probando.

[http://www.ubuntu-es.org/node/124186](http://www.ubuntu-es.org/node/124186)

La Genius Cam Eye, tiene el mismo chip. asi que, proba con esto.:

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=6976559&postcount=7](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=6976559&postcount=7)

De última, con este.:

[http://www.esdebian.org/foro/43625/configurar-camara-genius-eye-312](http://www.esdebian.org/foro/43625/configurar-camara-genius-eye-312)

Esto es lo genial de Linux, poder probar mucho para hacer andar algo :)

Contanos como seguis.

Saludos
Nacho

---

### Post by topito2 on 2010-10-08
gracias por la ayuda, amigo

creo que he encontrado la solucion perfecta para mi problema: usare Ubuntu para las cosas que Ubuntu me permite hacer sin tanto lio, y usare Windows para aquello que me facilite la vida.

Intente las opciones de los dos primeros enlaces que me ofreciste y no se soluciono el asunto. No intente lo del tercer enlace, pues lastimosamente no tengo el tiempo para estar leyendo tanto documento y haciendo pruebas, cuando se que mi webcam funciona perfectamene en Windows, sin tanto embrollo.

Esperare a que los chicos que desarrollan Ubuntu propongan una solucion practica y efectiva a este tipo de visicitudes que se presentan al usar Ubuntu.

---

### Post by hectorivand on 2010-10-08
Topito, lamento que no tengas tiempo, ni las ganas para buscarle la vuelta. Lamentablmente para vos, no es un problema de Ubuntu o cualquier otra distro, es del fabricante de tu hardware que no fabrica perifericos compatibles con Linux.
 
Saludos
Nacho

---

### Post by guillermolisi on 2010-10-09
> **hectorivand said:**
> Topito, lamento que no tengas tiempo, ni las ganas para buscarle la vuelta. Lamentablmente para vos, no es un problema de Ubuntu o cualquier otra distro, es del fabricante de tu hardware que no fabrica perifericos compatibles con Linux.
 
Saludos
Nacho
Y agrego: hoy te pasa con la webcam, mañana puede suceder con otro componente, una placa de video (VIA por ejemplo), una WiFi, etc.

Ubuntu Linux es abierto e incluye mas drivers que Windows, pero si el fabricante no expone como esta diseñado su dispositivo es imposible desarrollar drivers (y la ingenieria inversa esta incluida en las practicas prohibidas para la mayor parte de lo que sea privativo).

No tiene nada de malo que uses Windows si para vos resulta mejor.

---

