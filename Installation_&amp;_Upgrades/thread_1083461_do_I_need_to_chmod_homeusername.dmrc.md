---
title: "do I need to chmod /home/username/.dmrc ???"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-03-01
Hey guys,

I get this announce saying more or less as follows

 	Quote:
 	 	 		 It's being ignored the file $HOME/.dmrc of the user. This stops you from saving your default section and language. The file should belong to the user and have the permits 644. The user's personal directory most belong to the user and not be writable to other users.  	 	 
is there any solution for stopping the announce from keep showing every time i log in?

I already run

  	 	 	 		 			 				ls -la /home/william/.dmrc 			 		 	 	 
and i get
 	Quote:
 	 	 		 			 				-rw-r--r-- 1 william william 26 2009-02-26 19:27 /home/william/.dmrc 			 		 	 	 
any idea??
Thanks...
 		                   		  		  		 		 			 				_____________

---

### Post by taurus on 2009-03-01
```
chmod 755 /home/william
```

---

### Post by Will4 on 2009-03-01
Thank you taurus,

hahaha you are kind of my savior today...

Ok i did, what next? 
I also did 
> ls -al /home/william/.dmrc
and gave me
> -rwxrwxrwx 1 william william 26 2009-02-26 19:27 /home/william/.dmrc

Thank you

---

### Post by taurus on 2009-03-01
The permission for your ~/.dmrc is wrong.  You have it right before so change it back or change it to -rw------.

```
chmod 600 ~/.dmrc
ls -la ~
```

---

### Post by Will4 on 2009-03-01
Ok now is 

> -rw-------  1 william william     26 2009-02-26 19:27 .dmrc

do this one have anything to do with the error??
> ??????????  ? ?       ?            ?                ? .gvfs

---

### Post by taurus on 2009-03-01
It should something like this.

