---
title: "Problema con lector de memorias USB"
date: 2009-09-17
forum: Hardware
---

### Post by anarko on 2009-09-17
Hola gente tengo un problema con un card reader de esos que se ponen en la bahia de 3 y 1/2 y se enchufan al USB del mother. 
El problema es que cuando inserto una memoria para lerr queda haciendo esto:
```
[  497.521048] sd 4:0:0:3: [sde] Spinning up disk....<5>sd 4:0:0:3: [sde] Spinning up disk....<5>sd 4:0:0:3: [sde] Spinning up
disk.......<5>sd 4:0:0:3: [sde] Spinning up disk.........<5>sd 4:0:0:3: [sde] Spinning up disk.....<5>sd 4:0:0:3: [sde] Spinning up
disk....<5>sd 4:0:0:3: [sde] Spinning up disk......<5>sd 4:0:0:3: [sde] Spinning up disk.....<5>sd 4:0:0:3: [sde] Spinning up disk.....<5>sd
4:0:0:3: [sde] Spinning up disk.....<5>sd 4:0:0:3: [sde] Spinning up disk.........<5>sd 4:0:0:3: [sde] Spinning up disk.........<5>sd 4:0:0:3:
[sde] Spinning up disk..........<5>sd 4:0:0:3: [sde] Spinning up disk.........<5>sd 4:0:0:3: [sde] Spinning up disk......<5>sd 4:0:0:3: [sde]
Spinning up disk.....
```

Queda asi todo el tiempo.
Esto es lo que tengo yo:
Ubuntu 9.04 
Kernel 2.6.28-15-generic #49-Ubuntu SMP ( tambie pasaba con los kernels anteriores )

El card reader funciona 10 puntos si levanto la pc con un live del 8.04 asi que asumo que no es problema de hard sino de soft.

Saludos.

---

### Post by josecuervo86 on 2009-09-17
podrias postear el resultado de correr **lsusb** en terminal?

---

### Post by anarko on 2009-09-17
Si como no: 
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1019:0c55 Elitegroup Computer Systems (ECS) USB Flash Reader, Desknote UCR-61S2B
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
El aparaejo en custion es el unico que se enumera en el lsusb.

---

### Post by anarko on 2009-09-17
-- Sory doble post, se me chiflo la coneccion de inet. --

---

### Post by josecuervo86 on 2009-09-17
Por casualidad no estas intentando montar una tarjeta XD no?

---

### Post by anarko on 2009-09-21
No no, una M2, ya lei sobre los problemas de las XD.

---

### Post by anarko on 2009-09-22
up

---

