---
title: "problemas con wifi Atheros AR9285 en una Netbook AR9285"
date: 2009-10-04
forum: Hardware
---

### Post by donmatas on 2009-10-04
Estimad@s ubunteros:

Estoy instalando Ubuntu 9.04 en un Toshiba NB 200 que tiene esta bendita tarjeta wi fi Atheros AR9285. Ya hice lo que señalaban de instalar linux-backports-modules-jaunty, reinicié pero no funciona. Si escribo en el terminal echo ath9k / sudo tee -a /etc/modules , me devuelve ath9k. 
Intenté encender la antena (fn+f pero permanece apagada... ¿tienen alguna solución?

gracias de antemano

salud
DM

---

### Post by Patriciologico on 2009-10-05
donmatas,

 Tus post ha sido movido, por que no lo publicaste en lugar correcto (en cada seccion hay un aviso sobre lo que puedes publicar), ademas no cumples con las normas (lee "Lectura necesaria de todo buen forero en mi firma) al publicar mas una vez la misma pregunta.

 Si tu nos ayudas a que el foro se mantenga ordenado, sera mas facil dar respuesta a tus problemas,

Saludos.

---

### Post by moreback on 2009-10-05
> **donmatas said:**
> Si escribo en el terminal echo ath9k / sudo tee -a /etc/modules , me devuelve ath9k. 

Creo que estás errando con el comando, debiera ser:

```
echo ath9k **|** sudo tee -a /etc/modules
```Pero más fácil es que agregues **ath9k** al final de tu archivo **/etc/modules** con el editor de tu preferencia.

---

### Post by donmatas on 2009-10-05
Compa, la línea de comandos la puse bien en la terminal y el resultado es el mismo.
abro con gedit el modules y la última línea dice ath9k...
He estado explorando y al parecer es necesario encender el dispositivo desde win$... el problema es que no tengo lector CD's y no se como hacer un usb booteable con win xp desde ubuntu (tengo la imagen).

saludos
DM

---

### Post by _ZeTa on 2009-10-14
donmatas, si es ese el caso, existen windor$ portables [pre-hechos] o el mismo hiren's boot cd [v 10.4] que tiene un windor$ live... 
a todo esto, usaste FUCH? :rolleyes:

saludos!

---

### Post by donmatas on 2009-10-15
> **_ZeTa said:**
> donmatas, si es ese el caso, existen windor$ portables [pre-hechos] o el mismo hiren's boot cd [v 10.4] que tiene un windor$ live... 
a todo esto, usaste FUCH? :rolleyes:

saludos!

compa:
no le entendí mucho el post...¿win$ portable pre-hecho? de donde saco eso. Yo tengo una imagen .iso de un xp que extraje de un cd. No sé lo que es hiren's boot cd [v 10.4], pero supongo que será un programa para crear un usb boot con xp. Ya he intentado eso con dos programas distintos pero no me ha funcionado (arranca pero al rato dice que le falta un archivo)

¿FUCH? te refieres al [Foro Único de Chespirito]("http://www.forumch.com.br/")? jejejej

saludos
;M

---

### Post by Maciett on 2009-10-15
Hola a todos.

Estimado donmatas,

Fuch es un software que facilita el soporte.  En este tema esta [http://ubuntuforums.org/showthread.php?t=1211568 ]("http://ubuntuforums.org/showthread.php?t=1211568")

Descárgalo, instálalo y postea lo que te entrega.

---

