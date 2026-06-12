---
title: "Problem with ubuntu recognizing my external hard drive"
date: 2008-10-17
forum: General Help
---

### Post by Natpjohnson on 2008-10-17
I have searched through many threads like this however i cannot find a solution.  I have a 80gb seagate external hard drive.  I dont know if it is fat or ntfs. I don't know the name of the drive because it won't show up on my computer.  Im pretty much new to ubuntu, and I'm sorry for the lack of information but i don't know how to retrieve any.  Any suggestions are very much appreciated.

---

### Post by Fixman on 2008-10-17
> **Natpjohnson said:**
> I have searched through many threads like this however i cannot find a solution.  I have a 80gb seagate external hard drive.  I dont know if it is fat or ntfs. I don't know the name of the drive because it won't show up on my computer.  Im pretty much new to ubuntu, and I'm sorry for the lack of information but i don't know how to retrieve any.  Any suggestions are very much appreciated.

Does the hard drive hace any data?

---

### Post by jerome1232 on 2008-10-17
With the hard drive plugged in what's the output of this command

```
sudo fdsik -l
```

---

### Post by jhernandez1270 on 2008-10-17
> **jerome1232 said:**
> With the hard drive plugged in what's the output of this command

```
sudo fdsik -l
```

After this you should see something like:
/dev/sda1
/dev/sda2
/dev/sda3

and then a drive like

/dev/sdb1 (This should be your external)

then get gparted installed
with code:

sudo apt-get install gparted

go to System > Administration > Partition Editor

in the upper right-corner there is a pull-down menu that says /dev/sda
click it and select /dev/sdb

it will give you all the info you need and even let you delete and reformat (SO BE CAREFUL)

---

### Post by Natpjohnson on 2008-10-17
> **jhernandez1270 said:**
> After this you should see something like:
/dev/sda1
/dev/sda2
/dev/sda3

and then a drive like

/dev/sdb1 (This should be your external)

then get gparted installed
with code:

sudo apt-get install gparted

go to System > Administration > Partition Editor

in the upper right-corner there is a pull-down menu that says /dev/sda
click it and select /dev/sdb

it will give you all the info you need and even let you delete and reformat (SO BE CAREFUL)
K thx that really does help so now i know its not my hard drives problem.  But now how to i use it like an external hard drive?
it says theres 29.45 gb use of it its a fat32.  Now i just need to be able to use it.

---

### Post by jerome1232 on 2008-10-17
all right well it should be auto-mounting itself to /media/disk and show up on your desktop but since it's not let's try a few things

manually mounting a drive, I'll pretend your drive is /dev/sdc1

```
sudo mkdir /media/mydisk
sudo mount /dev/sdc1 /media/mydisk -o umask=000
```

---

### Post by Natpjohnson on 2008-10-18
when i do that i get:
mount: you must specify the filesystem type

how do i specify that? i know its a ntfs.

---

### Post by sparky-steve on 2008-10-18
Hi

try

```
sudo mount /dev/sdc1 /media/mydisk -t ntfs -o umask=000
```

It's been a while since I had any NTFS drives; From memory you may need to install ntfsprogs

```
sudo apt-get install ntfsprogs
```

---

### Post by jerome1232 on 2008-10-18
Try adjusting the mount command to

```
sudo mount -t ntfs-3g /dev/sdc1 /media/mydisk -o umask=000
```

---

