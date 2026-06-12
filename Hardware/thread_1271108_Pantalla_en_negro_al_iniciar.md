---
title: "Pantalla en negro al iniciar"
date: 2009-09-20
forum: Hardware
---

### Post by akiestudio on 2009-09-20
Hola buenos dias, el problema es, que sale la pantanlla en negro con un guio en blanco al iniciar el laptop y despues de que salga la barra de carga de ubuntu....he leido varios post , pero no consigo entrar en el terminal...

He hecho Ctr + alt + f1, Ctr + alt + f2. Ctr + alt + +, Ctrl + alt + -, como he leido en varios post y nada , 

Tambien he intentado en modo recovery y nada,

Alguna ayuda desesperadamente , no hay manera de que esto arranque en modo recovery sale lo siguiente:

kinit :no resume image doing normal boot
[3697076] Ext3-fs: info ; Recovery required ir readonly find system 
[mas numeros] Ext3-fs:writte : access will be enable during recovery

Uso Ubuntu 9.04 .
Laptop . Tarjeta grafica es una radeom 2400   

Alguna ayuda

---

### Post by gmunioz on 2009-09-20
Hola aki.....:

Inicia con el live-cd

En una consola (Aplicaciones - Accesorios - Terminal)

Ejecuta:

```
sudo fdisk -l
```

Esto te dará una salida parecida a esta:

```
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0007763c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1945    15623181   83  Linux
/dev/sda2            1946       19457   140665140    5  Extendida
/dev/sda5            1946        4255    18555043+  83  Linux
/dev/sda6            4256        4377      979933+  82  Linux swap / Solaris
/dev/sda7            4378       19457   121130068+  83  Linux
```

A todas las particiones que tengas identificadas con Id 83 Sistema linux

le corres, previo desmontarlas fsck, y lee con detenimiento los mensajes

por si debes ejecutar algo sugerido por el comando fsck

Por ejemplo, para /dev/sda1

```
sudo umount /dev/sda1
```

```
sudo fsck /dev/sda1
```

Desmonta y repara, respectivamente

---

### Post by akiestudio on 2009-09-20
Gracias no se que hice pero consegui arrancarlo , 

Es posible hacerlo ahora eso de desmontar y reparar sin usar el cd live?, porque no se si lo hago borrare algo...

Gracias

---

### Post by gmunioz on 2009-09-20
**No - No - No**

Nunca debes ejecutar fsck sobre una partición montada.

Corres el riesgo de perder todos los datos.

El procedimiento mas adecuado es hacerlo desde una

sesión live.

---

### Post by akiestudio on 2009-09-20
Asi que hago esas pruebas con el  live....o ya no me hace falta, aunque a lo mejor hay algun daño ...?
Si lo hago con una sesion live no perderia los datos?

---

### Post by gmunioz on 2009-09-20
Hola:

Te sugiero respetes el dicho popular

***"¡¡Si te funciona no lo toques!!"***

---

