---
title: "se corta instalacion de ubuntu en 90%"
date: 2009-08-24
forum: Instalación y Actualización
---

### Post by lricardorl on 2009-08-24
Hola!, un cordial saludo a todos.

Primeramente tengo una maquina optiplex 170L con cpu P4 de 3.0 ghz, 1.5 gb de ram y 1.2 gb de swap, disco duro de 250 gb.Tengo el disco particionado de la siguiente manera:

sk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1df21df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       27970   182723310    f  W95 Ext'd (LBA)
/dev/sda5            5223        7572    18876343+   7  HPFS/NTFS
/dev/sda6            7573       16710    73400953+   7  HPFS/NTFS
/dev/sda7           16711       16971     2096451    b  W95 FAT32
/dev/sda8           16972       22192    41937651    6  FAT16
/dev/sda9           22193       22354     1301233+  82  Linux swap / Solaris
/dev/sda10          22355       23225     6996276   83  Linux
/dev/sda11          23226       24034     6498261   83  Linux
/dev/sda12          24035       25128     8787523+  83  Linux
/dev/sda13          25129       25999     6996276   83  Linux
/dev/sda14          26000       27119     8996368+  83  Linux
/dev/sda15          27120       27970     6835626   83  Linux

Mi problema es el siguiente: no puedo instalar ubuntu en cualquier partición que no este pegada a la swap o a la ultima partición windows (sda7), sda8 es espacio vacio.  La cuestión es que pude instalar una versión modificada de ubuntu, pero despues trate de instalar ubuntu en la siguiente(o cualquier) partición (diferentes versiones y deribados también), y se corta al 90% :| , no da ningun mensaje (ni registro) solo se interrumpe, tanto en español, como en las opciones por defecto . Cabe señalar que pude instalar diferentes distribuciones Linux en las demás particiones sin problema. He instalado Linux desde hace tiempo (he tenido algunos problema que he resuelto) pero nunca me habia pasado algo parecido, lei documentos tecnicos de ubuntu de particionado y sistema de archivos ,así como en foros donde dicen que ubuntu se conecta a internet para descargar paquetes: si lo hace, descarga y después se corta la instalación, usando alguna de la distribuciones veo la partición donde quedo instalada y esta todo, solo que faltan dispositivos en la carpeta /dev y algunos archivos de configuracion. Es un bug de ubuntu? parece que no puede coexistir con otras distribuciones, sino se instala primero  :( . 

Ojala puedan ayudarme. No quisiera concluir que ubuntu tiene un bug de ese tipo:|:(. Como nota revise los tests de todos los ubuntu que use.

---

### Post by Patriciologico on 2009-08-31
Respecto a dos ddudas que planteas:

1.- Si puede coexistir con otros SO

2.- No necesita ser instalada en un orden preestablecido.

¿Has probado que la particion no este dañada?

¿y si instalas sin conexion a internet, saltandote ese paso?

Saludos!

---

