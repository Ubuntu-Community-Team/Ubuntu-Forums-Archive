---
title: "Dos problemas al actualizar a 10.04"
date: 2010-05-31
forum: Instalación y Actualización
---

### Post by aantinao on 2010-05-31
Estimados

Soy nuevo de foro. Al arrancar mi equipo recien actualizado, justo antes de aparecer la pantalla de login, la pantalla me muestra dos errores, luego el ordenador se queda unos 60 segundos colgado, hasta que finalmente arranca, no es un problema crítico, pero es molesto qe tarde tanto en arrancar (incluso mas que con windows xp, qe ya es decir)

los errores son estos:

mount: mounting none on /dev failed: No such device
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

Luego es cuando se queda colgado unos 60 segundos para arrancar sin problemas transcurrido ese tiempo.

¿alguien ha encontrado la solucion?

Saludos cordiales

---

### Post by Ferduz on 2010-07-29
Hola aantinao, te comento que esto funciono para mi;
 				 				**Re: removing apparmor** 			
 			 			 		   		 		 		If you remove it, you need to update your initramfs.  I did this:

1. created custom kernel and got rid of apparmor (optional)

2. to remove it:  	Code:
 	apt-get purge apparmor 
3. to get rid of config folder:  	Code:
 	rm -rf /etc/apparmor* 
4. to not try to load removed apparmor script:  	Code:
 	update-initramfs -u 
And it was all gone.  In your case, you may simply need to do the  update-initramfs and that's it.  I'd recommend making backups before  doing any of these steps!


Lo saque de aqui, [http://georgia.ubuntuforums.org/showthread.php?p=8456613](http://georgia.ubuntuforums.org/showthread.php?p=8456613).

En cuanto al otro error desaparecio, lo cual no es bueno ya que no saber la causas de una solucion es un problema futuro asegurado, asi que recomiendo hacer:

unos

apt-get update
apt-get dist-upgrade
apt-get -f install ( recuerden que si por equivocacion instalaron algun paquete raro de otra version este comando los puede tirar a la lona, siempre que lo vean chequee bien que es lo que van a borrar)
apt-get clean
apt-get autoclean
apt-get autoremove


Espero te/les sirva.

saludos

---

### Post by Patriciologico on 2010-08-01
El directorio /dev contiene los archivos de dispositivos especiales para todos los dispositivos hardware y pienso que no se montan porque apparmor permite al administrador del sistema asociar a cada programa un perfil de seguridad que restrinja las capacidades de ese programa.

Entonces, si falla al leer las directrices de seguridad (pienso y lo resalto, pues no lo he comprobado) retrasa al sistema en montar los dispositivos de hardware o algún otro proceso posterior (debieras leer los sucesos del sistema)

En conclusión, como ya decía Ferduz, es muy probable que si solo lo eliminas te de problemas posteriores. Yo creo que debes dirigir la acción, a ver porque no se ejecuta apparmor y tratar de repararlo o purgarlo e instalarlo nuevamente.  


Sobre  Initramfs > es un archivo cpio comprimido en gzip. En el arranque, el núcleo lo descomprime en la RAM, lo monta y lo usa como el sistema de archivo raíz inicial. El montado del sistema de archivo raíz real ocurre en espacio de usuario

Eso explica por que retrasa el montado de discos. 



Saludos!

Movido a "Instalación y Actualización"

---

### Post by lopulus on 2010-09-04
hola: tuve un problema cuando quise actualizar a lucid. cuando reinicie la compu, me salio el siguiente error MV: cannot move `/etc/resolv.conf.pppd-backup'to /etc/resolv.conf´ operation not permited

Luego de que pude entrar y reparar a travez de recovery mode, me surgieron una serie de problemas. 
no me permite actualizar 
no me permite montar los discos que tengo y el pendrive

Desde ya muchas gracias

---

### Post by RafaelG on 2010-09-04
> **lopulus said:**
> hola: tuve un problema cuando quise actualizar a lucid. cuando reinicie la compu, me salio el siguiente error MV: cannot move `/etc/resolv.conf.pppd-backup'to /etc/resolv.conf´ operation not permited
Luego de que pude entrar y reparar a travez de recovery mode, me surgieron una serie de problemas. 
no me permite actualizar 
no me permite montar los discos que tengo y el pendrive
Desde ya muchas gracias

Lopulus,

Por favor, la próxima vez que desees publicar una duda en el foro  te pido que lo hagas en un Post nuevo ya que este Post fue abierto bajo una pregunta en especifico, por este motivo para poder ayudar a resolver tus dudas y problemas debes crear un Post nuevo donde planteas tu problema o duda. 

Si no tienes muy clara la  división que utilizamos puedes leer el siguiente post:
[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

También te pido que leas las normas he intentamos aplicarlas en el foro para que tu experiencia en el mismo sea más efectiva:
[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

---

