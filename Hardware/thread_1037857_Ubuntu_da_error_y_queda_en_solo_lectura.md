---
title: "Ubuntu da error y queda en solo lectura"
date: 2009-01-12
forum: Hardware
---

### Post by edugonza2008 on 2009-01-12
Hola , socorro !!!!! El viernes apague la maquina y hoy lunes la prendo y me encuentro que el sistema da error, me permite arrancarlo solamente en modo lectura , saltenado el proceso de verificacion.
Como recompongo esto, soy usuario inexperto en linux, y necesito urgente usar la maquina.
Encontre presionando la tecla scape, un testeador de memoria y ya me dio un montor de errores, que es lo que paso!!!!!!

---

### Post by sergiom99 on 2009-01-12
podes poner un poco mas de detalles de que error te esta dando?
Que version estas usando?
Con un poco mas de data alguien seguro va poder darte una mano.

---

### Post by edugonza2008 on 2009-01-26
hola, termine reinstalando todo devuelta, lo que sucedio es que apague la maquina antes que el sistema termine de cerrar, y resultaron dañados un monton de bancos de memoria, asi que no supe como repararlos y reinstale todo.
es un problema que no entiendo por que sucede, ya que si se corta la luz justo cuando estas apagando el sistema el misma se rompe, es esto asi???
gracias !!

---

### Post by guillermolisi on 2009-01-26
> **edugonza2008 said:**
> hola, termine reinstalando todo devuelta, lo que sucedio es que apague la maquina antes que el sistema termine de cerrar, y resultaron dañados un monton de bancos de memoria, asi que no supe como repararlos y reinstale todo.
es un problema que no entiendo por que sucede, ya que si se corta la luz justo cuando estas apagando el sistema el misma se rompe, es esto asi???
gracias !!

En realidad no son los bancos de memoria lo que se pueden dañar sino que la estructura del filesystem queda corrupta y es necesario revisarla y corregir lo que no este bien para el funcionamiento de la maquina.

Cuando haces un shutdown lo que el sistema hace es cerrar adecuadamente los archivos del filesystem asi no tenes problemas cuando lo volves a iniciar.

Igual hay herramientas que realizan esta tarea de verificacion y arreglo que evitan tener que instalar todo de nuevo (fsck).

---

### Post by edugonza2008 on 2009-03-06
> **guillermolisi said:**
> En realidad no son los bancos de memoria lo que se pueden dañar sino que la estructura del filesystem queda corrupta y es necesario revisarla y corregir lo que no este bien para el funcionamiento de la maquina.

Cuando haces un shutdown lo que el sistema hace es cerrar adecuadamente los archivos del filesystem asi no tenes problemas cuando lo volves a iniciar.

Igual hay herramientas que realizan esta tarea de verificacion y arreglo que evitan tener que instalar todo de nuevo (fsck).

Muchisimas gracias por la respuesta, te constesto hoy porque no sabia que lo habias hecho.saludos

---

