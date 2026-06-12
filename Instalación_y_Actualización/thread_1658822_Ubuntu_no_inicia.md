---
title: "Ubuntu no inicia"
date: 2011-01-03
forum: Instalación y Actualización
---

### Post by Maciett on 2011-01-03
Hola,

Estaba aprendiendo como correr un programa en ubuntu y como me demoré mucho, mi pareja dijo dejémoslo particionado con windows y ubuntu, y le dije bueno.

Redujo la partición de home y en el espacio que dejo trató de instalar windows, pero no lo deja y le dice que tiene que usar todo el disco, así que no lo dejé. 

Pero después cuando yo lo quiero usar no carga ubuntu...Él logró recuperar el grub, pero si selecciono cualquiera de las opciones de kernel me dice
```
Error 17: Cannot mount selected partition
Press any key to continue...
```No respaldé antes que hiciera esto, puesto que en otro pc hicimos lo mismo, dejarlo con windows y linux, sólo que habíamos instalado primero el SO privado.

Si alguien sabe como lo puedo arreglar, se lo agradeceré.

Saludos

---

### Post by moreback on 2011-01-03
Me parece que al reasignar el espacio se cambió la UUID a las unidades.

Creo que tendrías que entrar con el livecd y buscar la manera de cambiarselas por las correctas en tu /etc/fstab. (o podrías reescribirlo usando las unidades sin UUID como /dev/sda1, /dev/sda5, etc.)

Las UUID las puedes ver con **Gparted** haciendo clic en la partición y luego seleccionando **Información**.

Buena suerte.

---

### Post by Maciett on 2011-01-05
Menos mal que no fue eso. Ya lo arregló, les cuento cómo por si les pasa :S

Primero al recuperar el grub hay que hacer mención de en partición esta el sistema operativo en este caso era:
```
sda1/dev1     swap
sda1/dev2     ext
sda1/dev5     sistema operativo
sda1/dev      home
```Entonces cuando se edita el archivo del grub hay que decirle en que partición está (pero con el cuidado de que resta 1, por ej. el disco 2 se escribiría disco 1), por lo tanto la primera vez le había puesto que boteara 0h0, es decir disco uno, partición uno, pero esa es la swap y por eso no partía...

Luego lo editó de nuevo y le cambió a 0h4, disco uno, partición cinco y ahí si partió.

Saludos, y gracias por la ayuda moreback.

---

