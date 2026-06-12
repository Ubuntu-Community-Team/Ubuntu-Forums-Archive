---
title: "Perdida de MBR tras instalación fallida de Windows XP"
date: 2009-07-29
forum: Instalación y Actualización
---

### Post by kena_85 on 2009-07-29
Hola, mi problema es el siguiente:
 
  Mi computador tenia instalada en una unica particion Ubuntu 7.10,  al necesitar Autocad y otros programas decidi instalar Windows XP en otra particion ...uff...  al colocar el CD de instalacion de Windows XP al iniciar mi computador al parecer se cargo automaticamente MBR en mi computador, luego cuando el programa de instalacion de Windows XP me pregunto si deseaba proseguir con la instalacion decidi posponer la instalacion, luego al encender mi computador al parecer MBR estaba cargado, pero el unico sistema operativo en el disco duro era Ubuntu, por lo tanto no se cargaba ningun sistema operativo, finalmente instale Windows XP en un espacio de memoria pequeñisimo (¿Es posible que aquel espacio corresponda a la antigua SWAP?), no he borrado nada y aun tengo la esperanza de recuperar mis antiguos archivos de Ubuntu...¿ Que puedo hacer?...
  Saludos.

---

### Post by gmunioz on 2009-07-29
Hola ken...:

Instala Total Commander y su plugin para

ext3 y reiserfs.

[www.ghisler.com](www.ghisler.com)

Con el podrás acceder a la partición de Ubuntu

Y poner a salvo tus archivos.

Luego borra el disco rígido, reinstala Windows mínimo

con autocad y reinstala Ubuntu en lo posible Jaunty

para tener inicio dual.

---

### Post by luisdavila on 2009-07-29
hola, puedes descargar el CD de supergrub disk, un utilitario muy bueno, tiene muchas herramientas, entre otras te permite de recuperar tu antiguo grub y reinstalarlo en el MBR cuando has hecho la maniobra que tu hiciste (primero linux y luego window$, yo lo hice, por eso lo sé :P )
para el supergrub disk aqui esta el enlace:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

y luego puedes editar tu menu.lst 

sudo nano /boot/grub/menu.lst 

siguiendo las instrucciones de este tutorial (en ingles, pero debe existir en español) de forma de crear una entrada para arrancar windows (utilizando el chainloader del grub).. el resultado de tu entrada windows sera algo asi, lo copie directo del documento (lee el tutorial para la historia de particiones):

title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
rootnoverify (hd0,0) # This is the location of the windows partition
makeactive
chainloader +1



 en este tutorial hay varios metodos de restauracion o reinstalacion del grub MBR, incluyendo la herramienta via un CD LIVE.. a ti de escoger y de divertirte aprendiendo.. 
el enlace del tutorial en ingles:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

suerte

P.D.  y todo lo que preguntas que si la particion SWAP o que si podras recuperar tu info de ubuntu, pues haz primero la recuperacion de tu MBR/grub y si aun asi no te arranca pues ya se puede ver otra solucion, si ese es el caso, pero para recuperar tu info con un live CD es super facil

---

### Post by Carlos C on 2009-08-01
Hola kena_85. Por favor intenta publicar títulos que expliquen tu problema. Iniciar un thread con el título "Problema complicadísimo!" no da mucha información de tu situación, ni facilita que personas con el mismo problema den con tu post si utilizan el buscador. Por favor lee la siguiente entrada antes de crear un nuevo thread:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Procedo a editar el título.
Veo que te han dado muy buenos consejos. Espero que soluciones tus dudas.
Saludos!

---

