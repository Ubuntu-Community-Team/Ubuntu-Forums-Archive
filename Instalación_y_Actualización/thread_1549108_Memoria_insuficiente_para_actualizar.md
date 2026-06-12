---
title: "Memoria insuficiente para actualizar"
date: 2010-08-09
forum: Instalación y Actualización
---

### Post by capcabgue on 2010-08-09
Hola:

Les cuento estoy tratando de actualizar desde la 9.10 a la 10.04 (tengo un DELL Inspiron 1525, compartiendo windows y ubuntu el disco). 
Las particiones de ubuntu que tengo son 10 GB para /, 2 para SWAP y como 125 para home. Cada sistema y partición funciona muuy bien.
Mis problemas comienzan al tratar de hacer el upgrade, me indica el gestor lo siguiente:
**"Not enough free disk space**
The upgrade is now aborted. The upgrade needs a total of 1,669M free space on disk '/'. Please free at least an additional 63.1M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'. "

Hice un clean, autoclean y remove y nada me sigue dando el mismo error (me liberó algo de espacio, pero aún tengo problemas). Vi las particiones y estas son

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5727    45898437+   7  HPFS/NTFS
/dev/sda3            5728        6972    10000462+  83  Linux
/dev/sda4            6973       38913   256566082+   5  Extended
/dev/sda5           38665       38913     2000092+  82  Linux swap / Solaris
/dev/sda6            6973       33800   215495847   83  Linux
/dev/sda7           33801       38663    39062016    b  W95 FAT32

Y estos son los porcentajes de uso que tienen las particiones:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              9843308   7564292   1778996  81% /
udev                   1541276       352   1540924   1% /dev
none                   1541276       932   1540344   1% /dev/shm
none                   1541276       340   1540936   1% /var/run
none                   1541276         0   1541276   0% /var/lock
none                   1541276         0   1541276   0% /lib/init/rw
/dev/sda2             45898432  23634332  22264100  52% /windows
/dev/sda6            212112884  76647880 124690212  39% /home
/dev/sda7             39052448  16066528  22985920  42% /dos

Mis dudas son 4:
- ¿Cómo libero el espacio necesario sin después tener problemas con las particiones?, en especial las de guin2, que las necesito por compatibilidad con mi celular (un nokia) y con un ipod shuffle.

- Finalmente ¿cómo arreglo eso que los limites de la partición 1 no terminan en cilindro?

- ¿Esto de los límites significa una pérdida de desempeño, capacidades u algo del notebook?

- Cómo se puede redimensionar los espacios sin tener problemas posteriores , ya una vez me pasó que tuve que reinstalar todo)?

Gracias  por la ayuda y si necesitan cualquier otra información me avisan

---

### Post by EnriqueK on 2010-08-20
Haz lo siguiebte
1.- Borra la papelera oculta de root
**sudo rm -Rf /root/.local/share/Trash**
No importa que se borre inclusive la papelera ya que se vuelve a regenerar cuando haga falta
Como tienes mucho espacio disponible en /home , mueve allí el caché de paquetes descargados mediante
**sudo mv /var/cache/apt/archives /home**
seguidamente creas un enlace simbólico en el sitio original que apunte a la nueva ubicación, mediante 
**sudo ln -s /home/archives /var/cache/apt**

---

