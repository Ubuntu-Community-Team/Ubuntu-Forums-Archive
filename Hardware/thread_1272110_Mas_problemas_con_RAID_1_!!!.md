---
title: "Mas problemas con RAID 1 !!!"
date: 2009-09-21
forum: Hardware
---

### Post by matixslp on 2009-09-21
Amigos,
esto no es un post duplicado!!!
El post anterior pregunte sobre los permisos de carpetas en un raid montado sobre VMware. Pero lo que no me percate es que el raid desaparecio (se degrado).
Segui la guia ubuntu para configurar el raid bajo Vmware, me quedo hermoso, se monto y todo, pero al reiniciar la pc, se desmonto y me fue imposible ponerlo a andar nuevamente.
Estos resultados no me ayudan a animarme a poner un file server en raid1 en casa.
Aca les pongo la salida de la consola luego de reiniciar (antes de reiniciar todo andaba bien)
[COLOR=Red]Cualquier ayuda es bienvenida!!![/COLOR]
p.d> tengo el teclado en ingles -acentos omitidos y faltas de ortografia deliberadamente al azar



```
 tute@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdc1[1](S)
      1044096 blocks
       
unused devices: <none> 
```

```
tute@ubuntu:~$ sudo mdadm --query /dev/md0
/dev/md0: is an md device which is not active
```

```
tute@ubuntu:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```

```
tute@ubuntu:~$ sudo mdadm --query /dev/sdb1
/dev/sdb1: is not an md array
/dev/sdb1: device 0 in 2 device undetected raid1 /dev/md0.  Use mdadm --examine for more detail.
```

```
tute@ubuntu:~$ sudo mdadm --query /dev/sdc1
/dev/sdc1: is not an md array
/dev/sdc1: device 1 in 2 device undetected raid1 /dev/md0.  Use mdadm --examine for more detail.
```

El /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=23f264a5-af24-45ef-a880-00e4efd02988 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=03b935ec-59ee-484a-a33a-8c49f3eac766 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0    /home/tute/raid    ext3    defaults,user 0 0
# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software
```

El mdadm.conf

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 21 Sep 2009 15:11:38 -0700
# by mkconf $Id$
```

---

### Post by Mister X on 2009-09-22
leí tu otro post, yo te recomendaría instalar el servidor de archivos en la maquina fisica (no virtualizado), si es que no necesitás el windows para otra cosa

después te posteo un tutorial de como instalar un RAID 1 (no lo tengo acá), a mi me sirvió, es muy sencillo

---

### Post by matixslp on 2009-09-22
> **Mister X said:**
> leí tu otro post, yo te recomendaría instalar el servidor de archivos en la maquina fisica (no virtualizado), si es que no necesitás el windows para otra cosa

después te posteo un tutorial de como instalar un RAID 1 (no lo tengo acá), a mi me sirvió, es muy sencillo
Misterx,
el raid lo instale sin problema pero luego se degrado, supongo que debe ser por la virtualizacion.
en esta semana me consigo un p3 con hd de 10 gb para pruevas!
despues te cuento.

---

### Post by Jorge Mario Tobar Frosoni on 2010-01-19
Tu estás teniendo problemas con el raid md_d0 que no es el que montaste como md0

debes parar este raid con:
sudo mdadm --stop /dev/md_0
  	 	 	 	 	
luego forzar al raid md0 a rearmarse:
sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1
pon tus dispositivos al final (yo pongo aquí dos que creo que lo conforman)

finalmente monta nuevamente tu raid md0:
sudo mount -t tipo_de_fichero /dev/md0
ejemplo: sudo mount -t ext4 /dev/md0

Ocurre que otro dispositivo raid (md_d0) te toma el sdc1 por no se que motivo y no deja rearmar tu raid md0

---

### Post by selpoivre on 2010-10-07
No recomiendo usar RAID 1 para un server.  Para esos casos utiliza un RAID 5 o RAID 10.
 
Son configuraciones idoneas par los servidores, en cambio el RAID 1 es mejor para un ordenador.
 
Si tienes planeado manejar un gran volumen de datos en tu server, mejor que mantengas un respaldo de toda esa data ya que ninguna configuracion RAID es 100% segura.  Y si te pasa que pierdes el acceso a la informacion, ya sea por una falla fisica de uno o mas discos, entonces tendras que pedir ayuda a alguna de esas empresas que se dedican a recuperar datos.  
 
Las que conozco son ONRETRIEVAL, RECOVERY LABS y ONDATA.
 
 
Saludos.

---

