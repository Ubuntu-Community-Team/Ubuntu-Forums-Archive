---
title: "hardrive error"
date: 2008-10-29
forum: Hardware
---

### Post by francoarza on 2008-10-29
look i've installed ubuntu a few days ago, i've backed up my data from windows in an extra hardrive it was in NTFS format, but then i've formatted it into FAT32 and putted the files back into it, so then i thougt it should work, but when i try to mount the drives, the terminal says this:

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (¿no estará intentando montar una partición extendida,
       en lugar de alguna partición lógica que haya dentro?
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

please help me, i really need the information in the hardrive. thanks anyway. :)  i don't want to go back to windows.. because this would be the only reason i can't keep on using UBUNTU, i really like this OS, so i'd really apretiate any help you can provide me.

miren he insatalado ubuntu hace unos dias, la cosa es que hice un backup de mis datos en un disco duro que estaba en NTFS, lo formatie y pase a FAT32 volvi a meter mis archivos en ese disco duro y sin embargo ahora cuando trato de montarlo desde el terminal me dice lo siguiente:

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (¿no estará intentando montar una partición extendida,
       en lugar de alguna partición lógica que haya dentro?
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

por favor ayudenme pronto, porque realmente necesito esos archivos, desde ya muchas gracias :) no quiero volver a windows y este seria el unico motivo que me haria volver, me gusta mucho UBUNTU, por lo tanto apreciaria realmente cualquier ayuda que pudieran darme.**[B]**[/B]

---

### Post by Mauro22 on 2008-10-30
1) Bienvenido.

2) No te gastes en escribir en ingles porque no te van a dar bola.

3) La cosa es asi: Sin informacion no podemos ayudar. No tenemos donde empezar ni donde terminar.


Que comando pusiste?
Probaste con livecd // otros S.O.?
El disco es primario o logico?

> mount: wrong fs type 
Segun esto, le estas errando en el tipo de archivo de sistema (ntfs, vfat, etc)




Info, info y mas info...

---

### Post by clasificado on 2008-10-30
> **francoarza said:**
> la cosa es que hice un backup de mis datos en un disco duro que estaba en NTFS, lo formatie y pase a FAT32 volvi a meter mis archivos en ese disco duro 

Hoy en dia, gracias al trabajo de los muchachos de linux-ntfs, ntfs esta completamente soportado para lectura y escritura

Ese paso te lo pudiste haber ahorrado :D

clasificado

---

