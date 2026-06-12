---
title: "Correr Ubuntu desde Ramdisk"
date: 2010-04-21
forum: Hardware
---

### Post by Diego912 on 2010-04-21
Hola gente!
Tengo una inquietud.
Cuento mas o menos la situacion:
Necesito por unas compus con Ubuntu en unidades moviles, por lo cual por el momento lo unico que puedo poner como unidad de almacenamiento es un Pendrive o una SDHC (un SSD no, por los costos), ya que un Disco Duro HDD no duraría nada.
Todos sabemos que los Pendrives no duran demasiado si tienen que correr un S.O. sobre ellos... La idea mia era:
1) Instalar Ubuntu 9.10 en un Pendrive (ya lo hice, quedo bárbaro)
2) Poner a punto una instalación de Ubuntu, con todo lo que necesito que tenga.
3) Hacerla correr desde un Ramdisk (entera) para evitar el desgaste del pendrive. Que solo tenga el desgaste del arranque.
4) Al pendrive lo tengo particionado en 2. Una Ext3 con ubuntu y una FAT32 con archivos varios.

Desde el Ubuntu en Ramdisk voy a tener que levantar unos archivos de video que estan en la Fat32.

Bueno, planteada mi situacion, la pregunta seria:
**¿Es posible hacer correr mi Ubuntu puesto a punto, sobre un Ramdisk, de modo que solo se use el pendrive en el arranque y ocacionalmente para leer la 2da particion?**

Desde ya les agradezco por leer e interesarse ;)

PD: Al levantar desde el Ramdisk no se modificaria la particion Ext3 del pendrive, lo cual tambien me viene barbaro, ya que no guarda cambios el S.O.

Saludos!!

---

### Post by jpaugh64 on 2010-04-21
Well, I cannot speak Español, but I have [http://translate.google.es](http://translate.google.es) to do it for me. I think that what you are trying to do should be possible, and I wanted to do something similar once. (I never did.) I think that you would find some insights by comparing the boot process of a normal ubuntu linux distro to that of a live CD. Especially, look at the kernel boot options, and the boot scripts in /etc/init.d. You might be able to do it by writing one rc script, and placing it in the right order with the rest of them in bootup and shutdown in the /etc/rc?.d directories.

Saludos.

---

### Post by Diego912 on 2010-04-21
Gracias por orientarme hacia la solución! Incluso, a pesar del idioma!

Entiendo un poco por donde buscar la solución. En los modos de arranque del Kernel.
Me siento bastante inexperto como para ponerme a investigar esto solo.
Me gustaría saber si alguien me puede decir mas precisamente como realizar lo que jpaugh64 me propone.

Muchas gracias!

---

### Post by Diego912 on 2010-04-26
Alguien mas que me pueda explicar mas precisamente (en NOVATO MODE ON jejeje) como hacer esto?
Muchas gracias!

---

