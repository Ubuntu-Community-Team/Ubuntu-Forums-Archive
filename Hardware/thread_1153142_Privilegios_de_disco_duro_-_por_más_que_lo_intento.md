---
title: "Privilegios de disco duro - por más que lo intento, no quiere"
date: 2009-05-08
forum: Hardware
---

### Post by cor_stellae on 2009-05-08
Hola chicos:

De nuevo con preguntas básicas. Formateé un disco duro de 150 GB, con una sola partición. Con el GParted borré la partición anterior en NTFS, creé una partición nueva como ext3 y la formateé. Al seguir este procedimiento, el proceso de montaje fue muy sencillo y el pysdm (administrador Dispositivos de Almacenamiento) lo reconoció de inmediato, por lo que pude evitarme los procesos de montaje manuales.

El problema ahora es que luego de unos 30 intentos, todavía no me permite asignarle privilegios de lectura y escritura a través de 

sudo nautilus

propiedades > privilegios

Cada vez que le cambio los privilegios, solo, sin que yo pueda hacer nada, regresa a la posición anterior, es decir, sin privilegios de ninguna clase para ningún usuario.

Adjunto capturas de pantalla que puedan ser útiles.
El disco con el que estoy teniendo problemas es el sdc1 (el último de la lista). Creo que el error del nautilus es revelador, pero no sé si es tan sencillo como crear la carpeta ahí indicada. Ustedes me dirán.

De nuevo, muchas gracias por su ayuda.

---

### Post by sebastianabate on 2009-05-08
Podés hacer lo que necesitás desde la línea de comandos ejecutando:

sudo chmod 777 /media/sdc1

Lo que hace este comando es dar permisos rwxrwxrwx al directorio raíz de la partición que está montada en /media/sdc1 (según tus capturas /dev/sdc1)

Después de ejecutar ese comando cualquier usuario del sistema puede crear nuevos archivos o directorios en esa partición (que van a tener los permisos que cada usuario/proceso les asignen)

Si ya tenés archivos en esa partición y querés aplicarles los mismos permisos (rwxrwxrwx) podés ejecutar el comando así:

sudo chmos -R 777 /media/sdc1

La opción -R aplica los permisos al directorio que le indicás y a todos sus archivos y subdirectorios.

---

### Post by cor_stellae on 2009-05-08
Muuuáhhhhhh!!!!!! En 30 segundos, resuelto un problema que me ha tomado todo el día.... ¡Muchas gracias!!!!!!! \\:D/

Ubuntu me encanta, pero a ratos me vuelve loquita.... En fin, un millón y ya añdí este a mi nuevo archivito de lista de comandos imprescindibles en Ubuntu. :guitar:

---

### Post by sebastianabate on 2009-05-09
**BIEN** porque pudiste solucionar tu problema, pero [COLOR=Red]**MAL**[/COLOR] porque yo no revisé bien los comandos que puse antes de postear!!!!!!

En el segundo comando que te pasé le pifié a la D y mandé S... el comando es:

sudo chmod -R 777 /media/sdc1
              ^^

Y además de corregirme aprovecho para advertir del peligro de hacer un -R con los comandos chmod o chown como root (con sudo), porque aplican los cambios a todos los archivos que encuentren sin preguntar, _**[COLOR=Red]Y DESPUÉS ES IMPOSIBLE DESHACER LOS CAMBIOS AUTOMÁTICAMENTE[/COLOR]**_.

Así que ojo con esta opción

---

### Post by cor_stellae on 2009-05-09
Je je je je... muchas gracias por la corrección que ya añadí a mi documento de comandos. La ventaja es que como no había podido meterle nada del todo al disco, entonces no tuve necesidad de usar el comando incorrecto y solo usé el bueno... :guitar:

---

