---
title: "Update fails with this error"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by breauxlg on 2009-08-24
Update failed and gave me this error. Help. Thanks in advance.
Lynn


E: linux-image-2.6.28-15-server: subprocess post-installation script returned error exit status 1

E: linux-restricted-modules-2.6.28-15-server: dependency problems - leaving unconfigured

E: linux-image-server: dependency problems - leaving unconfigured

E: linux-restricted-modules-server: dependency problems - leaving unconfigured

E: linux-server: dependency problems - leaving unconfigured

---

### Post by Partyboi2 on 2009-08-24
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo dpkg --configure -a
``` Hopefully this will provide some more info on what has gone wrong.

---

### Post by breauxlg on 2009-08-25
Here it is. Thanks.

administrator@ubuntulamp:~$ sudo dpkg --configure -a
[sudo] password for administrator: 
Setting up linux-image-2.6.28-15-server (2.6.28-15.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-server
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-15-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.28-15-server; however:
  Package linux-image-2.6.28-15-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.28.15.20); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-server:
 linux-restricted-modules-2.6.28-15-server depends on linux-image-2.6.28-15-server; however:
  Package linux-image-2.6.28-15-server is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-15-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-server:
 linux-restricted-modules-server depends on linux-restricted-modules-2.6.28-15-server; however:
  Package linux-restricted-modules-2.6.28-15-server is not configured yet.
dpkg: error processing linux-restricted-modules-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-15-server
 linux-image-server
 linux-server
 linux-restricted-modules-2.6.28-15-server
 linux-restricted-modules-server
administrator@ubuntulamp:~$

---

### Post by Partyboi2 on 2009-08-26
What is the contents of /boot/grub?
```
ls -a /boot/grub
```

---

### Post by breauxlg on 2009-08-26
administrator@ubuntulamp:~$ ls -a /boot/grub
.  ..  default  device.map  menu.lst
administrator@ubuntulamp:~$ 


It looks like I've somehow lost grub. I've been looking at how to re-install it, but I was waiting to hear from you.

---

### Post by Partyboi2 on 2009-08-27
Open a terminal and try
```
sudo cp /usr/lib/grub/i386-pc/* /boot/grub
```
then
```
sudo grub
find /boot/grub/stage1
```
what ever the output to "find /boot/grub/stage1" use it for the next command
```
root (hd?,?)
```
then
```
setup (hd0)
```
```
quit
```
Then reboot to check grub is working. If it is then open a terminal and
```
sudo dpkg --configure -a
```

---

### Post by breauxlg on 2009-08-28
This is what I get.

grub> find /boot/grub/stage1

Error 15: File not found

grub> 


I had trouble the last time I rebooted (power failure) so I'm not shutting it down til I can fix this, I hope.

---

