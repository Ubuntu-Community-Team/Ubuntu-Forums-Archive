---
title: "Tu hardware en HTML"
date: 2009-05-27
forum: Hardware
---

### Post by Eddy_Kine on 2009-05-27
Pues es eso, rescate mi único aporte del antiguo foro ;)
Una excelente forma de detallar las especificaciones técnicas de tu hardware es por medio de la orden "lshw". 
 
		  ```
sudo lshw
```	 
 
Si deseas el detalle de un hardware específico puedes usar -C así: 
 
		  ```
sudo lshw -C disk
```	 
 
De esa forma obtendrás la lista y detalles de todos tus discos duros. 
 
Ahora manos a la obra, para crear nuestro html: 
 
		  ```
sudo lshw -html > nombre_del_archivo
```	 
 
Y buscando en tu carpeta personal tendras el archivo html con la especificación clara y precisa de tu harware. 
 
Bueno y para que me sirve? Pues para un montón de cosas, entre ellas cuando pidas asistencia colaborativa podrás detallar en post respectivo claramente tu hardware.-

---

### Post by moreback on 2009-05-28
Pinnear plis!

---

### Post by sucotronic on 2009-07-27
No sabía que lshw tuviese un parámetro -html, creo que me será de mucha utilidad para ayudar a los amigos en problemas. Gracias por el apunte.

---

### Post by aledruetta on 2009-07-28
Muy buen dato, Eddy Kine!!!

Mirando en el man de lshw, vi que instalando:
```
sudo aptitude install lshw-gtk
```
y colocando en consola:
```
sudo lshw -X
```
Se accede a la aplicación gráficamente.

---

### Post by maxmoraga on 2009-07-29
y puede ser xml tambien
# lshw -xml


y creo que tambien prepara el cafe

lshw -coffe

---

### Post by Carlos C on 2009-08-01
En este thread:

[http://ubuntuforums.org/showthread.php?p=7715835#post7715835](http://ubuntuforums.org/showthread.php?p=7715835#post7715835)

el usuario docetrago recomienda el siguiente parametro:
```

sudo lshw -sanitize
```de esa forma evitamos que se muestre información potencialmente sensible. Sirve mucho a la hora de postear en el foro.
Saludos.

---

### Post by themasterdark on 2009-09-22
Gracias me sirvio el comando no lo conocia... y justo necesita la especificacion de mi note....

=)

---

### Post by tmsrvs on 2009-11-22
Justo lo que buscaba, gracias!

---

### Post by Rob_Erto on 2010-05-26
Yo utilice
```
sudo lshw -html >Hardware
```
Asi me genero un archivo de nombre Hardware con todos los datos...

Saludos!

PD: El archivo lo guarda en la carpeta personal.

---

