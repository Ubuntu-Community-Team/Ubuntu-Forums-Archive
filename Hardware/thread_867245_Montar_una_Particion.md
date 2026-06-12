---
title: "Montar una Particion"
date: 2008-07-22
forum: Hardware
---

### Post by xpelaox on 2008-07-22
HOla gente!!! Que tal? Vuelvo a desafiar sus conocimientos con una pregunta:P

El tema es asi:
              Tenia Ubuntu y vista instalados cada uno en una respectiva particion, migre completamente a ubuntu, entonces formatie la particion de vista y la hize Ext3. ahora la puedo montar y usar como si fuera un disco externo basicamente. Ahora lo que quiero hacer es montar la particion y que me quede no se... como una carpeta adentro del home, como por ejemplo /home/downloads o que quede en el root /Downloads o algo asi, y que se monte automaticamente. Hay alguna forma de hacer esto? seguro que si:P

Si alguien me puede dar una mano se lo agradecere muchisimo:)

Saludosss y Gracias

---

### Post by xpelaox on 2008-07-22
otra cosa que note, es que no puedo crear carpetas ni pasarle archivos a la particion nueva:S

---

### Post by juanman on 2008-07-22
> **xpelaox said:**
> Tenia Ubuntu y vista instalados cada uno en una respectiva particion, migre completamente a ubuntu, entonces formatie la particion de vista y la hize Ext3. ahora la puedo montar y usar como si fuera un disco externo basicamente. Ahora lo que quiero hacer es montar la particion y que me quede no se... como una carpeta adentro del home, como por ejemplo /home/downloads o que quede en el root /Downloads o algo asi, y que se monte automaticamente. Hay alguna forma de hacer esto? seguro que si

En linux o unix siempre se puede :D
El q maneja el montaje de las particiones es el archivo /etc/fstab

Si queres hacerlo graficamente, podes instalar pysdm.

Te explico como hacerlo "a mano". Para editarlo, escribi
```
gksudo gedit /etc/fstab
```
Busca la linea donde esta la particion y cambiala. Tiene q quedar algo asi:
```
/dev/sda1       /downloads       ext3    defaults         0       2
```
donde: /dev/sda1 es el nombre del dispositivo de tu particion.
/downloads es el lugar donde queres q se monte. Tiene q ser una carpeta q ya exista...
ext3 es el sistema de archivos
defaults son las opciones de montaje. Hay muchisimas, hace "man fstab" o "man mount" en consola si queres mas info... Se puede especificar quien puede montar o desmontar la particion, si se pueden ejecutar programas desde esa particion, etc etc
0 lo usa el comando dump q sirve para hacer backups (no es importante)
2 lo usa mkfs (el scandisk en linux), cambialo por un 0 si no queres q le pase el fsck al inicio, o por 1 si queres mas prioridad. Creo q el 2 es el mas apropiado para esa particion...

Guardas el archivo y cerras gedit.

Despues en consola: ```
sudo mount -a
``` y ya va a remontar todos las particiones. O reinicias, como quieras...

Saludos

---

### Post by xpelaox on 2008-07-22
UHHHH genial, al pelo:D Mil gracias!!!

Ya no quedan Rastros de Vosta :D

---

### Post by xpelaox on 2008-07-22
Otra pregunta!! COmo hago para que no me aparesca en el escritorio "Soporte de 80gib" o el CD ?

---

### Post by Mister X on 2008-07-24
> **xpelaox said:**
> Otra pregunta!! COmo hago para que no me aparesca en el escritorio "Soporte de 80gib" o el CD ?

Abri desde el menu Aplicaciones > Herramientas del sistema > Editor de configuracion (o en la consola escribi gconf-editor)
 y anda a la carpeta /apps/nautilus/desktop , en la parte derecha podes elegir que mostrar en el escritorio

---

