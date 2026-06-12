---
title: "formateo de disco"
date: 2009-07-29
forum: Hardware
---

### Post by outsiders on 2009-07-29
hola, tengo un problema con uno de los discos rígidos (contiene solo archivos). Esto es lo que me tira el Hard disk sentinel. 
 
Failure Predicted - Attribute: 5 Count of sectors moved to the spare area. Indicate problem with the disk surface or the read/write heads. 
There are 1251 bad sectors on the disk surface. The contents of these sectors were moved to the spare area. 
The drive found 1 bad sectors during its self test. 
Based on the number of remapping operations, the health of the disk was decreased in different steps. 
There are 14 weak sectors found on the disk surface. They may be remapped any time in the later use of the disk. 
Replace hard disk immediately. 
 
Como hago para formatearlo en bajo nivel desde el ubuntu y darle luego formato ntfs? 
Muchas gracias.

---

### Post by Mauro22 on 2009-07-29
Nuevo o Viejo es disco??


Si es nuevo, no conviene darle bajo nivel.. Es más los lugares erroneos los "descuenta", asi que lo unico que pasa hasta ahora fue perder KBs... los clusters dañados se dan de baja..

---

### Post by outsiders on 2009-07-29
digamos que el disco tiene un año o dos. el tema es q no quiero q se escriban cosas sobre las partes dañadas. Es una pc en la q tengo xp y linux
bye

---

### Post by gmunioz on 2009-07-29
Hola out....:

El formateo de bajo nivel, que es el borrado total de 

la estructura magnética del disco duro, no es posible

practicarlo en los discos duros modernos, dado que su

estructura ha cambiado desde hace unos 10 años.

Algo similar, consistente en el borrado de todos los datos 

de todos los sectores del disco duro, para descartar los 

sectores defectuosos desde GnuLinux se puede hacer con el comando

dd

Previo desmontar el disco y desde el sistema, o en caso de un

disco duro único, desde una sesión live ejecutar:

sudo dd if=/dev/zero of=/dev/sdx bs=1M

Y tras un tiempo de formateo, dependiente del tamaño del disco duro

tendras el disco formateado simil bajo nivel.

---

