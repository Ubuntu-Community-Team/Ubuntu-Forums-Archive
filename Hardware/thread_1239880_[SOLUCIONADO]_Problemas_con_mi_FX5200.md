---
title: "[SOLUCIONADO] Problemas con mi FX5200"
date: 2009-08-14
forum: Hardware
---

### Post by krakc on 2009-08-14
Hola a todos

Les cuento que tengo esta pc:

board asrock p4i45gv
procesador P4 2.4Ghz
Ram 1.3GB
Aceleradora NVIDIA GeForce FX5200

y tengo instalado Ubuntu Ultimate Edition 2.3 - kernel 2.6.28-14-generic

les comento mi problema: resulta que vi una guia para instalar los drivers de mi fx5200 e hice lo siguiente.

1- inicio mi pc -> entro a la bios -> graficas Internal VGA
2- entro a ubuntu -> abro el synaptic -> desinstalo todo lo que sea de Nvidia
3- abro el terminal -> edito los siguientes archivos asi.
*1* /etc/default/linux-restricted-modules-common * 
**agregando: DISABLED_MODULES="nv nvidia_new"
*2* /etc/modules 
** agregando: nvidia
4- descargo la ultima version de los drivers desde la pagina de nvidia (173.14.20).
5- ctrl+alt+f1 y detengo el x server
6- instalo el driver que descargue.
7- reinicio -> entro a la bios y activo la tarjeta grafica
8- entro a ubuntu y me sale la pantalla negra, luego de un momento al presionar una tecla cualquiera me sale error x server (su interfaz grafica) ..... intento reinstalar el driver y me dice que no se halla el "nvidia.ko"
9- reinicio -> ento en modo de recuperacion.
10- hago el dkpg -> el fsck -> el de loadder -> y el xfix -> luego resume
11- otra vez la pantalla negra -> detengo el gdm -> reinstalo el driver
12- inicio el gdm $sudo /etc/init.d/gdm start -> luego lo mismo pero al final restart
13- ahora me entra al ubuntu con mi tarjeta puesta, pero no tengo sonido y no sirve el mouse..

alguna ayuda que me puedan dar???

por cierto me pasaba mucho (antes de hacer lo anterior) lo siguiente:

1- teniendo desinstalado todo lo de nvidia con el sinaptic, reiniciaba la pc, cambiaba el adaptador a mi aceleradora, iniciaba el ubuntu y me salia lo siguiente:
** tty1 respawning too fast, stopped
2- al entrar luego por el modo de recuperacion se quedaba tambien y no hacia nada con el siguiente error:
** /bin/sb: 6: /sbin/sulogin: invalid argument
** init: rcS-sulogin main process (xxxx) terminated with status 2

lo anterior tambien me pasa si intento instalar drivers con el EnvyNG.
otra forma es si intento en este momento instalar el driver que me aparece en:
** sistema -> administracion -> controladores de hardware

alguna idea ???? hice algo mal ??? algo me falta por hacer ????

por fin pude entrar al ubuntu con el monitor conectado a mi aceleradora pero ahora no tengo mouse ni sonido.

gracias

---

### Post by CdK1 on 2009-08-14
Aunque me parece verdaderamente INNECESARIO los pasos que seguiste, te pregunto, agregaste Driver   "nvidia" a tú xorg.conf?

---

### Post by krakc on 2009-08-14
si lo he hecho.

---

### Post by krakc on 2009-08-14
SOLUCIONADO

[http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/)

---

