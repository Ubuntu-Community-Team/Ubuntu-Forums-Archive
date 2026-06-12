---
title: "como mantengo mis programas al actualizarme"
date: 2010-05-14
forum: Instalación y Actualización
---

### Post by asterix77 on 2010-05-14
Quisiera consultar cual es la mejor forma de actualizarme a Lucid sin perder mis programas ya instalados. Sé que las configuraciones quedan guardadas en mi home (que lo tengo en una partición aparte), pero eso no evitará perder mis programas instalados ¿o me equivoco?¿Es necesario formatear?

Saludos

---

### Post by bichopro on 2010-05-15
No es necesario formatear y tus programas se mantendran. Quizas alguna aplicacion puede tener problemas pero los upgrades son muy seguros, puedes hacerlo tranquilo. Cualquier problema con algun paquete te sera avisado en el proceso.

Cuando copias el home copias las configuraciones de los programas pero no el programa, por eso cuando borras una carpeta y ejecutas el programa parte de cero, como recién instalado.

en caso de una instalacion limpia (formateo de la paticion del sistema)

Te recomiendo que ocupes este comando: 

> sudo dpkg --get-selections > installed-software 

Eso creara un archivo con todas las aplicaciones instaladas separas por un espacio.

Luego te queda en el pc nuevo agregar los repositorios que tienes el en ubuntu anterior, por que si no, no podra bajar todos los paquetes ya para terminar toca abrir una consola y colocar: 

> sudo apt-get install 

seguido de las lista de programas. Asi instalara todo lo que tenias en el pc viejo, y como ya tendrás copiado las carpetas de configuración volverá a estar como antes.

---

### Post by RafaelG on 2010-05-16
> **asterix77 said:**
> Quisiera consultar cual es la mejor forma de actualizarme a Lucid sin perder mis programas ya instalados. Sé que las configuraciones quedan guardadas en mi home (que lo tengo en una partición aparte), pero eso no evitará perder mis programas instalados ¿o me equivoco?¿Es necesario formatear?

Saludos


         Yo la verdad prefiero realizar una instalacion en Limpio de ubuntu, por experiencias vividas los Upgrade me han traido muchas dificultades.

---

### Post by asterix77 on 2010-05-18
Bueno finalmente di el paso, instalé lucid desde un cd. No tuve mayores problemas, y mis archivos del home (partición aparte), no se tocaron, pero me asaltó otra duda.

Se que en mi home quedan las configuraciones personales de los programas instalados, pero al actualizar muchos de esos programas no son instalados, por lo que esas carpetas con las configuraciones ocupan espacio. ¿se pueden borrar sin problemas?

o ¿existe alguna utilidad de limpieza?.

Saludos

---

### Post by BenjaminChile on 2010-06-30
COTERRANEO,

recomiendo el uso de Bleach Bit, te permite seleccionar con prevista aquellos archivos obsoletos, o paquetes rotos del pasado que ocupan espacio. Ademas existe acceso de usuario para archivos que no son dependientes del sistema o de otros paquetes, y y tienes el acceso de root con esta aplicacion para autorizar acceso a tipos de archivo de seguridad de tu sistema o dependientes de aplicaciones elimindas, acceso a tmp, a cahe de synaptic etc...

Saludos a Quellon, el temporal de viento por Castro es de 81 kms...

---

### Post by asterix77 on 2010-07-02
Gracias por el dato de la aplicación, no la conocía.

Con respecto al clima, acá en Quellón estuvo igual, dimelo a mi que trabajo en una salmonera.........


Saludos

---

