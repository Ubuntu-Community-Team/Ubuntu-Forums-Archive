---
title: "Partition detection"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by Fintan on 2005-03-21
Hi out there, first off i really the pre 5.04 release. Great install, super quick.
Now for my problem:
After install my ubuntu did not see my partions especialy hda5 where i have most of my data stored. I probably should have done sometrhing at install but i forgot as i have never had to this with other distro installs.
Can someone remind me to hand mount my hda5?

That would be a great help.
Thank you in advance
Fintan

---

### Post by Buffalo Soldier on 2005-03-21
[list=1]
[*]Create a mount point```
$ sudo mkdir /media/anyname
```
[*]Edit your fstab file```
$ sudo gedit /etc/fstab
```
[*]Add this entry*```
/dev/hda5     /media/anyname      ext3       defaults        0       0
```
[*]Remount```
$ sudo mount -a
```
[/list]* Assuming it's an ext3 type filesystem. And not really sure about the last two 0 0.

---

### Post by Fintan on 2005-03-21
Hi buffalo,
 This what i get after doing everthing else:
fintan1@fitanws1:~$ sudo mkdir /dev/hda5
Password:
mkdir: „/dev/hda5“ existiert, ist aber kein Verzeichnis
fintan1@fitanws1:~$ sudo gedit /etc/fstab
fintan1@fitanws1:~$ sudo gedit /etc/fstab
fintan1@fitanws1:~$ sudo mount -a
mount: Einhängepunkt /mnt/hda5 existiert nicht
fintan1@fitanws1:~$ exit
  this is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5 /mnt/hda5 vfat auto,users,exec,defaults,	0	0
/dev/hda9       /               reiserfs notail          0       1
/dev/hda10      /home           reiserfs defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Whats wron?
Greetings and thanks for the quick reply
Fintan

---

### Post by BigRod on 2005-03-21
This should work for 4.1 as well, correct?  I installed it yesterday and it didn't set any of my other partitions (NTFS and FAT32) up for automounting.  I got them setup in my fstab file, but I was having problems configuring them correctly and getting the mount points setup.

---

### Post by alastair on 2005-03-21
"fintan1@fitanws1:~$ sudo mkdir /dev/hda5
Password:
mkdir: „/dev/hda5“ existiert, ist aber kein Verzeichnis"

No - read what he said.

/dev/hda5 is the device/partition!

You want to make a directory to MOUNT it on i.e.

sudo mkdir /mnt/mydata

Then :

mount /dev/hd5 /mnt/mydata

i.e. mount partition /dev/hda5 under /mnt/mydata.

Then, add the fstab lines ...

---

### Post by Buffalo Soldier on 2005-03-21
[QUOTE=Fintan]Hi buffalo,
 This what i get after doing everthing else:
*** fintan1@fitanws1:~$ sudo mkdir *_*/dev/hda5*_**
Password:
mkdir: „/dev/hda5“ existiert, ist aber kein Verzeichnis
fintan1@fitanws1:~$ sudo gedit /etc/fstab
fintan1@fitanws1:~$ sudo mount -a
** mount: Einhängepunkt /mnt/hda5 existiert nicht**
fintan1@fitanws1:~$ exit
  this is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
**/dev/hda5 /mnt/hda5 vfat auto,users,exec,defaults,    0    0**
[/QUOTE]I think you're creating the wrong directory. It should be **sudo mkdir /mnt/hda5**.

---

### Post by Fintan on 2005-03-22
Thanks guys, that worked, my mistake. As i said it's been a while.

Thanks agin
Greets
Fintan

---

### Post by kb00heda on 2005-03-22
Regarding the /etc/fstab file:

I added two HDDs in my own file the other day. I have really no idea what options to set for them? I put in "auto" just to make them be mounted automatically at startup. I saw that my other drive, the one where Ubuntu is installed, has options

defaults,errors=remount-ro

and get mounted at startup, i.e., without the "auto" option. When is the "auto" option needed? Should I add "defaults" as well, making it "defaults,auto"?

/David

---

### Post by alastair on 2005-03-22
See : man 8 mount  (-o options section)

It tells you what options "auto" is equivalent to.

I tend to only use "noauto" if I do not want to automatically mount a disk at boot.

Using "dafaults" alone is generally fine for normal usage.

---

### Post by kb00heda on 2005-03-23
Thanks (again!) alastair!

Should have checked the man pages myself ... I guess I was lazy by habit. Stupid thing!  :)

Think I will go with "defaults" in the end.

/David

---

