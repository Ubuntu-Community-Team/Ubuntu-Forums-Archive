---
title: "Particionamiento recomendado para instalar Ubuntu."
date: 2010-07-12
forum: Instalación y Actualización
---

### Post by zhottaz on 2010-07-12
ola soy alejandro y quiero instalar ubuntu 9.04 pero mis dudas son que sistema de archivos usar y cuantas particiones nesesito y que directorio elegir para cada particion.

tengo un disco duro ide de 20gb y esta particionado por la mitad y cada particion esta en ntfs y en la 1ra particion hay un windows pero no me importa perder todo porque tengo otro disco sata donde tengo otro windows y ese uso.

pero kiero tener mi disco ide solo para ubuntu...... esta bien con 2 particiones?? o tengo que crear algun otra??? y que directorios instalo en la particion C y en la particion D.

me muestra las 2 partciones ubuntu y me da a elegir formato de estas y darle un directorio "salen varios entre ellos uno q se boot que creo que es nesesario,, pero cuantas particiones nesesito???? y que ago con todos los demas directorios que se puedes seleccionar??????..

mi idea no es mezclar windows con ubnutu por eso dejo exclusivamente el disco ide de 20 solo para ubuntu para no tener problemas ,, pero si me dieras una explicacion generalizada de cuantas particiones y q hacer con los directorios que muestra la instañlacion se los agradeceria muxo....

PD: igual probe el ubuntu ya q con el cd  puedo probrarlo pero no kise hacer ninguna escritura en el disco duro pensando que me podia ocacionar problemas asi que solo lo probe y lo encontre genial con solo meter el cd pude navegar en internet sin hacer nada solo pinchar eso lo encontre genial:o

y ya averigue y mi version es i386 y poseo un celeron x86 conpatible con esta version despok de ubuntu solo nesesito los pasos correctos en los discos y particionesy directorios.

---

### Post by Rolo linux on 2010-07-13
Hola:

Tienes dos opciones: dejar que el disco de instalación lo instale por sí solo usando todo el disco duro  o hacerlo manualmente formateando en Ext3 todo el disco duro asignando particiones para:

**/** (root, bin, etc, sbin, y otros directorios... )
**swap** o area de intercambio (el paging file en windows), y
**Home** (donde estan tus documentos, fotos, música... )

así tendrías tres particiones básicas en caso que tengas que reinstalar el sistema operativo no pierdas tus archivos, llamese documentos, fotos etc...

ahora que tu disco no es muy grande, debes pensar cuantas aplicaciones vas a instalar para elegir el tamaño de "/", puedes darle 8 Gb., 1Gb al swap y el resto para Home.

La primera vez que instalas Ubuntu parece dificil, pero una vez hecho te das cuenta que es mucho mas sencillo que windows, y como dies no temer perder tu Windows puedes practicar, si no te sale a la primera puedes volver a intentarlo. Los pasos que te da el disco de instalacion son bastante claros.

Te dejo un enlace donde hay un tutorial aunque esta en ingles:
[http://www.dedoimedo.com/computers/ubuntu-install.html](http://www.dedoimedo.com/computers/ubuntu-install.html)

Suerte :)
Saludos.

---

### Post by Carlos C on 2010-07-13
Hola zhottaz. Me veo en la obligación de hacerte unas cuantas observaciones, pero únicamente con el ánimo de que tu experiencia en el foro sea la mejor.

Por favor, cuando abras un hilo de conversación, evita escoger títulos que no sean descriptivos de tu problema, "ayuda!!!" no es muy adecuado en ese sentido, además de ser justamente un tipo de expresión que evitamos utilizar. Te pido que antes de volver a publicar en el foro te des un minuto para leer esto:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Por otro lado, recuerda siempre publicar en el subforo adecuado:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Por último, te adjunto un par de enlaces que te puede servir para resolver tus dudas:

[http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar]("http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar")
[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

Movido a "Instalación y Actualización".

---

