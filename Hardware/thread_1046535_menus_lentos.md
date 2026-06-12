---
title: "menus lentos"
date: 2009-01-21
forum: Hardware
---

### Post by elgazeta on 2009-01-21
la situacion es la siguiente, tengo ubuntu 8.04, y en algun momento por alguna razon comenzo a suceder esto, que me ocurre en con todos los programas
supongamos el writer de openoffice, voy con el mouse a la pestaña de archivo y luego hago click en el menu de abrir... y tarda un monton en aparecer la ventana de dialogo
otro ejemplo
en el reproductor de musica para agregar una carpeta llena de mp3 tambien tarda en abrirse o luego de sacar un screenshot para guardar el archivo generado
no se que hacer por que si bien no es un problemon!! es incomodo y un poco molesto que me ocurra esto
digame que info hace falta y se las paso espero que lo pueda solucionar

---

### Post by Hei Ku on 2009-01-21
Supongamos que tu disco se llama sda, ejecuta lo siguiente:

```

sudo hdparm -Tt /dev/sda

```

Y postea el resultado.

---

### Post by guillermolisi on 2009-01-21
> **elgazeta said:**
> la situacion es la siguiente, tengo ubuntu 8.04, y en algun momento por alguna razon comenzo a suceder esto, que me ocurre en con todos los programas
supongamos el writer de openoffice, voy con el mouse a la pestaña de archivo y luego hago click en el menu de abrir... y tarda un monton en aparecer la ventana de dialogo
otro ejemplo
en el reproductor de musica para agregar una carpeta llena de mp3 tambien tarda en abrirse o luego de sacar un screenshot para guardar el archivo generado
no se que hacer por que si bien no es un problemon!! es incomodo y un poco molesto que me ocurra esto
digame que info hace falta y se las paso espero que lo pueda solucionar
Podrias pasar la composicion de tu PC (cantidad de memoria RAM, procesador, placa de video, etc.) ?

La memoria que se supone tenes instalada es el total de la que es reconocida por la PC ?
La fue fuente esta bien o calienta mucho ?
Y el ventilador de la CPU funciona bien ?
Tendras suficiente espacio en disco en las distintas particiones que utiliza el sistema operativo ?
Te fijaste si hay algun proceso que este consumiendo mucha CPU en todo momento ?

---

