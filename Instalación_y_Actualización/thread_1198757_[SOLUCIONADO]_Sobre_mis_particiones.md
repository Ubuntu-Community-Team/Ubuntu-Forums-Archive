---
title: "[SOLUCIONADO] Sobre mis particiones"
date: 2009-06-27
forum: Instalación y Actualización
---

### Post by AlvaroV on 2009-06-27
Corri un fdisk L  y aprece esta frase repetida varias veces. ¿Alguien me puede decir que significa?

"La partición 3 tiene distintos principios físicos/lógicos (¿no Linux?)"

---

### Post by kamus on 2009-06-27
Cual es el esquema de tus particiones?, digo cuantas particiones primarias / logicas extendidas tienes y como estan asignadas?, lo otro seria que revisaras el man fdisk para buscar mas info al respecto.

Saludos

---

### Post by moreback on 2009-06-27
Seguramente es una inconsistencia en el particionado de un disco. ¿Qué es lo que sale con **fdisk -l**?

---

### Post by AlvaroV on 2009-06-28
> **moreback said:**
> Seguramente es una inconsistencia en el particionado de un disco. ¿Qué es lo que sale con **fdisk -l**?

Sale:

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x028b028b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1098     8819653+  83  Linux
/dev/sda2            1099        1565     3751177+  82  Linux swap / Solaris
/dev/sda3            1566        4998    27575572+  83  Linux

---

### Post by Carlos C on 2009-06-29
Prueba escanear el sistema de archivos. La partición no puede estar montada, así que tienes que usar el live cd para entrar a una sesión. Al hacerlo consigues entrar a Ubuntu sin montar las particiones. Prueba correr e2fsck:
```
e2fsck /dev/sda3
```

Puedes encontrar más información acá:

[http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html](http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html)

---

### Post by moreback on 2009-06-29
> **AlvaroV said:**
> Sale:

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x028b028b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1098     8819653+  83  Linux
/dev/sda2            1099        1565     3751177+  82  Linux swap / Solaris
/dev/sda3            1566        4998    27575572+  83  Linux

¿Seguro que es en este disco donde se da el problema? ¿Podrías dar el listado completo que da **fdisk -l** o ese que pusiste es? Es que me huele a que es otro disco, posiblemente un pendrive.

Saludos.

---

### Post by AlvaroV on 2009-07-02
Gracias por la colaboración pero realice desde un Live Cd un chkdisk yparece que todo se arreglo porque no me aparece nada raro.

---

### Post by Carlos C on 2009-07-02
¿Damos el tema por solucionado?

---

### Post by AlvaroV on 2009-07-03
Si señor moderador puede dar el tema por soluciado.

---

