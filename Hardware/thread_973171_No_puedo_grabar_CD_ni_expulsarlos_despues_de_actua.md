---
title: "No puedo grabar CD ni expulsarlos despues de actualizar a 8.10"
date: 2008-11-06
forum: Hardware
---

### Post by arysar on 2008-11-06
Despues de actualizar a Intrepid tengo 2 problemas:

1) si pongo un un CD se puede leer pero despues no lo puedo expulsar, leí esta información podría ayudar a ver el problema:

leonardo@sistemas07:~$ ls -l /dev/cdrom

lrwxrwxrwx 1 root root 4 2008-11-06 14:41 /dev/cdrom -> scd0

leonardo@sistemas07:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb2 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/Leo type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Win type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/RVA/leonardo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=leonardo)

leonardo@sistemas07:~$ gnome-eject -vbd /dev/cdrom
gnome-mount 0.8
Se ha resuelto el archivo de dispositivo /dev/cdrom -> /dev/scd0
** (gnome-eject:21886): DEBUG: Ejecting /org/freedesktop/Hal/devices/volume_label_CentOS_5_2_Final
El dispositivo /dev/scd0 está en /etc/fstab con punto de montaje «/media/cdrom0»
** Message: eject said error 256, stdout='', stderr='eject: incapaz de abrir `/dev/scd0'

----------

2) Cuando quiero grabar un CD , al poner un disco virgen reconoce que es un disco virgen, me pregunta que quiero hacer pero cuando lo quiero grabar BRASERO me dice que no detecta ningun disco en el drive.

Gracias por cualquier ayuda!

---

### Post by arysar on 2008-11-06
Agrego que debe ser un problema de permisos porque con el siguiente comando

leonardo@sistemas07:~$ sudo gnome-eject -vbd /dev/cdrom
gnome-mount 0.8
Se ha resuelto el archivo de dispositivo /dev/cdrom -> /dev/scd0
** (gnome-eject:30609): DEBUG: Ejecting /org/freedesktop/Hal/devices/volume_label_CentOS_5_2_Final
El dispositivo /dev/scd0 está en /etc/fstab con punto de montaje «/media/cdrom0»
Se ha expulsado /dev/scd0 (usando /etc/fstab).

el drive se abre y vuelve a cerrar.
Adjunto el contenido del /etc/fstab

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

gracias!

---

