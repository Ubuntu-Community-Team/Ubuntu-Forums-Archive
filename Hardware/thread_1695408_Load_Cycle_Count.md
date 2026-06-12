---
title: "Load Cycle Count"
date: 2011-02-25
forum: Hardware
---

### Post by fgl82 on 2011-02-25
Hola,

les hago una consulta. Consciente del problema de rapido aumento del load cycle count que alguna vez tuvo ubuntu al correr en laptops alimentadas a bateria (sin estar conectadas), decidi chequearlo en mi netbook, una hp mini 210.

Corri el comando:

sudo smartctl -a /dev/sda | grep 193

lo cual arroja la linea relacionada con el load cycle count.

Ahora bien, noto que este numero se incrementa de  1 o 2 por minuto, a veces mas.

¿Es esto normal? 

Encontre fixes en internet, pero soy consciente de que poner hdparm con un valor de 255 o 254 hace que nunca se "estacione" el cabezal y no esta protegido el disco de la notebook al moverla.

Aparte, como les digo, no estoy seguro de que este mal el incremento, por eso les consulto.

Gracias


edit: si corro el comando:

sudo hdparm -I /dev/sda | grep -i "Advanced power management level"

me da que esta en 128 y si aplico la solucion encontrada aca:

[http://ubuntuforums.org/showthread.php?t=1605416](http://ubuntuforums.org/showthread.php?t=1605416)

el problema parece desaparecer pero, una vez mas, me preocupa la proteccion del rigido en movimiento.

---

### Post by fgl82 on 2011-02-27
Bump

---

### Post by fgl82 on 2011-03-03
(con cara de vergüenza): bump?

---

### Post by guillermolisi on 2011-03-03
:D Parece que el unico preocupado por este tema sos vos.

---

### Post by fgl82 on 2011-03-04
jajaja si, pero no debería ser así, seggún cuentas que hice no era un buen ritmo de aumento! Hubiera matado el rigido en un año y medio si tomamos en cuenta los 300000 que listan en varios lados como medida de quiebre en cuanto a estos load cycles

---

