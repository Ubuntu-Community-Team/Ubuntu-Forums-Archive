---
title: "Can't mount ntfs 500 gb external simpletech drive??"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by shawnchristopherconley on 2007-12-27
Hi when i try to plug in the external i get error message
unable to mount drive 
how do you mount an external ntfs drive in gutsy gibbon?

---

### Post by taurus on 2007-12-27
Let's see what happens when you run this command from a terminal.  Post the result here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Lower case letter L.

---

### Post by mikerduffy on 2007-12-27
I have a 500GB NTFS Cavalry external USB HDD.

I got it working in Gutsy by doing the following:

-Plug the external NTFS HDD into the USB port.
-Right-click on the external storage icon on the desktop.
-Click on "Properties".
-Click on the "Mounting" tab.
-**Uncheck** the "Mount as user" box.
-Right-click on the external storage icon on the desktop.
-Click "Mount".

Hopefully, that will solve your problem.

I found this info either here at ubuntuforums, or on kubuntuforums.

---

### Post by famleon on 2008-01-07
i try to run the fdisk l
this is what I got

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pistas, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfc318e1

Disposit. Inicio    Comienz
o      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extendida
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disco /dev/sdb: 500.1 GB, 500107861504 bytes
255 cabezas, 63 sectores/pistas, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3eec6fa

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

but when I try to do the second solution I am not able to do it because in the desktop there's not an icon for the drive, any other idea?

---

### Post by taurus on 2008-01-07
> **famleon said:**
> i try to run the fdisk l
this is what I got

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pistas, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfc318e1

Disposit. Inicio    Comienz
o      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extendida
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disco /dev/sdb: 500.1 GB, 500107861504 bytes
255 cabezas, 63 sectores/pistas, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3eec6fa

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

but when I try to do the second solution I am not able to do it because in the desktop there's not an icon for the drive, any other idea?

How about

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by famleon on 2008-01-07
this is what I got
Leyendo lista de paquetes... Hecho
tavolio@tavolio:~$ sudo apt-get install ntfs-3g
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
ntfs-3g ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  linphone-common
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
tavolio@tavolio:~$ sudo mkdir /media/sdb1
mkdir: no se puede crear el directorio `/media/sdb1': El fichero ya existe
tavolio@tavolio:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operación no soportada
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0
tavolio@tavolio:~$ ls -la /media/sdb1 -o force
ls: force: No existe el fichero ó directorio
/media/sdb1:
total 8
drwxr-xr-x 2 root 4096 2008-01-07 15:04 .
drwxr-xr-x 4 root 4096 2008-01-07 15:05 ..


Any Idea? please feel free to contact me directly

---

### Post by taurus on 2008-01-07
Sounds like you didn't shut down your windows cleanly.  So, you can either boot windows and shut it down cleanly this time or you can use the force option to mount it.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
ls -la /media/sdb1
```

---

### Post by famleon on 2008-01-07
Great it worked out, thanks, do i have to force the HDD everytime?

---

### Post by famleon on 2008-01-09
after i reboot the computer, the external drive works normal, but my cd dvd is not working, I can not mount it, is this related?

thanks

---

