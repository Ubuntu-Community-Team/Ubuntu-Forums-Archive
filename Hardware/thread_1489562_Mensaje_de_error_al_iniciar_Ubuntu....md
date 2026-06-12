---
title: "Mensaje de error al iniciar Ubuntu..."
date: 2010-05-21
forum: Hardware
---

### Post by dam1977 on 2010-05-21
Nuevo problemita: En mi trabajo (Estoy usando Ubuntu 10.04 desde hace 2 semanas), no se que cosa rara hice, pero me aparece el siguiente mensaje cuando arranca Ubuntu:

An error occurred while mounting /proc/bus/usb

Luego me permite saltar el error con S o arreglar manualmente. Como arreglar no tengo idea cómo, le doy con la S. y todo bien. pero, ¿qué significa? ¿Cómo se arregla? estuve buscando en los foros y con Google pero no encuentro nada sobre ese error específico....

---

### Post by leosr on 2010-05-21
> **dam1977 said:**
> Nuevo problemita: En mi trabajo (Estoy usando Ubuntu 10.04 desde hace 2 semanas), no se que cosa rara hice, pero me aparece el siguiente mensaje cuando arranca Ubuntu:

An error occurred while mounting /proc/bus/usb

Luego me permite saltar el error con S o arreglar manualmente. Como arreglar no tengo idea cómo, le doy con la S. y todo bien. pero, ¿qué significa? ¿Cómo se arregla? estuve buscando en los foros y con Google pero no encuentro nada sobre ese error específico....
Hola.
A mi también me aparece lo mismo.

---

### Post by dam1977 on 2010-05-21
Bueno, por lo menos ya somos dos!!!! jj

---

### Post by sebastianabate on 2010-05-22
Puede ser porque Lucid dejó de usar hal para manejar los dispositivos (entre ellos el bus usb); y si tienen alguna línea para montar ese bus en el fstab les tira este error (como la que se necesitaba para VirtualBox). Pasen el contenido del fstab para ver si tienen algo que genere este error.

---

### Post by dam1977 on 2010-05-23
Bueno, gracias. Pero qué cosa es el fstab y de donde lo saco?? Así te lo mando. Sorry, estoy consciente de lo ignorante que soy!!!!!

---

### Post by leonardomdq on 2010-05-23
> **dam1977 said:**
> Bueno, gracias. Pero qué cosa es el fstab y de donde lo saco?? Así te lo mando. Sorry, estoy consciente de lo ignorante que soy!!!!!
Hola dam1977 , lo que te dice sebastianabate es que muestres el contenido del fstab para ver cual es el error.
Abri una terminal y pone lo siguiente: (luego copia todo el contenido y pegalo aca) 

```
sudo gedit /etc/fstab
```

---

### Post by dam1977 on 2010-05-24
Ahi va mi fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7ecfbbe4-dac0-41aa-8621-dfd486ecf438 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3d59553-994e-409e-87cb-2109dcbb8788 none            swap    sw              0       0

---

### Post by dam1977 on 2010-05-29
Solucionado. Tenía una linea en el fstab que no iba, la habia agregado por sugerencia que encontré por ahi, relacionado con Virtualbox, pero no hacía falta. La saqué y todo volvió a andar bien...Bueno, esto es el precio de ser novato....

---

