---
title: "¿Qué sistema me conviene usar para formatear?"
date: 2011-07-12
forum: Hardware
---

### Post by 53RG10 on 2011-07-12
Hola a todos
Apelo a sus conocimientos, y les comento:
Tengo un disco nuevo y quiero instalar Windows primero (quisiera no tener que hacerlo peeeeero... monopolios son monopolios por ahora), y luego Linux. Mi pregunta es la siguiente, si lo particiono en 3, la tercera partición sería únicamente para archivos de datos, ¿En qué me conviene crearla? (Ej: NTFS, FAT, alguna de linux)
Muchas gracias y hasta pronto seguramente

---

### Post by gmunioz on 2011-07-13
Sugerencia:
Una partición primaria, ntfs, para MSwindows.
Una partición primaria ext4 para /
Una partición extendida del resto
En esta partición extendida
Una lógica para swap (intercambio)
Una lógica para /home (ext4)
Una lógica para datos (ntfs)

---

### Post by 53RG10 on 2011-07-14
Gracias
Preguntas al respecto:

*- Una lógica para swap (intercambio): *Tengo 4GB de memoria, ¿de cuánto me conviene crearla?

*- Una lógica para /home (ext4): *¿Es necesaria? ¿Para qué sirve?

El resto era más o menos lo que tenía pensado, pero esas 2 cosas no me quedan claras.
Saludos

---

### Post by gmunioz on 2011-07-14
1- Con 4 gigas de Ram, 1 giga de swap es suficiente. en general se estila usar el doble de la Ram hasta no mas de 1 giga.
2- /home separado permite mantener las configuraciones a salvo para proximas actualizaciones o reinstalaciones.

---

### Post by 53RG10 on 2011-07-15
Abuso de novato con otra pregunta :wink::

*/home separado permite mantener las configuraciones a salvo para proximas actualizaciones o reinstalaciones.*

Ahora sólo me queda una duda y es cómo se instala Linux de esa manera, o sea, creo la **partición /**, **la partición /home** y la **swap**, pero la **/ **y la **/home** cómo hago para instalarlas para que funcione correctamente y cuánto tamaño le debería poner a cada una (Te aclaro que espacio tengo porque tengo un disco de 1TB, pero sé que Linux no necesita mucho espacio para el sistema).

Espero haber sido claro y espero también que sea la última pregunta porque sé que es demasiado abuso ya
Saludos

---

### Post by gmunioz on 2011-07-15
1- Cuando llegas a particionamiento eliges manual.
A estas alturas se supone que ya has instalado MSwindows
en una partición primaria y has dejado espacio libre para
gnu/Linux.

2- Creas:
Una partición lógica (Ubuntu se encarga de generar
la extendida en el espacio libre) sistema de archivos ext4,
punto de montaje /, en general con 25 a 30 gigas es suficiente.

Una partición lógica, sistema de archivos intercambio, de
1 giga, se monta por defecto como swap.

Una partición lógica, sistema de archivos ext4, punto de montaje
/home (el tamaño depende de lo que alojes, si creas una de datos para
compartir archivos fotos, musica, textos, calculo, pdfs,etc.) con 15 gigas
es suficiente.

Y si has instalado ntfs-3g ntfs-config y las ntfsprogs, creas una lógica ntfs del espacio que necesites para alojar tus datos, punto de montaje
/media/datos, si no la creas desde MSwindows, una vez terminada la instalación de Ubuntu.

Hasta aqui nada a cambiado, hace falta aplicar los cambios para que estos
se hagan efectivos y continue la instalación.

Una vez iniciado el sistema es necesario ejecutar en una terminal
sudo su
chmod -Rf 777 /media/datos 
Para poder escribir en esa partición.

Si la creas desde MSWindows, mediante ntfs-config la montas y le otorgas permisos.

Si usas Maverick, existe un bug para ntfs-config que demanda ejecutes en una terminal antes de iniciarlo:

sudo su
apt-get update
apt-get install hal
mkdir  /etc/hal/fdi/policy

---

### Post by 53RG10 on 2011-07-15
Muchas gracias por todas tus respuestas, muy claras todas.
Ahora lo tendré que llevar a la práctica y ver si de verdad entendí ;)
Sino, acá estaré otra vez...
Saludos y ojalá NO sea hasta pronto :D

Sergio

---

