---
title: "Cambiar nombre dispositivo diosco duro"
date: 2011-05-04
forum: Hardware
---

### Post by EnriqueK on 2011-05-04
Tenía mi equipo con un DD sata y era reconocido como sda, le instalé un DD IDE o PATA y no me di cuenta que el mismo estaba seteado como MASTER , el equipo arrancó correctamente, pero entrando a Gparted veo que sda pasa a ser el último disco o sea el IDE, por lo que mi disco original pasó a ser sdb , la pregunta es si habrá alguna manera de lograr que el disco sata vuelva a ser sda , ojalá sea posible evitasrme la tarea de tener que destapar el equipo para poner el DD pata como esclavo.

---

### Post by z37a on 2011-05-05
> **EnriqueK said:**
> Tenía mi equipo con un DD sata y era reconocido como sda, le instalé un DD IDE o PATA y no me di cuenta que el mismo estaba seteado como MASTER , el equipo arrancó correctamente, pero entrando a Gparted veo que sda pasa a ser el último disco o sea el IDE, por lo que mi disco original pasó a ser sdb , la pregunta es si habrá alguna manera de lograr que el disco sata vuelva a ser sda , ojalá sea posible evitasrme la tarea de tener que destapar el equipo para poner el DD pata como esclavo.

Es un problema muy común, pero fijate que de seguro el fstab debería estar seteado para usar UUID en vez de los nombres de dispositivos, el UUID no cambia nunca, así que pro mas que tengas sda o sdb si te manejas por UUID no vas a tener problemas.

---

