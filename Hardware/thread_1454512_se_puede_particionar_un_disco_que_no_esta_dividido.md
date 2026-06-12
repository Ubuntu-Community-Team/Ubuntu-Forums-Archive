---
title: "se puede particionar un disco que no esta dividido?"
date: 2010-04-14
forum: Hardware
---

### Post by p3rdid0 on 2010-04-14
Español:

Hola mi duda es la siguiente, tengo mi disco duro con ubuntu y no esta particionado esta totalmente con ubuntu, y quisiera hacer una particion con el espacio que me queda... pero no quiero formatear ni nada...  sera posible?

ojala respondan bie!

English!

can partition a disk that is not divided?

Hi my question is this, I have my hard drive with ubuntu and partitioning is not entirely with ubuntu, and I have one partition with the space I have left ... I do not want to format or anything ... be possible?

BIE hopefully respond!

---

### Post by hackb0y294 on 2010-04-14
English dude, English!

---

### Post by bichopro on 2010-04-14
Estas en el foro de chile y puede preguntar en español sin problemas es otro el que anda perdido.

Solo solo instala gparted y dale resize a tu particion luego crea la otra y listo, hay varios manuales en internet, es grafico y facil, se demora bastante por lo de mover los archivos pero por lo menos para mi ha sido bastante seguro.

---

### Post by p3rdid0 on 2010-04-14
ya me habia metido al gparted pero me aparece /dev/sda1 el que me imagino es mi disco que esta con toda mi memoria pero me aparece tambien /dev/sda2 que se llama extended y con subdivicion dev/sda5 llamado linux-swap, estos dos adicionales que veo tienen 2.5 gigas cada uno .... la cosa es que arriba en el menu pongo dispositivo y luego crear tabla de particiones, y me sale un advertencia que se me borraran todos los datos en el disco entero dev/sda y no quiero perder mis datos solo quiero dar cierta memoria para instalar un xp por el problema del autocad ¬¬

---

### Post by Carlos C on 2010-04-14
ok, amigo, necesitamos mayor claridad sobre la situación de tu disco para responderte. Por favor, escribe en el terminal:

```
sudo fdisk -l -u
```

Dices que Ubuntu no usa todo el disco, ¿estás compartiendo el disco con otro sistema?

Saludos.

---

### Post by moreback on 2010-04-17
yo lo haría con un LiveCD de Ubuntu para que puedas hacer los cambios en tu hdd de inmediato. La idea es reducir el tamaño de alguna partición y luego empezar a moverlas para acomodar el espacio y finalmente crear la partición para Windows.

---

