---
title: "Actualizar 8.04 a 9.04 sin perder configuraciones ni archivos"
date: 2009-07-12
forum: Instalación y Actualización
---

### Post by zombieBoy on 2009-07-12
Basicamente eso es lo que quiero... me aburri de güindous...  
Hace unas semanas me llego el disco de la nueva 9.04 y no quiero arriesgarme sin antes haber preguntado si se podia o no..
EL miedo que tengo es que al instalarlo borre todo el /home y pierda las configuraciones y todos mis programas...

Uso compiz, emesene, screenlets, internet 3,5G de entel con modem Sony Ericsson y bueno, ya se imaginaran todo lo que he hecho con mi actual 8.04 y no quiero perder ni las configuraciones ni los archivos

Saludos cordiales :).-

---

### Post by flakojaime on 2009-07-12
Hola.

Mira por _**[SIZE=5][COLOR=Blue][aca]("http://ubuntulife.wordpress.com/2008/10/31/actualizar-ubuntu-804-hardy-heron-a-ubuntu-810-intrepid-ibex/")[/COLOR][/SIZE]**_

Allí habla sobre los pasos para la actualización de 8.04 a 8.10, pero debería ser lo mismo.

saludos:guitar:

---

### Post by radixs on 2009-07-12
> **flakojaime said:**
> Hola.

Mira por _**[SIZE=5][COLOR=Blue][aca]("http://ubuntulife.wordpress.com/2008/10/31/actualizar-ubuntu-804-hardy-heron-a-ubuntu-810-intrepid-ibex/")[/COLOR][/SIZE]**_

Allí habla sobre los pasos para la actualización de 8.04 a 8.10, pero debería ser lo mismo.

saludos:guitar:

De la forma que sale en ese Blog claro que se puede pero tendrás que realizar dos actualizaciones de sistema, que significa esto? Primero deberás actualizar a Intrepid (8.10) y después deberás realizar el mismo paso para actualizar a jaunty (9.04)

---

### Post by nopersona on 2009-07-12
Tienes una partición /home separada del sistema base? si es así, ningún problema, si no, ya es tiempo de ir pensando en usar una. [Hilo sobre lo mismo.]("http://ubuntuforums.org/showthread.php?t=1206091")

Saludos.

---

### Post by zombieBoy on 2009-08-06
Hola, perdon por revivirlo pero no habia tenido una pisca de tiempo para upgradearlo.

Tengo todo separado, así:

/
/home
/swap

En concreto y segun el tutorial qe pusieron saco por conclusion que es mejor instalarlo desde 0, obviamente perderia todas las configuraciones y drivers y programas que he instalado, cosa que no quiero.
Lo otro que tambien quiero es ver si puedo pasarme de ext3 a ext4 lo he hecho con programas a otros discos duros desde partition magic desde win, pero siempre con HDD virjen.

Pero debe haber algun otro metodo no:confused:
Si estoy mal corrijanme.

Saludos.-

---

### Post by EnriqueK on 2009-08-06
Lo que creo que te coviene hacer es una migraci&#7765;n de  la 8.04 a la 9.04 , para ello abre Synaptic --> Archivo  --> Guardar selecciones como , marcas el casillero "Guardar el estado completo no solo los cambios" , le das un nombre --> Guardar , esto va a generar en  tu carpeta de usuario un archivo de texto plano que contiene el nombre de los paquetes instalados , pero sin indicar las versiones de los mismos, esta info va a servir para que puedas instalar esos mismos paquetes en otra versión de Ubuntu y para ello instala la 9.04 en / dejando sin formatear /home y luego de instalada , abre Synaptic --> Archivo--> Leer selecciones , abre el archivo creado en el primer paso y por último pulsa el botón Aplicar en Synaptic , para que esto funcione debes usar repositorios equivalentes en la nueva instalación y además debes tener una buena conexión a Inet por que son mas de 1000 paquetes que se descargarán.
Por último, este método solo instalará paquetes de repositorios , todo lo que hayas instalado manualmente por compilación o por gdebi, debes hacerlo de la misma manera-

---

### Post by vargux on 2009-08-07
[Otra cosa a página (en inglés) a tener en mente siempre para estos casos es https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes") (documantación oficial de ubuntu)

En mi blog muestro más gráficamente el proceso desde 8.10 a 9.04: [http://vargux.blogspot.com/2009/03/actualizar-ubuntu-810-904.html](http://vargux.blogspot.com/2009/03/actualizar-ubuntu-810-904.html)

Es recomentable también, si no se quiere perder nada, pero es un proceso largo, actualizar a ubuntu 8.10, desde 8.04 (haciendo el mismo procedimiento), y luego seguir las otras indicaciones, como mencionaron en este hilo.

Salu2 !!!!!

---

### Post by zombieBoy on 2009-08-10
grazzie por las respuestas. mañana haré eso de salvar en una lista los paquetes.. y recopilare en textos configuraciones 

saludos y muchas gracias!

---

### Post by CdK1 on 2009-08-12
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Más fácil?

---

