---
title: "Disco duro de 1.5 Terabyte se colapsa"
date: 2010-07-15
forum: Hardware
---

### Post by ponchomx on 2010-07-15
Hola a todos, tengo un mes con un disco duro de 1 terabyte y medio y ahora que he llegado al terabyte, aun me quedan 400 gigas, el disco al intentar "escribir" sobre el simplemente deja de funcionar.

El disco lo uso para almacenar datos, el SO esta montado en otra unidad y no lo tengo particionado, esta montado como unidad lógica.

Con el programa de **Utilidad de discos** me dice que el **Estado de SMART** [COLOR="Green"]El disco está sano[/COLOR].

He probado con el comando **fsck** con los atributos -vpf y esto es lo que me arroja:

> 4850 inodes used (0.01%)
     144 non-contiguous files (3.0%)
       5 non-contiguous directories (0.1%)
         # de nodos-i con bloques ind/dind/tind: 0/0/0
         Extent depth histogram: 4182/642/16
224511432 blocks used (61.29%)
       0 bad blocks
     120 large files

    4497 regular files
     344 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
    4841 files


En la misma pc uso otros dos discos de un terabyte y están al 95% de capacidad y hasta ahora no han dado problema y su fluidez es excelente.

El sistema de archivos es **ext4** con ubunto **10.04**.

Mi Hardware:
Placa Madre: [A790GXM-AD3]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=957&CategoryID=1&DetailName=Feature&MenuID=19&LanID=0")
Procesador: AMD Phenom II X4 955
RAM: DDR3 2 Gigas a 1066

Como dato adicional el sistema de ficheros de los otros discos es también ext4. Y no tengo windows.

Salu2

---

### Post by ponchomx on 2010-07-15
Un dato adicional, cuando intento escribir el disco deja de funcionar, ya no puedo no solo escribir en el si no tampoco leer, si reinicio la pc al arrancar ubuntu me marca error y no lo monta, ni siquiera lo contempla en el programa dispositivos de almacenamiento.

Al cabo de unas horas o reconectando los cables de datos del disco nuevamente lo reconoce pero al intentar escribir el problema vuelve.

---

### Post by rojojuan on 2010-07-15
Fijate aquí:

[http://www.ubuntu.org.uy/main/node/2472](http://www.ubuntu.org.uy/main/node/2472)

---

### Post by ponchomx on 2010-07-15
Gracias por la información. Acabo también de descubrir que el disco duro que huzo tiene un negro historial. resulta que la empresa **Seagate** lanzo al mercado varios discos duros defectuosos, el mio parece ser uno de ellos. Bueno he actualizado el firmware y por lo pronto espero poder respaldar aunque sea parte de mis datos. si esto resulta bien espero seguir con los pasos que se mencionan en el enlace que me proporcionastes. 
Seguire informando.

Salu2

---

### Post by ponchomx on 2010-07-16
Pues dificil la cosa, de la pagina de Seagate resulta, que segun el modelo debo actualizar el firmware y según el No. de serie el firmware que tiene esta bien. Ta solo he podido respaldar parte de la información, un 15% y me tira el error:

**end-to-end-error**

Despues de eso tengo que esperar un buen rato o desconectar y volver a conectar el disco duro, de lo contrario ni el bios lo reconoce.

es una verdadera lastima, a un mes de estrenado. mañana voy por la garantía y les cuento.

;( no me resigno a perder mis datos.

---

### Post by rojojuan on 2010-07-16
Suerte con la garantía!
Es interesante saber que va a pasar. Espero noticias.

---

