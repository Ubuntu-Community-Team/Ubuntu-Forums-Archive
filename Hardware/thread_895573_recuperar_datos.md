---
title: "recuperar datos"
date: 2008-08-20
forum: Hardware
---

### Post by phxnd on 2008-08-20
voy a describir rapido mi problema asi tamos todos felices y contentos ^^, va, de un amigo

lo que paso es que "acidentalmente" formateo la memoria SD donde tenia unas fotos muy importantes, o nose si estaban en la memoria de la camara.¿Hay algun programa para poder recuperarlas? (osea hay, pero nose como se llama ^^ )

saludos gente

---

### Post by Lokkete on 2008-08-20
Mmmm perdon por lo q voy a poner q no es linux todo sea por sus datos.xD

Bue en linux no se que herramienta hay pero si te vas a un ciber que tenga win$$$ hay un soft q se llama getdatarecovery hay 2 uno para ntfs y otro para fat32 instalalos e intenta con eso, tarda su tiempo en escanear todos los clouters pero vale la pena si averiguo algo de linxu te lo pongo por aqui..

Si no estoy mal las memorias esas estan en fat32 por default bue eso lo ves tu...

a lo mejor puedes correrlo con wine, en su defecto calculo q deberá ser con sudo pero nunca lo intente no sabria decirte

---

### Post by sergiom99 on 2008-08-20
hay un utilitario que se llama photorec, esta en los repos.
Aca tenes la info. seguro te sirve.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Suerte!

---

### Post by phxnd on 2008-08-20
muchas gracais a ambos, voy a probar y despues les digo que onda

PD: igual tengo W$ en una particion chiqitita para alguna emergencia(??????) jajaja

---

### Post by sergiom99 on 2008-08-20
el photorec a mi me salvo la semana pasada que mi jefe borro su backup de PST (2 o 3 Gb) en una carpeta de samba en un FC7, y con ese comando pude recuperarla.

---

### Post by phxnd on 2008-08-21
> **sergiom99 said:**
> el photorec a mi me salvo la semana pasada que mi jefe borro su backup de PST (2 o 3 Gb) en una carpeta de samba en un FC7, y con ese comando pude recuperarla.

como se usa? conecto la cam, inicio el programa, selecciono la mem de la camm y que mas? xq hay una aprte que me pide seleccionar un directorio para nose que cosa

---

### Post by sergiom99 on 2008-08-21
creo q es el directorio a donde vas a restaurar los archivos recuperados. Mañana me fijo en el server de la oficina donde lo use y te digo.

---

### Post by sergiom99 on 2008-08-22
Bueno, asi arranca:
```
sudo photorec
```
> 1° Pantalla: elegís el medio a escanear (Enter)
2° pantalla: elegís el tipo de partición (Enter)
3° Pantalla: elegís la partición a escanear (Enter)
4° Pantalla: elegís el sistema de archivos de la particion a escanear (Enter)
5° pantalla: elegis donde va a buscar, ponele (Whole) (Enter)
6° pantalla: donde va a guardar los archivos que encuentre. aconsejan que sea en una unidad distinta a la que estas escaneando.  Lo elegis y apretas (Y) 
7° ahi arranca...

esto lo hice con la version: 
PhotoRec 6.10, Data Recovery Utility, July 2008

---

### Post by phxnd on 2008-08-28
> **sergiom99 said:**
> Bueno, asi arranca:
```
sudo photorec
```


esto lo hice con la version: 
PhotoRec 6.10, Data Recovery Utility, July 2008

muchas gracias ^^

k+

---

### Post by sergiom99 on 2008-08-28
salvaste las cosas?

---

### Post by noveou01 on 2009-01-16
Quien osa hablar de guindows aqui???????????

No dañemos el foro con eso

---

