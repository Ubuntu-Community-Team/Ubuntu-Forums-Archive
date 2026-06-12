---
title: "apt-get probles"
date: 2008-07-18
forum: General Help
---

### Post by badgandalf on 2008-07-18
After a routine update that went wrong, I've been having problems with apt-get to install several packages so I googled around and found some recommendations to proceed with: 
*sudo dpkg --configure -a*

However I get into some problems I do not know how to resolve. This is what i get:

[I]Configurando linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.24-19.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.24-19.34 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error al procesar linux-image-2.6.24-19-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Se encontraron errores al procesar:
 linux-image-2.6.24-19-generic[/I]

Anyone can help ?
Best,

Ignacio
EDIT:
Everything seems to be related to the new linux-image-2.6.24-19-generic installation. I've managed to login with the previous one and although most of the things work, apt-get continues to give errors and stop in the middle of some installations. I've tried deleting the files at:

/var/cache/apt/archives/
/var/cache/apt/archives/partial/
/var/lib/apt/list/
/var/lib/apt/list/partial/
/var/lib/dpkg/info/
/var/lib/dpkg/updates/

Deleting status and status.old and restoring a previous version at:
/var/lib/dpkg/

Then I tried also: sudo dpkg --configure -a

...to the same avail: continuos problems with apt-get installations...

---

