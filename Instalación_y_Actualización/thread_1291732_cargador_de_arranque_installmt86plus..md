---
title: "cargador de arranque /install/mt86plus."
date: 2009-10-15
forum: Instalación y Actualización
---

### Post by lolo.leo on 2009-10-15
mis saludos respetuosos.
Luego de mirar en profundida nuestro foro no he podido encontrar respuesta.
Recibi el disco  ubuntu 9.04 (desktop edition), al momento de instalar ubuntu, indica "casper/vmlinuz" , asi tambien cuando opto por probar ubuntu, figura : "casper/vmlinuz".
Selecciono analizar la memoria,luego de cargar un momento indica ; cargador de arranque /install/mt86plus.
asi igual en los otros dos ejemplos que mencione cargador de arranque.
casper/vmlinuz y instal/mt86plus.
tremendas ganas tenia de empezar con ubuntu, y dejar windows en el pasado. 
 
info sobre el computador:
 
pentium III 
cache: 32 KB Level! :256 Level2; 0 KBLevel3; 0 KB trace
placa base: IBM
RANURAS PC CARD (PCMCIA) 32 BIT
PC CARD (PCMCIA)                32 BIT
PCI                                       32 BIT
DISPOSITIVOS EN PLACA        RFID 
UNIDAD   C          18,63 GB
MEMORIA MODULOS INSTALADOS     2
255 MB
ARCHIVO DE PAGINACION 618 MB
 
 
gracias.

---

### Post by gmunioz on 2009-10-15
Hola lol....:

1- Entra al setup de tu ordenador y configuralo

para iniciar desde el cd en primer término.

2- Guarda los cambios.

3- Introduce el cd de Ubuntu en la lectora.

4- Inicia el ordenador.

---

### Post by moreback on 2009-10-15
Descárgate la iso de nuevo y quémala a menor velocidad (8x, 4x, etc.), eso a veces funciona.

---

### Post by lolo.leo on 2009-10-16
muy bien,
 
antes que nada.
gracias
 
acabo de poder ingresar a instalar ubuntu
entonces luego de cargar me arroja la siguiente informacion:
 
[     5..042152] IO APIC resources could be not be allocated
Loading, please wait. . .
 
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs)

---

### Post by moreback on 2009-10-16
El BusyBox aparece cuando el sistema en el LiveCD no puede acceder al sistema raíz que está en el CD, esto me ha pasado cuando tengo un disco duro y un grabador de CD conectados en el mismo bus IDE. La solución fue dejar los lectores de CD en el IDE secundario y los discos duros en el IDE primario.

Si por último no te funciona, puedes grabar la imagen del CD en un pendrive y bootear desde ésta. Ubuntu viene con una aplicación que hace esto en **Sistema -> Administración -> Creador de discos USB de inicio** y para Windows tienes [Unetbootin]("http://unetbootin.sourceforge.net").

Saludos.

---

### Post by lolo.leo on 2009-10-16
entonces reviso lo que me has dicho.
este fin de semana .

---

### Post by lolo.leo on 2009-10-22
mis saludos.:P
.
 
 finalmente logre abrir el notebook,no logre encontrar los conectores.
tambien me recomendaron limpiar el lector de cd, nada .
 
intente instalar fedora, tampoco.
no quiero resignarme a windows. incluso pense en llevar el notebook al servicio tecnico.
 
mientras tanto, seguire buscando respuestas en foros y todo eso.
 
gracias.

---

### Post by moreback on 2009-10-24
Intentaste crear un pendrive del livecd para bootear con él?

---

### Post by lolo.leo on 2009-10-24
estoy arrancando la instalacion desde windows. 
todo bien, empieza a instalar y luego de cargar los datos desde el cd, me arroja el siguiente mensaje:
 
An error occurred:
 
Permision denied
 
For more information, please see the log file:
C:\docume~\admini~1\config~1\temp\wubi-9.04-rev128.log
 
 
entonces me dirijo hacia el archivo indicado pero no lo encuentro
ahora tambien voy a intentar con el pendrive.

---

