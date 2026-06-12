---
title: "[SOLVED] FSCK failed"
date: 2008-05-25
forum: Hardware
---

### Post by madelaki on 2008-05-25
No me deja bootear Ubuntu, y sinceramente no tengo idea de lo que es un FSCK o de como hacerlo a mano.

"An automatic file system check (fsck) of the root filesystem failed. Manual fsck must be performed, then the system restarted"

---

### Post by jjgomera on 2008-05-25
si leyeras todo lo que pone en pantalla, a mi me suena ese error a este: [http://linexiando.blogspot.com/2007/10/fsck-da-cada-susto.html](http://linexiando.blogspot.com/2007/10/fsck-da-cada-susto.html)

y la solución es sencilla: sudo fsck -vy /dev/xxx 

pero claro, también puede ser otro, más o menos peligroso , depende del mensaje de salida "exit status x"

---

### Post by Mauro22 on 2008-05-25
FSCK es un "File System Check", vendria a ser como un Scandisk en windows.


Ahi te dice que tenes que correrlo manualmente. Es decir sin montar los discos.

Parra ello usa el live cd, y desde la consola pones 

fsck /dev/sda1 o el disco que sea en tu caso.

---

### Post by madelaki on 2008-05-25
> **jjgomera said:**
> si leyeras todo lo que pone en pantalla, a mi me suena ese error a este: [http://linexiando.blogspot.com/2007/10/fsck-da-cada-susto.html](http://linexiando.blogspot.com/2007/10/fsck-da-cada-susto.html)

y la solución es sencilla: sudo fsck -vy /dev/xxx 

pero claro, también puede ser otro, más o menos peligroso , depende del mensaje de salida "exit status x"

Gracias, ahora lo pruebo. Mauro22, HH lo instale con Wubi.

EDIT: Solucionado. Gracias jjgomera.

---

### Post by qubit67 on 2008-10-06
tnx man

---

