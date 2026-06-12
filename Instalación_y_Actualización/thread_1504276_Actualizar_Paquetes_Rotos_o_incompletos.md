---
title: "Actualizar Paquetes Rotos o incompletos"
date: 2010-06-07
forum: Instalación y Actualización
---

### Post by zhelo on 2010-06-07
Hola hace tiempo supe que los repositior de ubuntu 10.04 estaban algo raros, es decir, o no se actualizaban o simplemente arrojaban un error;
llevo unos 7 dias sin recibir alguna actualizacion, trate por terminal con "sudo apt-get update" y "sudo apt-get upgrade"
pero nada =/, 0 actualizaciones, tengo todos los repositorios activados pero nada
que pasa??

---

### Post by bichopro on 2010-06-07
intenta: 
> sudo dpkg --configure -a
y luego:
> sudo apt-get update
y para terminar
> sudo apt-get upgrade

---

### Post by zhelo on 2010-06-07
> **bichopro said:**
> intenta: 

y luego:

y para terminar

muchas gracias funciono perfectamente, pero a que se debe esto???
mis saludos

---

### Post by bichopro on 2010-06-09
una actualizacion que no termino correctamente, un paquete que se bajo incompleto, etc.

---

### Post by zhelo on 2010-06-14
> **bichopro said:**
> una actualizacion que no termino correctamente, un paquete que se bajo incompleto, etc.

gracias por la aclaración :)

---

### Post by RafaelG on 2010-06-16
> **bichopro said:**
> una actualizacion que no termino correctamente, un paquete que se bajo incompleto, etc.


[SIZE=3]Este post deberian dejarlo como referencia hay varios usuarios que han sufrido ese inconveniente al momento de no descargarse correctamente una actualizacion desde el gestor.[/SIZE]

---

### Post by bichopro on 2010-06-17
quizas un mod lo tome en cuenta

---

### Post by zhelo on 2010-12-27
> **bichopro said:**
> quizas un mod lo tome en cuenta

seria bueno, por que me ha ayudado muucho esto

---

### Post by RafaelG on 2010-12-28
He modificado el titulo para que pueda servir de referencia y he movido thread al Sub-foro adecuado.

Saludos cordiales,

---

### Post by zhelo on 2011-01-21
vale, gracias

---

