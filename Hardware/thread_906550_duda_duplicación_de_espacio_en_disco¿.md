---
title: "duda duplicación de espacio en disco¿?"
date: 2008-08-31
forum: Hardware
---

### Post by Barasuishou on 2008-08-31
hola, bueno esto es simplemente una duda a ver si alguien sabe algo, mi disco se supone es de 150 gibs, o eso decía en win, ahora en ubuntu, me tira que tengo el doble de eso, puede ser esto?, es un error, es algo que suele hacer ubuntu, o el formato ext3 permite mayor espacio en disco??, bueno a ver si alguien sabe algo :p, me despido chauuuuu

---

### Post by Kantier on 2008-08-31
erm... por ahi tenés un disco más grande y en windows tenías una partición que no ocupaba todo el disco.

si tirás "sudo fdisk -l" (lo que tira una lista de los discos y particiones en tu computadora) en la consola y copiás acá lo que te tire seguro que cualquiera de los que tenemos algo de idea te va a poder ayudar :)

---

### Post by Barasuishou on 2008-08-31
Disco /dev/sda: 164.6 GB, 164696555520 bytes
255 cabezas, 63 sectores/pista, 20023 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x57fb57fb

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959       20023   145107112+   5  Extendida
/dev/sda5            1959       19648   142094893+  83  Linux
/dev/sda6           19649       20023     3012156   82  Linux swap / Solaris

bueno acá está como me dijiste, por lo qeu reconozco ahí dice que mi disco es de 164, pero el analizador de uso en disco me tira otra cosa, si quieren le saco una foto y les muestro :S

---

### Post by villa77 on 2008-09-01
En el analizador de uso de disco anda a Editar-Preferencias y destildá el dispositivo gvfs-fuse-daemon y ahí te lo va a mostrar correctamente.
Saludos.

---

