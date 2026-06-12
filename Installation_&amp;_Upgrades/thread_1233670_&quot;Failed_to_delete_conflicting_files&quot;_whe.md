---
title: "&quot;Failed to delete conflicting files&quot; when trying to install Ubuntu"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2009-08-06
I had a Windows Vista + Ubuntu 9.04 64 bits installation, but wanted to reinstall it since I've had several issues with the latest version (all of them related to video, posted here and searched the web but haven't got a fix :(). Anyway, I tried to install using the Ubuntu 9.04 64b LiveCD, got to the partition selection step, manually configured partitions: a partition to be formated for / mounting (previously ext4), another one for /home (won't be formatted, ext3) and the swap partition, but when the install process started, I received this message:

"Failed to delete conflicting files"
"The installer needs to remove operating system files from the install target, but was unable to do so. The install cannot continue"

Well, something like that, my system is in Spanish :).

Then, I tried with the 8.04 LiveCD but I'm getting same message. Tried deleting the Ubuntu partition and running the installation process but same message again.

Now, when booting I get a GRUB error message (first I got error 15, now I'm getting error 17).

At this moment, I'm trying to recover the Vista MBR so that I can boot 

Do you have any idea about this? Any comment/advice is welcome.

---

### Post by GeoMX on 2009-09-14
I've been using Ubuntu since 2005 and have never faced a problem like this :(.

I managed to recover my Vista boot (now replaced with Windows 7).

Yesterday, I tried once more to reinstall Ubuntu using the 8.04.3 alternate CD, but same message appears:

Original message (Spanish):
Particionado de discos
Error al eliminar los archivos conflictivos
El instalador necesita eliminar del destino de instalación ciertos archivos del sistema operativo, pero no ha sido capaz de hacerlo. La instalación no puede continuar.

English:
Disk  partitioning
Failed to delete conflicting files
The installer needs to remove operating system files from the install target, but was unable to do so. The install cannot continue.

I have tried using Ubuntu 8.04 and 9.04 live and alternate cds, but no luck.

---

### Post by GeoMX on 2009-09-15
Finally, I could install Ubuntu again :).

Followed suggestion in comment #15 at
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/186147?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/186147?comments=all)

I did not install Archlinux, just got to the partition setup, configured my partitions, applied changes and quitted the installation process. Then, I tried again with Ubuntu 8.04 alternate CD, the partition problem did not appear :), got some errors when copying files because my disc was corrupt, burned it again and voilá! Linux is rocking my laptop once again :guitar:

---

