---
title: "Recuperar tabla de particiones"
date: 2011-01-22
forum: Hardware
---

### Post by fedeavila on 2011-01-22
Hola gente después de tanto tiempo vuelvo...

Tuve un problema gravísimo... En una compu con W7 utilizando un Live CD de Ubuntu intentaba borrar la tabla de particiones de una memoria micro sd... Sin querer en vez de elegir la unidad de la memoria no elegí nada y borré COMPLETAMENTE la tabla de particiones del disco de la PC central de mi casa, casi me muero...

En la desesperación me bajé el Testdisk (todo con el LiveCD de Ubuntu) en la opción Analizar encuentra la partición de NTFS de W7 pero al tildar Write aún así no puedo iniciar nuevamente...

Tengo documentos muy importantes, de la facultad, trabajos prácticos, estudio fotografía y tengo muchas colecciones de imágenes en raw que no puedo perder!

Ahora no quiero volver a utilizar Tetsdisk porque ya escribió una tabla de particiones (que a mi parecer debe ser incorrecta) He probado la opcion de List files & directories pero me dice que el sistema de archivos puede estar dañado...

En fin, se puede hacer algo? Necesito recuperar aunque sea la carpeta de documentos y las imágenes del año pasado!

Mi pregunta es, conocen algún técnico que pueda recuperar la tabla de particiones original? o al menos que pueda hacer un escaneo y recuperar lo más importante sino estoy más que perdido :/

Desde ya, muchas gracias

---

### Post by nitstorm on 2011-01-22
Acabo de leer tu mensaje al traducir con traductor Google, tal vez este enlace puede ayudarte.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 ¡Salud!

---

### Post by fedeavila on 2011-01-22
> **nitstorm said:**
> Acabo de leer tu mensaje al traducir con traductor Google, tal vez este enlace puede ayudarte.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 ¡Salud!

Gracias, ya intenté lo de Testdisk sin éxito :(
Preferiría mil veces llevar el disco a una persona que sepa realmente y lo haga x mi :/

No es de vago, es de cag***

Además son muchos GB's los que tengo que recuperar no sabría como hacerlo.. Gracias igual

---

### Post by gmunioz on 2011-01-22
1- Si borraste la tabla de particiones, tus datos aun están a salvo e intactos.

2- Con tranquilidad y desde algún cd-live de recuperación con
aplicaciones de Microsoft, trata de reparar la tabla o recuperar los datos de la partición en sistema de archivos de Microsoft.

3- lamentablemente no solo este es un foro Ubuntu y no Windows, sino que no uso operativos de esa empresa desde hace unos 10 años, así que desconozco que aplicaciones puedan existir. Estimo que en algun foro de Microsoft debe haber información al respecto. No utilices aplicaciones Gnu/Linux, dado que Microsoft nunca liberó información ni código sobre NTFS, y lo que conocemos al respecto se debe a tecnología inversa, no aconsejable para tus necesidades.

---

### Post by fedeavila on 2011-01-22
> **gmunioz said:**
> 1- Si borraste la tabla de particiones, tus datos aun están a salvo e intactos.

2- Con tranquilidad y desde algún cd-live de recuperación con
aplicaciones de Microsoft, trata de reparar la tabla o recuperar los datos de la partición en sistema de archivos de Microsoft.

3- lamentablemente no solo este es un foro Ubuntu y no Windows, sino que no uso operativos de esa empresa desde hace unos 10 años, así que desconozco que aplicaciones puedan existir. Estimo que en algun foro de Microsoft debe haber información al respecto. No utilices aplicaciones Gnu/Linux, dado que Microsoft nunca liberó información ni código sobre NTFS, y lo que conocemos al respecto se debe a tecnología inversa, no aconsejable para tus necesidades.

Me deja un poco más aliviado el hecho de que me confirmes que los datos están intactos.

Sé que en realidad este foro es de Ubuntu específicamente (ya lo conozco hace bastante) el tema es que justamente es el único que conozco de soporte técnico.

En realidad explico como se originó el problema para que no parezca incoherente, tengo un celu con Android, y necesitaba eliminar una partición Ext2 de la tarj de memoria (con Windows no puedo, tampoco me puse a buscar alguna aplicación que lo pueda hacer) 

Como sé que existe una herramienta que administra particiones (gparted) directamente busqué un live cd que tenía por ahí y lo puse en la PC donde tengo todas las cosas importantes (justo esa) y de impulsivo, sin poner atención, eliminé todas las partis (después me di cuenta que estaba trabajando sobre el disco y no sobre la memoria) Fue todo en menos de 20 seg

En fin, gracias e intentaré el lunes ponerme en contacto con una empresa que me pasaron. No la quiero tocar a la compu...

Espero tener suerte!


PD: Si por mi fuera tampoco usaría Windows pero bueno, lamentablemente es algo que está fuera de mis manos :/




Un saludo

---

### Post by fedeavila on 2011-01-24
Bueno gente, escribo porque ya lo arreglé (a medias)
Volvi a escanear con el Testdisk pero esta vez no sólo escribí la partición NTFS sino que también la parte "booteable" por decirlo de alguna manera.

Sorprendentemente funcionó!


Si bien, no puedo acceder al sistema operativo Windows, lo que sí puedo hacer es acceder con el live cd a todos los archivos del disco rígido, por lo que voy a realizar un back up de todo y seguiré jugando un poco a ver si puedo arreglar este último incoveniente y quizás no tenga que formatear el disco...


Una vez más, linux me saca las papas del fuego :P


Un saludo!

---

