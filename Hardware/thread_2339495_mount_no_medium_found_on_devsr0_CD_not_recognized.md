---
title: "mount: no medium found on /dev/sr0 CD not recognized"
date: 2016-10-09
forum: Hardware
---

### Post by Rutrus on 2016-10-09
I didn't want comment in old posts, because this trouble happened in Xubuntu 16.04.1 LTS. I searched for a solution, and I didn't found any.
[B]
lsblk:[/B]
```
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom  

```

CD is in the device, but still is not recognized. I'm using Xubuntu based on: Ubuntu 16.04.1 LTS

```
sudo mount -t iso9660,udf /dev/sr0 /cdrom
```
shows:
```
mount: no medium found on /dev/sr0
```

**sr0** and **sr1** output is the same.

**lshw:**
```

     *-scsi:0
          id físico: 1
          nombre lógico: scsi0
          capacidades: emulated
        *-cdrom
             descripción: DVD-RAM writer
             producto: DVDRAM GSA-H44N
             fabricante: HL-DT-ST
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             versión: RB00
             capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuración: ansiversion=5 status=ready

     *-scsi:2
          id físico: 3
          nombre lógico: scsi3
          capacidades: emulated
        *-cdrom
             descripción: DVD-RAM writer
             producto: DVDRAM GH15F
             fabricante: HL-DT-ST
             id físico: 0.0.0
             información del bus: scsi@3:0.0.0
             nombre lógico: /dev/dvd
             nombre lógico: /dev/sr1
             versión: EG00
             capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuración: ansiversion=5 status=ready
           *-medium
                id físico: 0
                nombre lógico: /dev/dvd


```

---

### Post by deadflowr on 2016-10-09
It seems to be in the /dev/sr1 drive.
Or at least something seems to be there.

---

### Post by Rutrus on 2016-10-09
Both DVD-Writers are filled with CD and I can't mount anyone :(

---

### Post by Rutrus on 2016-11-28
Any suggestion?

---

