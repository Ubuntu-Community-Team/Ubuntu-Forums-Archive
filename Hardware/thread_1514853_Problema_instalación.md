---
title: "Problema instalación"
date: 2010-06-21
forum: Hardware
---

### Post by julicabrini on 2010-06-21
Hola como andan?? espero que bien...

Bueno, cuando doy a la opción "instalar ubuntu" todo marcha bien pero empiezan a mezclarse colores hasta aparecer toda la pantalla negra, lo soluciono apagando y prendiendo el monitor.

Más tarde, a la hora de instalar ubuntu 9.10 ( el 10.04 todavia no me animo a instalarlo), las ventanas instalación se ven muy grandes y no alcanzo a ver la totalidad de ellas lo que se torna demasiado molesto para instalar. Seguramente sea un problema de la placa.

La verdad es que me j**e bastante porque cuando da la opción de particionar el disco, no veo las barras completas y no se que estoy particionando....

Actualmente tengo en mi máquina Windows XP y Ubuntu 9.04


Microprocesador: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+

Placa de video: GeForce 6150SE nForce 430 (en ubuntu tengo instalado el controlador privativo de Nvidia y funciona a la perfección)

Desde ya muchas gracias!! 

Saludos!

PD: No supe en que sección del foro poner el post

---

### Post by euzkoarima on 2010-06-22
El hardware que tenés es "bastante normal" no deberías tener problemas.
Lo de la las ventanas muy grandes: no será que cuando te da el "problema de los colores" te cambia la resolución de la pantalla a una muy baja ? (fijate en preferencias -> resolucion de pantalla).

Con respecto a no animarte al 10.04 , creo que el 10.04 es bastante más estable con el 9.10, yo en tu lugar iría directo al 10.04

Saludos,
Eduardo

---

### Post by alfplayer on 2010-06-22
Se puede probar con el CD alternativo de Ubuntu que tiene otro instalador.

---

### Post by julicabrini on 2010-06-22
Mil gracias por responder!

Creo que voy a probar instalando el alternativo... En cuanto a la versión 10.04, la bajé y la quemé al CD con la velocidad más baja posible y aún así el disco trae errores... Que me recomiendan hacer? Ponerlo en un pendrive??

Saludos!

---

### Post by alfplayer on 2010-06-22
Quemar un CD de ubuntu es como quemar cualquier CD con un iso. Si falla puede haber problemas con la grabadora o con el CD. Podés calcular el valor MD5 del archivo iso antes de quemar el CD para saber que el archivo está perfecto (se puede hacer con el comando md5sum y comparar el valor calculado con el que corresponda en [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes"))

---

### Post by julicabrini on 2010-06-23
hola de nuevo

no me había fijado a la hora de quemar el cd del archivo md5.. ahora me fije y me aparece esto:

```
juliancabrini@juliancabrini-desktop:~$ cd /home/juliancabrini/Downloads
juliancabrini@juliancabrini-desktop:~/Downloads$ md5sum ubuntu-10.04-desktop-amd64.iso
3e0f72becd63cad79bf784ac2b34b448  ubuntu-10.04-desktop-amd64.iso
```

es el mismo de la página... de todos modos ya estoy terminando de bajar el alternate de i386 y el desktop del mismo...

Muchas gracias!

---

### Post by julicabrini on 2010-06-23
Listo ya pude instalar ubuntu 10.04! Muchas gracias!

---

