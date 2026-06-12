---
title: "nose como particionar"
date: 2009-06-25
forum: Instalación y Actualización
---

### Post by nagash93 on 2009-06-25
hola buenas

el problema es que lamentablemente deje mucho espacio para windows y ahora quiero agrandar la particion de ubuntu pero no puedo nose por que :(

aqui le dejo una imagen 

[[IMG]http://img341.imageshack.us/img341/3736/pantallazo1i.th.png[/IMG]]("http://img341.imageshack.us/i/pantallazo1i.png/")


aver si alguien me puedo decir 

muchas gracias

---

### Post by kamus on 2009-06-25
Debes redimensionar la partición pero no se puede hacer mientras esa partición este montada, creo que deberías poner el cd de ubuntu en modo live y hacerlo desde ahí con gparted aunque no te aseguro en un 100% que esto funciona ya que trabajar en la tabla de particiones es complejo y siempre lleva un riesgo que se debe asumir.

Saludos

---

### Post by nagash93 on 2009-06-25
aver voy a probar si funciona :cool:

ahi que arriesgarse no mas

---

### Post by gmunioz on 2009-06-25
Hola nag...:

No es que no sepas particionar, puede que no sepas,

es que **no puedes particionar**.

¿Por qué? Pues porque solo se pueden tener 4 particiones

primarias y ya las tienes:

/dev/sda1 /dev/sda2 /dev/sda3 /dev/sda4

¿Esto tiene solución?

Si

Según como lo veo tienes varias opciones:

1- Eliminar /dev/sda1, recovery incorporar el poco

espacio libre a /dev/sda2, reducir luego /dev/sda2,

crear una nueva partición /dev/sda1 para montarla como

/home/usuario/datos. No lo aconsejo. ¿Por qué? Pues porque

te llevaria mucho tiempo y es trabajoso, eliminar, incorporar,

disminuir, crear. Sin embargo tu decides.

2- Reducir /dev/sda2 directamente, incorporar el espacio liberado 

a /dev/sda3, con el espacio ganado hacer lo que te convenga

aumentar /dev/sda5, aumentar /dev/sda6, aumentar a ambas, crear una

nueva partición (lógica, lógicas son las creadas practicamente sin

límite de cantidad dentro de una extendida) para montar como 

/home/usuario/datos o como mas te guste. Esto sería lo que 

particularmente haria. Sin embargo tu decides.

3- Lo mismo, pero referido a /dev/sda4 eliminarla o reducirla y

utilizar segun conveniencia, depende de lo que tengas en esa partición.

Hagas lo que hagas, debes tener presente:

a- Ejecuta desde Windows defrag y chkdsk /f sobre la partición ntfs que

vayas a modificar.

b- Una vez modificada, ejecuta nuevamente chkdsk /f sobre ella

c- Las modificaciones se hacen desde una sesión live, con las

particiones desmontadas, teniendo instalados gparted y ntfsprogs.

d- Debes prever la posibilidad de que pierdas todos los datos, y poner

a salvo todo lo que no pueda ser reinstalado. Particularmente lo he

hecho cientos de veces sin perder datos, pero puede ser que en la

próxima los pierda a todos, asi **que resguarda los datos**

e- ¿Una swap de 3 gigas? En general con 1 giga sobra.

---

### Post by nagash93 on 2009-06-25
ok muchas gracias voy a seguir tu indicaciones

lo de la swap de 3 gb es que ley que tenia que ser segun la cantidad de ram que uno tuviese o no es asi?

---

### Post by gmunioz on 2009-06-25
Hola nag....:

La swap al doble de la ram, era cuando se tenia poca ram

ahora despues de un giga de ram, swap de 1 giga es suficiente.

Se me quedó en el tintero:

Si modificas particiones de Ubuntu, seguramente cambiará

su uuid

Esta se averigua en consola con el comando:

sudo vol_id /dev/sdax

Como en el archivo /etc/fstab las particiones

se montan ahora con uuid, tienes dos caminos

Desde la sesión live, una vez modificadas las particiones

montas / accedes a /etc/fstab y si las uuid cambiaron las modificas

o directamente reemplazas uuid por /dev/sdax 

x es el numero de partición.

Tambien deberás editar el archivo /boot/grub/menu.list y cambiar

el valor de la uuid, si modificas la partición /

---

