---
title: "¿Qué Sistema de Archivos Usar en un Disco Duro Externo?"
date: 2009-08-16
forum: Hardware
---

### Post by daggaz on 2009-08-16
Hola.
Tengo un nuevo Disco Duro Externo de 1 Terabyte y quiero darle un formato para guardar archivos que voy a compartir en diferentes S.O. pero que básicamente trabajaré en Ubuntu (tanto lectura como escritura).
Busqué información en Google sobre cuál era el mejor Sistema de Archivos para utilizar en Ubuntu; si Fat32 o NTFS; parece que el primero tiene una gran fragmentación de escritura y el segundo no sé si aún tiene muchos problemas para ser trabajado desde Linux. Las opiniones y consejos son muy diversos y no hay mucha información concreta.
¿Qué sistema de archivos me aconsejarían utilizar? El disco lo usaré para cargar Audio y Video, por lo que en muchos casos sí trabajré con archivos muuuy grandes (de hasta 100Gb). El formato se lo daré con *Gparted*.
Gracias.

---

### Post by staar on 2009-08-17
de primera, si vas a trabajar con archivos grandes, descartá FAT32, porque no soporta archivos de más de 4 GB, después, si necesitás usar el disco con Ventanas, entonces lo único que te queda es NTFS, lamentablemente es el único filesystem que funciona nativamente en aquel SO (otros funcionan, pero necesitan de herramientas de terceras partes, y ya sabemos como son las cosas con ellas en Ventanas, sobre todo con partes tan importantes como los filesystems, aparte de incomodidad de instalarlas en cada máquina con la que quieras usar el HD), en ubuntu también funciona excelentemente y out-of-the-box, los problemas que había ya fueron solucionados hace mucho...

saludos

---

### Post by daggaz on 2009-08-18
Muy bien : >
¡Gracias!

---

### Post by sebastianabate on 2009-08-23
Lo que tenés que tener en cuenta es que el acceso a particiones NTFS en Linux es considerablemente más lento que a cualquier otro filesystem nativo (como ext3 o reiserfs), y además usa bastante más procesador.
Lo mismo te va a pasar si usás ext3 en el disco y lo montás en Windows con ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/))

---

