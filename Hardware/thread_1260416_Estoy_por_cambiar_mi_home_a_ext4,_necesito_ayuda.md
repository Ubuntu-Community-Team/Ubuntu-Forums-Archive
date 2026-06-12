---
title: "Estoy por cambiar mi home a ext4, necesito ayuda"
date: 2009-09-07
forum: Hardware
---

### Post by guisheca on 2009-09-07
Que tal comunidad, dado las bondades que he oído del sistema de ficheros ext4 he decidido dar el salto y actualizar mis particiones a dicho formato.

Pero tengo un dilema. Mi home tiene 1 y 1/2 años de uso y nunca se modificó, consta de 138 Gb y tiene info muy importante que no quisiera que se pierda o modifique. Y cuando me refiero a información importante, me refiero a configuraciones de programas, charlas en distintos sistemas de mensajería (que son oro puro jejeje), y por último lo que puedan ser videos, música, y trabajos de la facu, etc.

Esta es la salida de mi fdisk -l:

```
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8ed28ed2

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        3945    31688181   83  Linux
/dev/sda2            3946       23856   159935107+   5  Extendida
/dev/sda3           23857       30312    51857820   83  Linux
/dev/sda4           30313       30401      714892+  82  Linux swap / Solaris
/dev/sda5            3946       21448   140592816   83  Linux
/dev/sda6           21449       23856    19342228+  83  Linux

```

En sda1 tengo ubuntu, en sda6 archlinux, en sda5 el home, en sda4 el swap y en sda3 estaba windows, pero el pobre se ha ido a dormir el sueño eterno en favor de que pueda hacer un respaldo de mis archivos jeje.

El asunto es que ya e organizado todo y en la partición de respaldo (antes windows) quisiera poner tal cual mi home y luego recuperarlo una ves hecho el formato en ext4 (obviamente he reducido el tamaño de los datos de mi home para que quepan en la otra partición. Conozco el comando dd, pero se que hay que tener cuidado por eso vengo a pedir ayuda.

En fin, lo que quiero hacer es pasar mi home a ext4 y que todos mis datos queden tal cual antes del proceso. Tengo espacio suficiente en mi disco para hacer el respaldo.

¿Que me aconsejan?

Saludos.

---

### Post by guisheca on 2009-09-07
Gente, verán, agarré el nautilus como root y empecé a copiar el home entero en la partición de respaldo. No se porque, pero hay archivos que no me deja copiar porque dice que no tengo privilegios!!! y estoy como root!!!

Alguien sabe a que se puede deber esto? la copia sigue igual, fueron un par de archivos los que tuve que decirle que ignore, pero en fin, todo sigue su curso.

Solo espero que esos archivos no sean de algo importante.

Saludos.

---

### Post by MC707 on 2009-09-07
bueno, lo que yo hice fue usar mi disco duro externo de 2 teras y lo pasé todo desde mi ext3. Formatee mi ext3 a ext4 y de vuelta los archivos a casa. Despues formatee mi disco de 2 teras a ext4 tambien y copie los archivos como respaldo. 

No estoy seguro sobre tu error de pasar archivos... quizas es porque tiene un sistema de archivos que no es bueno en manejar archivos grandes? (ext4 es bueno para eso :P)

salu2

---

