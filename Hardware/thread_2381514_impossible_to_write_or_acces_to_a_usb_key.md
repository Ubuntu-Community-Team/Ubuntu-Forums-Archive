---
title: "impossible to write or acces to a usb key"
date: 2018-01-01
forum: Hardware
---

### Post by bugin on 2018-01-01
First sorry for my bad english. I ve recently bought a usb key, and manage for some days to use it. But  recently it doesn't work anymore. I cant even acces to. There is noting important inside, and i will be  happy to manage to format it. But nothing done for the moment. I ve already try a lot of thing :
  I ve try with GParted, but it didn't manage to recognize the key
```

gparted-pkexec Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
======================
libparted : 3.2
======================
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Erreur d'entrée/sortie lors de la lecture sur /dev/sdb
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/tmp.mount.

```The key is somewhere :
  ```
sudo lsblk -o name,fstype,size,mountpoint,label
NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           931,5G            
&#9500;&#9472;sda1 ntfs     500M            Réservé au système
&#9500;&#9472;sda2 ntfs   194,8G            
&#9492;&#9472;sda5 ext4   736,2G /          
sdb            29,3G            
sr0            1024M 

```  But nothing to do :
  ```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=4096
dd: erreur d'écriture de '/dev/sdb': Erreur d'entrée/sortie
1+0 enregistrements lus
0+0 enregistrements écrits
0 bytes copied, 0,00102609 s, 0,0 kB/s
floflodou@floflodou-MS-7A74:~$ sudo install-mbr /dev/sdb --force -t 0 -e 1install-mbr: Error reading /dev/sdb: Input/output error
  
```Ive try some classic operations :
  ```
$ sudo fdisk -l /dev/sdb
fdisk: impossible d'ouvrir /dev/sdb: Erreur d'entrée/sortie

```  but noting done :
  ```
sudo e2fsck -f -v /dev/sdb[sudo] Mot de passe de floflodou : 
e2fsck 1.43.5 (04-Aug-2017)
e2fsck: Erreur d'entrée/sortie lors de la tentative d'ouverture de /dev/sdb

Le superbloc n'a pu être lu ou ne contient pas un système de fichiers
ext2/ext3/ext4 correct. Si le périphérique est valide et qu'il contient réellement
un système de fichiers ext2/ext3/ext4 (et non pas de type swap, ufs ou autre),
alors le superbloc est corrompu, et vous pourriez tenter d'exécuter
e2fsck avec un autre superbloc :
    e2fsck -b 8193 <périphérique>
 ou
    e2fsck -b 32768 <périphérique>

floflodou@floflodou-MS-7A74:~$ sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.43.5 (04-Aug-2017)
e2fsck: Erreur d'entrée/sortie lors de la tentative d'ouverture de /dev/sdb

Le superbloc n'a pu être lu ou ne contient pas un système de fichiers
ext2/ext3/ext4 correct. Si le périphérique est valide et qu'il contient réellement
un système de fichiers ext2/ext3/ext4 (et non pas de type swap, ufs ou autre),
alors le superbloc est corrompu, et vous pourriez tenter d'exécuter
e2fsck avec un autre superbloc :
    e2fsck -b 8193 <périphérique>
 ou
    e2fsck -b 32768 <périphérique>

floflodou@floflodou-MS-7A74:~$ sudo e2fsck -b 32768 /dev/sdb
e2fsck 1.43.5 (04-Aug-2017)
e2fsck: Erreur d'entrée/sortie lors de la tentative d'ouverture de /dev/sdb

Le superbloc n'a pu être lu ou ne contient pas un système de fichiers
ext2/ext3/ext4 correct. Si le périphérique est valide et qu'il contient réellement
un système de fichiers ext2/ext3/ext4 (et non pas de type swap, ufs ou autre),
alors le superbloc est corrompu, et vous pourriez tenter d'exécuter
e2fsck avec un autre superbloc :
    e2fsck -b 8193 <périphérique>
 ou
    e2fsck -b 32768 <périphérique>

```
 Ive try under windows 7 and 10 but without result
  If some people have an idea...
  Ive try also some other thing purpose in french, you can see here, but no result : [https://forum.ubuntu-fr.org/viewtopic.php?pid=21847677#p21847677](https://forum.ubuntu-fr.org/viewtopic.php?pid=21847677#p21847677)

---

### Post by gordintoronto on 2018-01-01
It sounds like you removed the USB key before using "Unmount Volume" or "Eject Volume". I've done it, and the USB key became electronic waste.

---

### Post by Autodave on 2018-01-02
Sounds like a bad / failed USB stick. Can you return it to where you bought it?

---

### Post by kurt18947 on 2018-01-02
> **gordintoronto said:**
> It sounds like you removed the USB key before using "Unmount Volume" or "Eject Volume". I've done it, and the USB key became electronic waste.

Would the key not be usable after reformatting? I can understand the data on the key being unreadable. If I understand it correctly, Unmount/Eject write any cached data to the removable device. Do they do more? Bugin said there was nothing of value on the key so reformat and rewrite? If gparted doesn't recognize the key it may indeed be waste but sdb appears in some of the entries. Isn't that the flash drive?

---

