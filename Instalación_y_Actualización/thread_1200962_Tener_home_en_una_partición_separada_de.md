---
title: "Tener /home en una partición separada de /"
date: 2009-06-30
forum: Instalación y Actualización
---

### Post by jorval on 2009-06-30
Después de mucho leer y darme vueltas me convencí que una de las primeras cosas que hay que hacer en Ubuntu es tener separado /home en otra partición, no entiendo por qué las versiones de Ubuntu no vienen ya con esto hecho, bueno porque deben considerarlo muy elemental y obvio, les recomiendo que lo hagan hoy día, ahora, y para ello hagan lo siguiente:

Vamos a suponer que ya destinaste una partición para albergar tu /home; la que en este caso llamaremos hda6 

1.- Entrar a una sesión no gráfica:
ctrl+alt+F1 (para volver lo haces con alt+F7)
También lo puedes hacer en un terminal.

2.- Ingresas con tus datos de usuario

3.- Creas el directorio para montar la nueva partición:
sudo mkdir /mnt/myhome

4.- Montas la partición en el directorio creado:
sudo mount /dev/hda6 /mnt/myhome

5.- Copias el contenido de tu antigua home a la nueva:
sudo mv /home/* /mnt/myhome/

6.- Abres el fstab para agregar la linea que permitirá que se monte en
el arranque la nueva partición como /home:
sudo gedit /etc/fstab

7.- Agregas la linea:
/dev/hda6 /home ext3 defaults,errors=umount-ro 0 1
Guardar y salir

8.- Borrar /myhome de /mnt

9.- Ahora al reiniciar debería arrancar con el home desde la partición hda6

Les recomiendo leer un artículo de wikipedia que explica como funciona este asunto de las particiones y los sistemas de ficheros. Su lectura les ahorrará muchas horas de búsqueda y dudas. Esta es su dirección:

[http://es.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://es.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by moreback on 2009-06-30
Creo que antes del punto 8, primero debe desmontarse /dev/hda6 con el comando

**sudo umount /mnt/myhome**

y posteriormente borrar el directorio /mnt/myhome.

Saludos!

---

