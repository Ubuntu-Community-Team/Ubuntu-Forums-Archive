---
title: "Tener instalado 3 sistemas operativos"
date: 2010-11-03
forum: Instalación y Actualización
---

### Post by benja22 on 2010-11-03
Hola 
Quisiera saber si es posible tener instalados en 1 disco duro, en
5 particiones(15, 50 ,200, 20, 20) 3 sistemas operativos:
Fedora en un disco de 20 gigas
ubuntu o debian en un disco de 20 gigas
windows en un disco de 15 gigas
¿cual deberia instalarse primero, segundo y tercero?
¿instalo todos y despues instalo el GRUB?

saludos

---

### Post by Elkan76 on 2010-11-03
Si es posible tener tres sistemas operativos, en un solo disco, pero se debe tener ciertas precauciones.
Primero debes instalar Windows ya que si lo instalas después, vas a perder el GRUB ya que este es pisado en la MBR.
Luego instala Fedora y finalmente Ubuntu o Debian.

La única salvedad que deberás tener, es que el GRUB de Fedora deberás reeditarlo para que reconozca manualmente los kernel de Debian/Ubuntu (es una lata que deberás repetir con cada kernel update).

Creo que mejor alternativa, si tu RAM lo permite, es virtualizar Windows y una de las distros que desees (más te vale que sea Fedora la virtualizada jejeje :) ).

Saludos.

---

### Post by Patriciologico on 2010-11-03
Debes tener en cuenta también, que el máximo de particiones primarias son 4, si haces una extendida puedes hacer las particiones lógicas que quieras. Windows exige (o exigía antes al menos) una partición primaria para ser instalado. Linux aguanta todas las lógicas que quieras (no conozco el limite de particiones lógicas, seguro que mas de las que necesitas)

Saludos

---

### Post by benja22 on 2010-11-04
Muchas gracias a los 2, lo tomare en cuenta.


> (más te vale que sea Fedora la virtualizada jejeje  ).
Si virtualizara alguna, seguro seria fedora ;)

---

