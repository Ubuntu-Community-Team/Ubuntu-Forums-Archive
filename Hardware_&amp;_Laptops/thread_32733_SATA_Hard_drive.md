---
title: "SATA Hard drive"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by Oblivious Hazard on 2005-05-09
does the Raptor SATA hard drive work with this linux..if so do i have to install anything for it or will linux automaticly detect it

---

### Post by Sam on 2005-05-09
[QUOTE=Oblivious Hazard]does the Raptor SATA hard drive work with this linux..if so do i have to install anything for it or will linux automaticly detect it[/QUOTE]
You don't need anything, it works out-of-the-box.

The only thing you should know is that the drive will be on /dev/sdX rather than /dev/hdX.

---

### Post by Oblivious Hazard on 2005-05-09
Thanks for your help, the reason for asking is because when installing windows I had to use a floppy and install the drivers off the floppy to install windows on the SATA HD.

---

### Post by Sam on 2005-05-09
[QUOTE=Oblivious Hazard]Thanks for your help, the reason for asking is because when installing windows I had to use a floppy and install the drivers off the floppy to install windows on the SATA HD.[/QUOTE]
I have SATA, but I didn't use a floppy for the installation of my windows partition. Did you use the F6 key on the beginning of the install ? If so, you did use your SATA with software raid. AFAIK, this isn't supported well in linux so avoid doing this.

---

### Post by Oblivious Hazard on 2005-05-09
[QUOTE=Sam]I have SATA, but I didn't use a floppy for the installation of my windows partition. Did you use the F6 key on the beginning of the install ? If so, you did use your SATA with software raid. AFAIK, this isn't supported well in linux so avoid doing this.[/QUOTE]
 what is afaik and i did use the f6 key...does this change anything about install linux

---

### Post by Sam on 2005-05-09
[QUOTE=Oblivious Hazard]what is afaik and i did use the f6 key...does this change anything about install linux[/QUOTE]
AFAIK = As far as I know

