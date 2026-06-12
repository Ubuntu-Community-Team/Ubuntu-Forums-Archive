---
title: "Cómo montar otro disco duro"
date: 2010-02-07
forum: Hardware
---

### Post by mano negra on 2010-02-07
Buenas,
  Esta vez les escribo por algo que nunca hice y quiero estar seguro. 
  Tengo un disco rígido suelto con windows (era de otra máquina), y lo que deseo es poder meterlo en la mía para sacar toda la info que hay ahí.
   Estuve leyendo por la web como se hace y me surgieron algunas dudas, que enumero:
- cuando tengo que indicar la partición en /dev/<partición>, no me queda mu claro cual es. Yo tengo en mi máquina de sda1 a sda6(una primaria para raíz, una swap y otra logica montada en home) , Le sigue sda7? El disco es SATA.
- creo que el formato es ntfs, pero como lo puedo corroborar?
- no me queda muy claro como se modifica el fstab, con sus opciones, más que nada por el sistema de archivos que tenga instalado.

Eso nomás.
Salud!

---

### Post by asterix77 on 2010-02-08
Para conocer el detalle de tus discos duros, debes ejecutar en consola lo siguiente:

sudo fdisk -l

El cual arrojará algo como:

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd8000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100        7041    15599115   83  Linux
/dev/sda3            7042        7296     2048287+  82  Linux swap / Solaris


Para el primer disco duro será sda, sdb para el segundo, etc. Ahora los discos pueden tener particiones las cuales se identifican con número. En el ejemplo el disco 1 posse tres de las cuales sda1  es una partición para mi home; sda2 es mi directorio raíz; y sda3 es mi memoria swap.

También puedes instalar gparted para tener esta misma información en forma gráfica.

sudo apt-get install gparted

---

### Post by mano negra on 2010-02-08
Gracias por el dato. Leyendo algo más me quedó un poco más claro, aunque sea lo básico. Una cosita más: cuando yo conecte el disco rígido, lo va a reconocer? Es decir, con gparted o fdisk voy a poder ver al disco nuevo que agregué físicamente y su ubicación?

---

### Post by majatu on 2010-02-15
Deberías de poder ver el disco apenas arranques la pc con ambos, gparted o fdisk.Igual como ya lo tenes con datos, una vez que lo conectes, arranca Ubuntu y fijate que ya lo vas a poder ver y montar desde el menu.

Saludos!

---

