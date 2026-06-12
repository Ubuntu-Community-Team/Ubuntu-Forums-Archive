---
title: "&quot;Error de bus&quot; y modo solo lectura"
date: 2012-12-31
forum: Hardware
---

### Post by partu on 2012-12-31
Hola que tal, soy nuevo en el foro.

Me pasó algo rarisimo, de un día para el otro me empezó a andar mal la pc..
Tengo ubuntu 11.10 de 32 bits, en un procesador de 64 bits intel i7.


Puedo usar la computadora bien, durante masomenos 10 minutos.. Después de ese tiempo, de repente como que empieza a funcionar mal toda la pc, y los iconos de carpetas se me ponen con candadito.. 

Entro desde consola  a los directorios, pongo "ls -al" y me dice "Error de bus" .. 

Cuando quiero compiar algo con el comando "cp" me dice "Error de E/S" 

Y se me bloque todo, no puedo hacer absolutamente nada.. 

Lo más raro es que cuando apago la PC y la vuelvo a encender (si no dejé pasar bastante tiempo entre que la pagaue y la volví a prender) se me traba en el medio del booteo.


No se que hacer, alguno sabe como se soluciona??

Gracias por el tiempo!
PArtu

---

### Post by yellowpaper on 2013-01-01
Parece disco rigido destruido o mal conectado....recuerdo un error que tuve parecido (NO IGUAL) con una memoria corrupta. 
Te recomiendo hacer un dmesg y fijarte bien cual es el problema (y postearlo aca) al margen de que halla un error en el bus...

---

### Post by partu on 2013-01-01
Gracias por la respuesta.

Pero que es un "dmesg",  lo tengo qe hacer en alguna ubicación en especial???

Gracias ! Saludo

---

### Post by guillermolisi on 2013-01-01
En una consola/terminal, ingresa ```
dmesg
```y veras una larga lista de mensajes que el sistema ha registrado desde que se inicio.
Copia y pega ese contenido en tu proximo post asi podemos verlo y opinar en funcion de el.

---

### Post by yellowpaper on 2013-01-02
Tal cual como dice guillermolisi.

---