```
dr-x------  2 taurus taurus      0 2009-02-28 08:35 .gvfs
```
Post these.

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la ~
```

---

### Post by Will4 on 2009-03-01
wait

---

### Post by Will4 on 2009-03-01
it sais 

> ls -la ~
ls: no se puede acceder a /home/william/.gvfs: Permiso denegado
in English
> ls: can not access /home/william/.gvfs: Permission denied. 

what next??
Thanks

---

### Post by taurus on 2009-03-01
What happens to the other three commands?

---

### Post by Will4 on 2009-03-01
after 

> ls -la ~
??????????  ? ?       ?            ?                ? .gvfs

nothing changed!! Sorry!! 
So??

---

### Post by Will4 on 2009-03-01
sorry i will post it now it was too much staff...

---

### Post by Will4 on 2009-03-01
this is for 

> fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf1d4a41d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       11044    88710898+   7  HPFS/NTFS
/dev/sda2           11045       19457    67577422+   7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x5c4dde18

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1          46      369463+  83  Linux
/dev/sdb2            9445        9726     2265165    5  Extendida
/dev/sdb3              47        9444    75489435   83  Linux
/dev/sdb5            9445        9726     2265133+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdc: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xc4dec4de

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1        4998    40146403+  83  Linux

Disco /dev/sdd: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x44fdfe06

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disco /dev/sdf: 8021 MB, 8021606400 bytes
5 cabezas, 32 sectores/pista, 97920 cilindros
Unidades = cilindros de 160 * 512 = 81920 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdf1   *          51       97920     7829568    c  W95 FAT32 (LBA)

---

### Post by Will4 on 2009-03-01
this is for 

> cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fd4b1619-59ad-4341-ab35-d8a332bac727 /               reiserfs relatime        0       1
# /dev/sda1
UUID=348ddd1a-aaac-4f33-b40b-da2e0d4cc6a0 /boot           reiserfs notail,relatime 0       2
# /dev/sda5
UUID=eff76261-d3c2-4d9d-8a2f-456610251339 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Will4 on 2009-03-01
this is for 

> df -h

S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb3              72G   26G   47G  36% /
varrun                379M  148K  378M   1% /var/run
varlock               379M  4,0K  379M   1% /var/lock
udev                  379M   84K  378M   1% /dev
devshm                379M  192K  378M   1% /dev/shm
lrm                   379M   38M  341M  10% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb1             361M   87M  275M  25% /boot
/dev/sdd1             466G  408G   59G  88% /media/William_WD
/dev/sdf1             7,5G  2,9G  4,6G  39% /media/WILLIAM


---

### Post by Will4 on 2009-03-01
and then 

> ls -la ~

ls: no se puede acceder a /home/william/.gvfs: Permiso denegado
total 549
drwxr-xr-x 71 william william   2584 2009-03-01 01:29 .
drwxr-xr-x  4 root    root        96 2008-12-10 01:07 ..
drwxrwxrwx  3 william william     80 2009-01-07 01:59 .adobe
drwxrwxrwx  2 william root        48 2009-02-05 01:41 .aptoncd
drwxrwxrwx  3 william william    360 2009-01-21 23:35 .aTunes
drwxrwxrwx 10 william william    656 2009-01-30 19:14 .azureus
drwxrwxrwx  3 william william     72 2009-01-30 18:38 .Azureus
-rwxrwxrwx  1 william root     13193 2009-03-01 01:28 .bash_history
-rwxrwxrwx  1 william william    220 2008-12-09 11:09 .bash_logout
-rwxrwxrwx  1 william william   2928 2008-12-09 11:09 .bashrc
drwxrwxrwx  7 william william    264 2009-03-01 01:32 .beagle
drwxrwxrwx  8 william william    200 2008-12-21 17:26 .cache
drwxrwxrwx  3 william william     72 2008-12-10 01:08 .compiz
drwxrwxrwx  2 william william    144 2008-12-16 23:58 .conduit
drwxrwxrwx 18 william william    568 2009-02-25 04:07 .config
-rwxrwxrwx  1 william william    578 2009-02-18 15:33 .convertall
drwxrwxrwx  3 william william     80 2008-12-09 19:25 .dbus
drwxrwxrwx  2 william william     48 2009-02-27 00:25 Desktop
-rw-------  1 william william     26 2009-03-01 01:29 .dmrc
drwxrwxrwx  2 william william    872 2009-02-27 00:34 Documentos
drwxrwxrwx 12 william william    616 2009-03-01 00:57 Escritorio
-rwxrwxrwx  1 william william     16 2008-12-09 11:16 .esd_auth
drwxrwxrwx  2 william william    176 2009-02-27 00:28 e-Sword
drwxrwxrwx  8 william william    344 2009-03-01 01:28 .evolution
lrwxrwxrwx  1 william william     26 2008-12-09 11:09 Examples -> /usr/share/example-content
-rwxrwxrwx  1 william william 161862 2008-12-15 00:05 .face
drwxrwxrwx  2 william william     48 2008-12-15 22:21 fet-results
drwxrwxrwx  2 william william    240 2008-12-26 23:55 .fontconfig
drwxrwxrwx  4 william william     96 2009-03-01 01:29 .gconf
drwxrwxrwx  2 william william     80 2009-03-01 01:35 .gconfd
drwxrwxrwx 22 william william    928 2009-03-01 00:31 .gimp-2.4
-rwxrwxrwx  1 william william      0 2009-02-28 20:39 .gksu.lock
drwxrwxrwx  2 william william     48 2009-01-18 23:49 .gnome
drwxrwxrwx 17 william william    848 2009-02-28 23:34 .gnome2
drwxrwxrwx  2 william william     48 2008-12-09 11:16 .gnome2_private
drwxrwxrwx  3 william william    152 2008-12-15 22:37 .gnome-commander
drwxrwxrwx  4 william william    136 2009-01-05 14:12 .gnomesword
drwxrwxrwx  2 william william    168 2009-03-01 01:29 .gnupg
drwxrwxrwx  2 william william     88 2009-02-01 23:06 .gstreamer-0.10
-rw-r--r--  1 william william    139 2009-03-01 01:29 .gtk-bookmarks
??????????  ? ?       ?            ?                ? .gvfs
drwxrwxrwx  2 william william     48 2009-02-25 02:30 .helix
-rwxrwxrwx  1 william william    199 2009-01-17 16:13  home.htm~
-rw-------  1 william william   7846 2009-03-01 01:29 .ICEauthority
drwxrwxrwx  2 william william     48 2008-12-09 19:22 .icons
drwxrwxrwx 14 william william    440 2009-02-19 23:27 Imágenes
drwxrwxrwx  3 william william     80 2009-02-18 02:59 .java
drwxrwxrwx  3 william william    168 2009-02-17 18:57 .kde
drwxrwxrwx  3 william william     72 2008-12-09 11:16 .local
drwxrwxrwx  3 william william     80 2009-01-07 01:59 .macromedia
-rwxrwxrwx  1 william william   3146 2009-02-25 02:32 .mailcap
drwxrwxrwx  3 william william     72 2008-12-26 19:23 .marble
drwxrwxrwx  3 william root       168 2009-02-27 18:04 .mc
drwxrwxrwx  3 william william    112 2008-12-11 15:56 .mcop
-rwxrwxrwx  1 william william     31 2008-12-11 15:56 .mcoprc
drwxrwxrwx  3 william william     72 2008-12-09 11:16 .metacity
drwxrwxrwx  4 william william    104 2008-12-09 20:47 .mozilla
drwxrwxrwx  3 william william    112 2008-12-09 19:39 .mozilla-thunderbird
drwxrwxrwx  2 william william    176 2008-12-15 22:01 .mplayer
drwxrwxrwx 11 william william    352 2009-02-05 15:32 Música
drwxrwxrwx  3 william william   3760 2009-02-27 00:53 .nautilus
drwxrwxrwx  3 william william     80 2009-01-16 09:53 .ogle
drwxrwxrwx  3 william william     72 2008-12-09 20:40 .openoffice.org
drwxrwxrwx  3 william william     72 2008-12-09 20:03 .openoffice.org2
drwxrwxrwx  4 william william     96 2009-01-07 22:21 Photos
drwxrwxrwx  2 william william     48 2008-12-09 11:16 Plantillas
drwxrwxrwx  3 william william    112 2009-01-19 19:01 .prism
-rwxrwxrwx  1 william william    586 2008-12-09 11:09 .profile
drwxrwxrwx  2 william william     48 2008-12-09 11:16 Público
drwxrwxrwx  2 william william    152 2008-12-10 23:38 .pulse
-rwxrwxrwx  1 william william    256 2008-12-09 11:16 .pulse-cookie
drwxrwxrwx  3 william william     80 2008-12-23 18:26 .qstardict
drwxrwxrwx  2 william william    120 2008-12-11 15:51 .qt
-rwxrwxrwx  1 william william   7790 2009-02-27 00:48 .recently-used
-rw-r--r--  1 william william 283683 2009-03-01 00:43 .recently-used.xbel
drwxrwxrwx  3 william william    152 2009-02-28 16:15 .smplayer
drwxrwxrwx  2 william william     48 2008-12-09 11:16 .ssh
drwxrwxrwx  2 william william    104 2009-02-18 15:36 .stardict
-rwxrwxrwx  1 william william      0 2008-12-09 11:17 .sudo_as_admin_successful
drwxrwxrwx  5 william william    128 2009-01-05 14:12 .sword
drwxrwxrwx  2 william william     48 2008-12-09 19:22 .themes
drwxrwxrwx  5 william william    120 2008-12-17 17:16 .thumbnails
drwxrwxrwx  2 william william    112 2009-02-25 03:55 .update-manager-core
drwxrwxrwx  2 william william     48 2008-12-09 11:16 .update-notifier
drwxrwxrwx  3 william william    240 2009-03-01 00:20 Videos
drwxrwxrwx  3 william william     88 2009-02-07 17:07 vmware
drwxrwxrwx  2 william william    184 2009-02-07 17:24 .vmware
drwxrwxrwx  2 william william    168 2009-03-01 01:29 .wapi
drwxrwxrwx  4 william william    232 2009-02-28 17:58 .wine
-rw-------  1 william william    600 2009-02-28 22:33 .wvdial.conf
-rwxrwxrwx  1 william william    117 2009-02-26 19:27 .Xauthority
drwxrwxrwx  2 william william     80 2008-12-11 15:51 .xine
-rw-r--r--  1 william william  12882 2009-03-01 01:30 .xsession-errors

---

### Post by taurus on 2009-03-01
> **Will4 said:**
> 
**[COLOR="Red"]-rwxrwxrwx[/COLOR]** 1 william william 117 2009-02-26 19:27 .Xauthority


Looks like you were playing with the permissions big time.

```
chmod 600 ~/.Xauthority
```
And not sure how you got ~/.gvfs to look like that?

---

### Post by Will4 on 2009-03-01
Now looks like this

> -rw-------  1 william william    117 2009-02-26 19:27 .Xauthority

but ~/.gvfs still looks the same.
Any clue??

---

