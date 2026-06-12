---
title: "preguntita cdrom"
date: 2008-07-12
forum: Hardware
---

### Post by katon on 2008-07-12
hola como va gente les hago una consulta ...tengo en la laptop con xubuntu de un dia para el otro no funciona el cdrom , osea, como que se desmonto . cuando intento montarlo me dice que falta el "type"  se refiere a el tipo de sistema de archivos?
como harian para montarlo al cdrom normalmente?
gracias

---

### Post by Hei Ku on 2008-07-12
postea tu archivo /etc/fstab

---

### Post by excaliburs on 2008-07-13
Algo parecido a esto tenes que ver en ese archivo
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2caadfa6-ff07-42af-9584-c286fdb9c0f4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



y esta en el directorio que te marco Hei Ku
Saludos

---

### Post by Mauro22 on 2008-07-13
> **excaliburs said:**
> 
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



Un hd como cd-rom ??


Yo tengo scd0   :confused::confused:

---

### Post by Hei Ku on 2008-07-13
si el cdrom es ide, te aparece como hda o hdb. si es scsi, como sda, sdb, etc.

por eso lo mejor es ver el archivo fstab, y de ahi corregirlo.

---

### Post by katon on 2008-07-26
este ese mi archivo, disculpen que demore mucho es que no estuve por la computadora....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c98cf8f6-dc72-4916-9d37-ebbdbeab0b0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=43ecace9-5961-4dff-b675-54f8d1637848 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by katon on 2008-07-27
alguien por ahi???

---

### Post by Hei Ku on 2008-07-27
el fstab parece estar bien. Por lo que veo tenes 2 cdroms. Tenes problemas con los dos?

Que sucede si en la consola pones: sudo mount /media/cdrom0

Postea el error completo.

---

### Post by katon on 2008-07-27
mati@laptop-mati:~$ sudo mount /media/cdrom0
[sudo] password for mati: 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Esto es de la Laptop que tiene 1 cdrom y me pasa lo mismo tambien con Xubuntu.
ahi te escribi el error que tira cuando pongo eso

---

### Post by Hei Ku on 2008-07-27
es raro, porque tu fstab aparece como si tuvieras 2 cdroms.

pone este comando y postea el resultado: 

```

sudo lshw -class disk

```

---

### Post by katon on 2008-07-28
les reitero que ahora estoy en mi laptop con 1 CDROM en la cual tengo el mismo problema , 
ahi va el /fstab y luego el comando 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dc8bb38c-4799-4c4a-98f0-5aa17bb0152f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0b8acfc4-3fb7-4bef-bbde-2c392b4646ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by katon on 2008-07-28
mati@laptop-mati:~$ sudo lshw -class disk
[sudo] password for mati: 
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK1214GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: N0.1
       serial: 40310285G
       size: 11GiB (12GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000adab9
  *-cdrom
       description: SCSI CD-ROM
       product: CD-224E
       vendor: COMPAQ
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9.0B
       serial: COMPAQ  CD-224E         9.0B
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: 0BB-00FJA0
       vendor: WDC WD80
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 00
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=bb84bb84

---

### Post by katon on 2008-08-02
che alguien vio lo que postie ?

---

### Post by Hei Ku on 2008-08-02
Que pasa si pones:

sudo mount -t iso9660 /dev/cdrom0 /media/cdrom0

---

