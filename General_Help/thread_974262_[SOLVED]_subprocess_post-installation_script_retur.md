---
title: "[SOLVED] subprocess post-installation script returned error exit status 2"
date: 2008-11-07
forum: General Help
---

### Post by kulus1969 on 2008-11-07
Not sure why I keep getting this error message whenever I update ubuntu:

E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

Please help...

Kulus

---

### Post by kulus1969 on 2008-11-07
kevin@daddy:~$ sudo dpkg --configure -a
sudo: unable to resolve host daddy
[sudo] password for kevin: 
Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/appleblack.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
kevin@daddy:~$

---

### Post by kulus1969 on 2008-11-07
kevin@daddy:~$ sudo apt-get install -f
sudo: unable to resolve host daddy
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/appleblack.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@daddy:~$

---

### Post by kulus1969 on 2008-11-07
Do I need to delete some of the old versions of the kernel so that I have room to install new versions of the kernel?

Kulus

---

### Post by kulus1969 on 2008-11-07
If I use:

sudo dpkg-reconfigure -a

should I just accept all default entries?

Kulus

---

### Post by kulus1969 on 2008-11-07
I this bad?  It happened after I picked a non-default keyboard that was the most similar to mine which is a Microsoft Multimedia Keyboard 1.0A.  The one I picked was the same only a wireless version.  Maybe that wasn't very smart...

Updating certificates in /etc/ssl/certs....done.
 * Saving console font and keymap for next boot...                                                  WARNING: Undefined kernel key code for 121
WARNING: Undefined kernel key code for 122
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Unknown X keysym "XF86Messenger"
WARNING: Undefined kernel key code for 135
WARNING: Undefined kernel key code for 136
WARNING: Undefined kernel key code for 150
WARNING: Undefined kernel key code for 153
WARNING: Undefined kernel key code for 160
WARNING: Undefined kernel key code for 161
WARNING: Undefined kernel key code for 162
WARNING: Undefined kernel key code for 163
WARNING: Undefined kernel key code for 164
WARNING: Undefined kernel key code for 174
WARNING: Undefined kernel key code for 176
WARNING: Undefined kernel key code for 178
WARNING: Undefined kernel key code for 187
WARNING: Undefined kernel key code for 188
WARNING: Undefined kernel key code for 194
WARNING: Undefined kernel key code for 195
WARNING: Undefined kernel key code for 223
WARNING: Undefined kernel key code for 228
WARNING: Undefined kernel key code for 236
WARNING: Undefined kernel key code for 237

Thanks in advance...

Kulus

---

### Post by kulus1969 on 2008-11-07
Despite errors the sudo dpkg-reconfighure -a seems to have not broken anything.

I started this thread not just because of the original error but also because"

GRUB does not show latest version of kernel

"2.6.24-21"

It only shows "2.6.24-18" and "2.6.24-19" plus there recovery mode equivalents and memtest.

How do I update the GRUB Menu to include "2.6.24-21"?

---

### Post by kulus1969 on 2008-11-07
reinstalled linux-generic

unfortuneately still get this error:

E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

---

### Post by kulus1969 on 2008-12-06
reinstalled grub

Still get this error:
E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.24-22-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-22-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-22-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured

I will now try to backup my drive and reinstall ubuntu

---

### Post by kulus1969 on 2008-12-09
Backup, reinstall, and restore fixed my problem.

Does anyone know how to fix this problem without a reinstall?

Kulus

---

### Post by eumetaxas on 2008-12-09
Hi,
had exact the same problem.
Downgraded to 2.6.24.19 solved my problem.
But i had a boot issue because menu.lst was not updated and solved it using the live cd and edited the menu.lst from there.

Regards \

Eugene

---

### Post by macabro22 on 2010-01-11
****. same problem,

---

### Post by forteller on 2010-11-07
So, how did this get solved? I have the same problem!

E: linux-image-2.6.35-23-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured

---