I you did use the F6 key and you're about to make a dual boot, your windows partitions won't be available in linux at all (it could even be a mess if you delete a raid'ed partition). But if you're planning to format everything, there won't be any problem !

---

### Post by Oblivious Hazard on 2005-05-09
I am planning on formatting everything, so thats good news... So I wont need to use anything sense I am formatting everyhting... Also, I have a normal harddrive for my storage, do you think there will be any conflicts in that?

---

### Post by Sam on 2005-05-09
[QUOTE=Oblivious Hazard]I am planning on formatting everything, so thats good news... So I wont need to use anything sense I am formatting everyhting... Also, I have a normal harddrive for my storage, do you think there will be any conflicts in that?[/QUOTE]
No problems, you can mix IDE and SATA drives !

---

### Post by DaGGer on 2005-05-09
[QUOTE=Sam]No problems, you can mix IDE and SATA drives ![/QUOTE]
 my team speak doesn't work...when i click it nothing happens...also my counter strike doesn't work....when i start cs it works fine but i don't have sound and i can join a server but when i join a team it freezes

---

### Post by Oblivious Hazard on 2005-05-15
[QUOTE=Sam]No problems, you can mix IDE and SATA drives ![/QUOTE]


I am having problems... my SATA drive works fine... but i can not see my IDE drive.. any suggestions?

---

### Post by Sam on 2005-05-15
Are the IDE in NTFS ? If so, you have to mount them before use, see [here](http://ubuntuguide.org/#windows).


If not, maybe they aren't recognized ?
List every SATA drives:
```
$ ls /dev/sd*
```
List every IDE drives:
```
$ ls /dev/hd*
```
Tell me what outputs.

---

### Post by Oblivious Hazard on 2005-05-15
[QUOTE=Sam]Are the IDE in NTFS ? If so, you have to mount them before use, see [here](http://ubuntuguide.org/#windows).


If not, maybe they aren't recognized ?
List every SATA drives:
```
$ ls /dev/sd*
```
List every IDE drives:
```
$ ls /dev/hd*
```
Tell me what outputs.[/QUOTE]
 oblivioushazard@Tyler:~$  ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5

oblivioushazard@Tyler:~$  ls /dev/hd*
/dev/hdb  /dev/hdb1  /dev/hdc  /dev/hdd

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]oblivioushazard@Tyler:~$  ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5

oblivioushazard@Tyler:~$  ls /dev/hd*
/dev/hdb  /dev/hdb1  /dev/hdc  /dev/hdd[/QUOTE]
If the hdb1 is a Windows partition, follow the instructions [here](http://ubuntuguide.org/#mountunmountntfs) to mount the drive.

I assume that /dev/hdc and /dev/hdd are cd-rom reader/writer. Are they available ? Is so you should see something like:
```
$ ls /media/
cdrom  cdrom0  cdrw cdrom1
```

---

### Post by Oblivious Hazard on 2005-05-15
I thought it was in NTFS but when i did the mount  that you sent me to, on the guide forum, it did not work. 

mount: special device /dev/hda1 does not exist

---

### Post by Oblivious Hazard on 2005-05-15
[QUOTE=Sam]If the hdb1 is a Windows partition, follow the instructions [here](http://ubuntuguide.org/#mountunmountntfs) to mount the drive.

I assume that /dev/hdc and /dev/hdd are cd-rom reader/writer. Are they available ? Is so you should see something like:
```
$ ls /media/
cdrom  cdrom0  cdrw cdrom1
```[/QUOTE]
 oblivioushazard@Tyler:~$ ls /media/
cdrom  cdrom0  cdrom1  windows

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]oblivioushazard@Tyler:~$ ls /media/
cdrom  cdrom0  cdrom1  windows[/QUOTE]
Browse to these directory (insert cds first). It doesn't work ?
Post your /etc/fstab file please

---

### Post by Oblivious Hazard on 2005-05-15
Sorry.... I just installed this the other day.. and i know nothing about this stuff... but i got this error...
bash: /etc/fstab: Permission denied

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]Sorry.... I just installed this the other day.. and i know nothing about this stuff... but i got this error...
bash: /etc/fstab: Permission denied[/QUOTE]
```
$ gedit /etc/fstab
```or```
$ sudo gedit /etc/fstab
```if the first don't work.

---

### Post by Oblivious Hazard on 2005-05-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0[/QUOTE]
Your cd drives are working. For your partition on the IDE drive please follow the instructions for mounting it [once](http://ubuntuguide.org/#mountunmountntfs) or on [boot-up](http://ubuntuguide.org/#automountntfs).

---

### Post by Oblivious Hazard on 2005-05-15
oblivioushazard@Tyler:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
oblivioushazard@Tyler:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
mount: special device /dev/hda1 does not exist


 :???:

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]oblivioushazard@Tyler:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
oblivioushazard@Tyler:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
mount: special device /dev/hda1 does not exist


 :???:[/QUOTE]
/dev/hda1 was an example, your drive is /dev/hdb1
(your IDE drives listing was:
[QUOTE=Oblivious Hazard]oblivioushazard@Tyler:~$ ls /dev/hd*
/dev/hdb **/dev/hdb1** /dev/hdc /dev/hdd[/QUOTE])

You have to do:
```
$ sudo mount /dev/hdb1 /media/windows/ -t ntfs -o umask=0222
```

---

### Post by Oblivious Hazard on 2005-05-15
[QUOTE=Sam]/dev/hda1 was an example, your drive is /dev/hdb1
(your IDE drives listing was:
)

You have to do:
```
$ sudo mount /dev/hdb1 /media/windows/ -t ntfs -o umask=0222
```[/QUOTE]
 youre awsome. Thanks for all your help!

---

### Post by Sam on 2005-05-15
[QUOTE=Oblivious Hazard]youre awsome. Thanks for all your help![/QUOTE]
You're welcome :wink:

---

