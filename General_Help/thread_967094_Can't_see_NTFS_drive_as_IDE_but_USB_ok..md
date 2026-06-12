---
title: "Can't see NTFS drive as IDE but USB ok."
date: 2008-11-01
forum: General Help
---

### Post by asmg48 on 2008-11-01
I am using the Live CD to check my WinXP drive but if connect it as an internal IDE got an error saying that I don't have permissions to see the content.(It's root user!) This drive boots OK and have no problems with it with WinXP.
But works fine if connected as an USB drive. I can see all files and also can execute Open Office on xls and doc.
Also tried with Ubuntu installed in a hard drive but the message is the same.
Any ideas?

---

### Post by taurus on 2008-11-01
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And by the way, just because you are the only/first user of your machine, it doesn't mean that you are root!

---

### Post by asmg48 on 2008-11-02
Thanks for your help.
The output for 'fdisk -l' is:
Disco /dev/hda: 41.1 GB, 41174138880 bytes
255 cabezas, 63 sectores/pista, 5005 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        4865    39078081   83  Linux
/dev/hda2            4866        5005     1124550    5  Extendida
/dev/hda5            4866        5005     1124518+  82  Linux swap / Solaris

Disco /dev/hdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS

I did not know that you are not 'root' user when you are using the Live CD, but I also tried to modify directory permissions (chmod 777)under 'root' ('su root') booting from '/dev/hda1' and then I can see the content of the Win drive but all files show as 'hidden' and cannot execute them beeing 'root'.

---

### Post by asmg48 on 2008-11-03
I tried also a LiveCD with Gentoo and had the same problem. Then I installed Suse and I was able to see the Win files.
Then I decided to give Ubuntu another chance and this time it worked fine!
Something might went wrong during the first installation, but I didn see any error message.
Thank for your help anyway...):P

---

### Post by taurus on 2008-11-03
Looks like your ntfs is on /dev/hdb1.  The easiest way is to install ntfs-config and use it to configure your ntfs filesystem.

Open a terminal (not from the LiveCD) and run

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

