---
title: "Mi PC no arranca: System Halted"
date: 2009-10-24
forum: Hardware
---

### Post by Hadso on 2009-10-24
Hace rato que tengo Ubuntu 9.04. Todo anda a la perfección. 
Recién, apago el sistema con 
```
sudo halt
```

cosa que hago normalmente. Ahora cuando la prendo, comienza a bootear, me tira la info de que está leyendo el HD. Luego dice Starting up, y luego 

```
crc error
-- System halted

```

Cualquier tecla que apriete no hace nada... alguien me puede decir como hago para solucionar esto? 

Muchas gracias!!!

---

### Post by Hadso on 2009-10-24
Aclaro, arranca eligiendo la opción de la sesión anterior desde el GRUB, pero, quiero saber por qué pasa esto... 

GRACIAS!

---

### Post by guillermolisi on 2009-10-24
> **Hadso said:**
> Aclaro, arranca eligiendo la opción de la sesión anterior desde el GRUB, pero, quiero saber por qué pasa esto... 

GRACIAS!
Lo primero que haria es correr fsck porque ese error CRC puede tener origen en algun archivo corrupto.

Otra alternativa, tal vez algo mas lejana, es que el disco se este rompiendo.

Todo esto, a partir de la informacion que diste.

---

### Post by Hadso on 2009-11-04
Gracias por el dato. Al final es el disco. Luego de haber arrancado mi PC con la opción del GRUB de la sesión anterior, tuve que formatear. 
Despues del format, cuando actualizo, me doy cuenta de que no puedo bajar los archivos porque una de las librerías que tengo está dañada. 
Así, vuelvo a formatear y posteriormente a actualizar y me da el mismo problema en otra librería. 
En fin, conclusión, por 167$ al mes, tengo una PC nueva y muy buena. 
Gracias de todas maneras. 
Ya se puede cerrar este hilo. 
Saludos!

---

