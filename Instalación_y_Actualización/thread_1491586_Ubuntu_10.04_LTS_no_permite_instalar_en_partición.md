---
title: "Ubuntu 10.04 LTS no permite instalar en partición"
date: 2010-05-23
forum: Instalación y Actualización
---

### Post by Rob_Erto on 2010-05-23
Estimados,

Baje Ubuntu 10.04 LTS para instalarlo en mi PC, en el tengo un disco duro de 300Gb con WinXP, cuando instale WinXP deje una particion de 20GB, pues en algun punto se me ocurriria instalar Linux, el momento llego y al arrancar el CD para instalarlo no me permite seleccionar dicha particion, me da la opcion de achicar la particion de WinXP pero no de elegir la particion de 20GB.

Espero haber sido claro, si alguien tiene alguna duda para poder orientarme no dude en consultar.

Saludos

---

### Post by asterix77 on 2010-05-24
¿Puedes iniciar desde el live cd?

Si puedes hacerlo corre el siguiente comando

#sudo fdisk -l


Puedes también verificar el estado de tus discos duros con gparted (solo desde el live cd), para ello ve a sistema ------>Administración -------->Gparted (cuidado eso sí)


Saludos

---

### Post by Rob_Erto on 2010-05-24
Haré la prueba hoy a la noche y cuento como me fue, muchas gracias de todas maneras...

Saludos!

Al analizar las particiones por Gparted el espacio que habia dejado libre me lo mostraba como utilizado, asi k lo elimine y ahora si me dio la opcion de instalar Ubuntu en esa seccion del disco.

Saludos!

---

### Post by Carlos C on 2010-05-27
Lo damos por solucionado?

---

### Post by Rob_Erto on 2010-05-27
Si, pero no le puedo colocar [SOLVED] al titulo.

Saludos!

---

