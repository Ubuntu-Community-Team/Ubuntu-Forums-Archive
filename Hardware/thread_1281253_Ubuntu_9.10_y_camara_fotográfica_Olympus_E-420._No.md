---
title: "Ubuntu 9.10 y camara fotográfica Olympus E-420. No se detecta la cámara."
date: 2009-10-03
forum: Hardware
---

### Post by lo gambusí on 2009-10-03
Saludos des de Catalunya, compañeros.

Me dirijo a ustedes para ver si pueden ayudarme, ya que en el Catalan Team de momento no han podido.

Hace pocos días me compre una cámara Olympus E-420,. Cuando intento descargar las fotografías, mi ordinador no me detecta la camara, ni siquiera usando todos los programas de los que dispongo. Es curioso que, sin embargo, haciendo un lsusb en la consola sí aparece:

> logambusi@logambusi-desktop:~$ lsusb
Bus 001 Device 005: ID 07b4:0118 Olympus Optical Co., Ltd Mju Mini Digital/Mju Digital 500 Camera
Bus 001 Device 004: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
logambusi@logambusi-desktop:~$


Lo he intentado con las diferentes opciones de la cámara: opción de descargar usando programas, opción de descargar sin programas... con todas, y el resultado es el mismo. Alguien podría ayudarme?

Muchas gracias a todos.:P

---

### Post by guillermolisi on 2009-10-03
> **lo gambusí said:**
> Saludos des de Catalunya, compañeros.

Me dirijo a ustedes para ver si pueden ayudarme, ya que en el Catalan Team de momento no han podido.

Hace pocos días me compre una cámara Olympus E-420,. Cuando intento descargar las fotografías, mi ordinador no me detecta la camara, ni siquiera usando todos los programas de los que dispongo. Es curioso que, sin embargo, haciendo un lsusb en la consola sí aparece:



Lo he intentado con las diferentes opciones de la cámara: opción de descargar usando programas, opción de descargar sin programas... con todas, y el resultado es el mismo. Alguien podría ayudarme?

Muchas gracias a todos.:P
Bienvenido al subforo del LoCo Team argentino !

Una recomendacion de forma, si bien tu consulta en el LoCo Catalan no tuvo solucion por ahora, solo hace un dia que abriste el thread.
Tecnicamente hablando esa accion podria ser considerada como Cross Posting lo cual va contra las reglas de foro (Ubuntu Forums es una solo e incluye los subforos).

Considerando las respuestas que recibiste en tu thread original, hace un dia atras, lo dejare pasar con el objetivo de ver si tenes mas suerte por aqui y alguien te puede contar su experiencia y/o alguna recomendacion que te acerque a la solucion.

Cualquier consulta respecto del tema cross posting no dudes en contactarme via PM.

---

### Post by Mauro22 on 2009-10-03
Desconozco en el area de las camaras digitales, pero como todo lo electronico cada vez hace mas y mas funciones por ahi tiene como las terminales moviles que podes "elegir" que hacer al conectar por usb...


Por ejemplo, por ahi (no se) esa camara se puede usar como webcam, entonces al conectar y no especificar, no te deja acceder a la memoria...


Si mande verdura, solicito perdon. :confused:

---

### Post by pablo.s on 2009-10-03
Hola, felicitaciones por la cámara.
Mis observaciones son las siguientes:
 * Es una cámara reflex, no sé si entra
   en el espectro semi/profesional. Lo que
   se acostumbra con este tipo de equipos
   son los lectores de tarjetas, porque algo
   muy común es el desperfecto del puerto
   de salida USB que deja a las cámaras
   inusables luego de que se descompone.
   No estoy diciendo que te vaya a suceder
   a ti, pero todos los fotoperiodistas que
   conozco tienen la costumbre de tener por
   lo menos cinco tarjetas de memoria que
   van barajando con el lector conectado a la
   máquina.
 * El modelo de cámara que detecta el ordenador
   no es ni parecida a la tuya. La Mju es una
   cámara diminuta. He tenido una de esas por
   el año 2004. Posiblemente el controlador de
   puerto USB sea el mismo. Ahí está el error.

---

### Post by staar on 2009-10-03
probaste con KDE/Kubuntu? porque ese modelo sale en la lista de los soportados por Kamera (aunque sale como Olympus mju 500). solo tendrías que agregarla en las preferencias del sistema y despues usar el navegador de archivos (dolphin) o cualquier programa de fotos de KDE para acceder a ella...

salutacions

---

### Post by lo gambusí on 2009-10-06
Hola, compañeros.

Finalmente lo he "solucionado" insertando directamente la tarjeta en el lector del ordenador.

Muchas gracias por su ayuda.

Un saludo.

---

