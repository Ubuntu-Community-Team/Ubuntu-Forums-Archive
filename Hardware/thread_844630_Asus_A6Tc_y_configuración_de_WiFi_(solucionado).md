---
title: "Asus A6Tc y configuración de WiFi (solucionado)"
date: 2008-06-29
forum: Hardware
---

### Post by pabloatilio on 2008-06-29
Especialmente para los amigos sneider y K-Pi y todos los que tengan   éste equipo, el chip de wireless es el broadcom 4318 (bcm4318 es la denominación correcta), se puede encontrar toda la información de como instalar los drivers en cualquier lado, en sí en éste post no hay nada "original" simplemente lo escribo para comentar que SI se puede hacer funcionar el wireless específicamente para este modelo de notebook, de hecho ahora mismo estoy usándolo. 

La info la saqué de [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) 

Los pasos son mas o menos simples, una de las formas es la siguiente: 

1) instalar el fwcutter, para ello se van a Sistema->Administración->Gestor de paquetes Synaptic y en buscar ponen "fwcutter", les va a salir que el paquete b43-fwcutter está disponible para instalar, lo marcan y le dan aplicar, tienen que tener el disco de instalación para que el gestor pueda descargar el paquete de ahí, o tener una conexión de red cableada o haberlo bajado antes de otro lado e indicarle al gestor el orígen en donde sea que lo hayan guardado.

2) IMPORTANTE : cuando se instala el paquete anterior les va a aparecer una ventana en donde les pregunta si desean extraer el firmware o microcódigo, la tildan y recién luego pican o clickean en "siguiente".

3) una vez que el paso anterior está completo, y synaptic les avisa que los cambios han sido aplicados, hay que ir a Sistema->Administración->Controladores de hardware y verificar que Broadcom B43 wireless driver está marcado como habilitado y en uso (de no ser así habilitarlo y reinicar si es que lo pide). IMPORTANTE: Si no logran ésto no va a funcionar porque no se tiene el driver instalado, así que es importante que no pasen por alto esto.

4) después de estos pasos , en mi caso inmediatamente se me conectó a mi red WiFi, pero si no les sucede eso, verifiquen en el panel superior, en el ícono de red, que esté habilitado el modo "activar modo itinerante", para ello en el ícono de red, pican con boton izquierdo y luego en desbloquear (les va a pedir la clave administrativa) , después marcan conexiones inalámbricas y luego marcan en propiedades, ahi verifican que esté activado "modo itinerante". Pueden probar sin hacer éste paso y configurar como quieran uds, pero a mi me funcionó recién cuando marqué modo itinerante

5) una vez que están con el modo itinerante activado, pican en el monitor de red del panel superior nuevamente y les deberían aparecer algunas de las siguientes opciones (o las dos) 
  a) conectar a otra red inalámbrica, hacen click ahí y ponen los datos que le pidan de su red (nombre, clave, tipo de autenticación, etc)

   b) las redes inalámbricas disponibles, entonces marcan a la que quieran conectarse (no robarle el wifi al vecino)

6) el ícono cambia de forma y empiezan a dar vueltas unos bichos azules y verdes, cuando se conecta, el ícono es reemplazado con un cuadro de barras en donde las de color azul les marcan la intensidad de la señal

Espero que le sirva a alguien, como dije antes, está dirigido especialmente a los que tienen éste equipo, aunque probablemente sirva también para los que tienen el mismo chip. Saludos

Pablo

PD: para éste equipo nos queda por solucionar lo de la barra del control del volúmen, prometo escribir si lo consigo

---

### Post by seryu on 2009-04-09
Gracias por explicar la solución, yo tengo un a6tc y con las nuevas versiones de k/ubuntu el wifi me dejo de funcionar.

Es la solución más simple y rápida que he encontrado en toda la red.

Un saludo ;)

---

