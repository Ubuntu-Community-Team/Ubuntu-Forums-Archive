---
title: "/usr/bin/dpkg returned an error code (2)"
date: 2008-09-04
forum: General Help
---

### Post by iKougar on 2008-09-04
lately after i updated my graphics driver i have been getting this error when i try to install anything or do any updates, i have reconfigured my xorg.conf file wich fixed my resolution problem but i cant use the graphics drivers now or install anything, here is the error i get.

> alan@alan-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  eject language-pack-en language-pack-gnome-en libgksu2-0 libglib2.0-0
  libsoup2.4-1 libtiff4 libxml2 libxml2-utils python-libxml2
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2488kB of archives.
After this operation, 496kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: unexpected eof reading `/var/lib/dpkg/diversions'
E: Sub-process /usr/bin/dpkg returned an error code (2)


i get that message when i try to install anything

i get this message when i try to do sudo dpkg-reconfigure -a 

> 
.
.
Use of uninitialized value in substitution (s///) at /usr/sbin/dpkg-divert line 125, <O> line 1.
dpkg-divert: internal error: /var/lib/dpkg/diversions corrupt: missing altname
alan@alan-desktop:~$ 


i dont have anything that important on here so i wanted to reinstall ubuntu all together but when i put my disk it and reboot it it will not read the disk.

any ideas?

---

### Post by iKougar on 2008-09-05
actually i dont need to fix this im getting ready to switch to Xubuntu but my cdrom wont read anything, the disk doesnt even sound like its spinning, the light just blinks for like 30 seconds then ejects the disk.

---

### Post by wolfen69 on 2008-09-05
> **iKougar said:**
> actually i dont need to fix this im getting ready to switch to Xubuntu but my cdrom wont read anything, the disk doesnt even sound like its spinning, the light just blinks for like 30 seconds then ejects the disk.

sounds like it's time for a new cd drive.

---

### Post by Shazaam on 2008-09-05
When you do a dist-upgrade you are trying to update Ubuntu to the latest version (Intrepid Ibex). Unless you have edited your sources.list to reflect this it won't work. And, since Ibex is only at Alpha stage it is not recommended for install unless you are prepared for things to either not work correctly or break.
```
sudo apt-get update
```
and...
```
sudo apt-get ugrade
```
or...
```
sudo apt-get update && sudo apt-get ugrade
```
will update/upgrade within your current installed version of Ubuntu.
This...
```
sudo dpkg-reconfigure -a 
```
will ask you to RE-configure ALL of your installed packages (one at a time). This...
```
sudo dpkg --configure -a
``` is probably what you want to enter.

---

### Post by iKougar on 2008-09-05
> alan@alan-desktop:~$ sudo dpkg --configure -a
dpkg: unexpected eof reading `/var/lib/dpkg/diversions'
alan@alan-desktop:~$ 


i just installed ubuntu on this computer a week ago so it cant be the cdrom, i used some command that ended up mounting it but i cant remember what it was now.

---

### Post by iKougar on 2008-09-06
here is the error i get when i try to mount my cd on almost any command i try 

> root@alan-desktop:/home/alan# mount /dev/cdrom 
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab


---

### Post by Shazaam on 2008-09-06
Try...
```
sudo mount /dev/cdrom0 /media
```
(thats cdromZERO)

---

### Post by iKougar on 2008-09-06
> **Shazaam said:**
> Try...
```
sudo mount /dev/cdrom0 /media
```
(thats cdromZERO)

heres what i got 

```
root@alan-desktop:/home/alan# sudo mount /dev/cdrom0 /media
mount: special device /dev/cdrom0 does not exist

```

---

### Post by Shazaam on 2008-09-06
Sorry I gave you the wrong drive id. Lets find out what is listed in fstab. In terminal...
```
cat /etc/fstab
```
Post the output here.

---

### Post by iKougar on 2008-09-06
> **Shazaam said:**
> Sorry I gave you the wrong drive id. Lets find out what is listed in fstab. In terminal...
```
cat /etc/fstab
```
Post the output here.

here ya go

```
alan@alan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4078c957-cf67-456d-8e2a-2fb67bf0f6f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=fc067aa6-f58b-42b9-b1b6-229a63970327 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
alan@alan-desktop:~$ 

```

---

### Post by Shazaam on 2008-09-06
Thanks.
Remove the # from in front of..
```
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
You will need to edit fstab as root so...
```
gksudo gedit /etc/fstab
```

---

### Post by iKougar on 2008-09-06
> **Shazaam said:**
> Thanks.
Remove the # from in front of..
```
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
You will need to edit fstab as root so...
```
gksudo gedit /etc/fstab
```

i read somewere that putting that there would fix the problem so it wasnt working before i added that either, will see if it does now.

---

### Post by iKougar on 2008-09-06
turns out it still wont work, any other suggestions?

---

### Post by iKougar on 2008-09-07
I noticed how when ubuntu starts up it trys to do a scan and when it scans /dev/sda1 my computer freezes and i have to restart, maby ill have to fix that before my cdrom will start working again.

---

### Post by iKougar on 2008-09-07
I got the startup thing fixed, just need this done now.

---

