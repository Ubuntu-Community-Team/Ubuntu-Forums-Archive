---
title: "Tengo dos valore de Swap ¿?"
date: 2009-02-25
forum: Hardware
---

### Post by EnriqueK on 2009-02-25
Si ejecuto **top** el valor de la Swap me da 1214 MB , si en cambio entro a **Gparted** este valor es de 714 MB, que es el valor que predefiní al hacer la instalación y es mas, si deshabilito la Swap (sudo swapoff /dev/sda7), en **top** me sigue mostrando una swap activa pero esta es de 500 MB o sea exactamente la diferencia entre los valores puestos al pricipio, no entiendo a que se pueda deber estas diferencias de valores y sobretodo por que el valor de swap que adopta el sistema es diferente a la predefinida al crear las particiones .

---

### Post by fmsismo on 2009-02-26
Hace una cosa simple.

sudo fdisk -l

Con este comando fdisk te lista todas las particiones que tiene tu sistema.  Ahí podemos ver cuantas particiones swap tenes.

Saludos

---

### Post by EnriqueK on 2009-02-26
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3843    30868866    7  HPFS/NTFS
/dev/sda2            3844       17546   110069347+   f  W95 Ext'd (LBA)
/dev/sda3           17547       19457    15350107+  83  Linux
/dev/sda5            3844        5374    12297726    b  W95 FAT32
/dev/sda6            5375       16180    86799163+   b  W95 FAT32
/dev/sda7           16181       16271      730926   82  Linux swap / Solaris
/dev/sda8           16272       17546    10241406   83  Linux

---

### Post by fmsismo on 2009-02-26
Ejecuta el comando
  mount

Lo unico que se me ocurre es que tengas swap en un archivo.

Ya que estas, copianos el fstab tuyo.

  cat /etc/fstab

Y el output del comando 
  free

Saludos

---

### Post by EnriqueK on 2009-02-26
Ante todo gracias, por el interés, aquí van los datos, fijate que con el comando free muestra un valor de Swap de 1243060  .
Otra cosa, las particiones las tengo montadas usando el programa **Disk Manager**

**enrique@enrique-desktop:~$ mount**
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
/dev/sda5 on /media/D type vfat (rw,utf8,umask=0)
/dev/sda6 on /media/E type vfat (rw,utf8,umask=0)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/enrique/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=enrique)



**enrique@enrique-desktop:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=04f436f2-604f-47ea-a907-4330f35fa014	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda8 :
UUID=2e216911-2d10-40b1-8e21-d2bc6f5a4281	/home	ext3	relatime	02
#Entry for /dev/sda5 :
UUID=45A4-322D	/media/D	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda6 :
UUID=41B3-E25F	/media/E	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda7 :
UUID=b3bcced9-b1be-443b-a529-31d027aeb12a	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


**enrique@enrique-desktop:~$ free**
             total       used       free     shared    buffers     cached
Mem:       2048588    2030932      17656          0     102548     961656
-/+ buffers/cache:     966728    1081860
Swap:      1243060       5592    1237468

---

### Post by fmsismo on 2009-02-27
Que raro che.

Pasame lo que te devuelve esto.

cat /proc/meminfo |grep Swap

cat /proc/swaps

Saludos

---

### Post by EnriqueK on 2009-02-27
Parece que hay algo, aunque no entiendo un pomo 


enrique@enrique-desktop:~$ cat /proc/meminfo |grep Swap
SwapCached:       2208 kB
SwapTotal:     1243060 kB
SwapFree:      1240844 kB



enrique@enrique-desktop:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	512144	2216	100
/dev/sda7                               partition	730916	0	-1

---

### Post by fmsismo on 2009-02-27
Ok, no se porque, pero estas usando un módulo que se llama Compcache.  No se si tu sistema tiene poca memoria.

Te paso la documentación que encontre en ubunto sobre esta modulo del kernel.

[https://wiki.ubuntu.com/Compcache](https://wiki.ubuntu.com/Compcache)

---

### Post by EnriqueK on 2009-02-28
Gracias por tu interés, solo que tengo 2 gigas de ram y una instalación de Intrepid 64 bits.

---

### Post by NickCis on 2009-03-07
Me intereso eso del Compcache. Lei el articulo en la wiki de ubuntu pero no entendi bien que es.
Por lo qeu entendi es un swap que se crea solo, mi pensamiento esta muy lejos de lo real? xD..

Saludos.

---

