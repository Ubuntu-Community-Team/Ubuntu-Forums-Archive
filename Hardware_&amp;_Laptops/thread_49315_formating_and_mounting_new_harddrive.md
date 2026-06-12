---
title: "formating and mounting new harddrive"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by wingdom on 2005-07-15
i finally got my 2nd harddrive to show up in linux, i still need to format and mount it, but, there is still stuff onthe harddrive that i want to get off. if i reformat it, it will erase all the stuff on it, wont it? is there any way to get this stuff off this harddrive and on to my primary one?

i will take the instructions on formating and mounting it, so i dont have 2 ask again, but i need 2 get sum stuff off that hdd first.

---

### Post by badrinarayan on 2005-07-15
I guess you have a few windows partitions on your second hard drive. First, open a Terminal (Applications > System Tools > Terminal) and type

```
sudo fdisk /dev/hdb
```

Give your password. Type **p** and obtain the list of partitions, **q** to quit.
Then you may mount the partitions you desire (Your C:, D: etc., will show up as partitions /dev/hdb1 /dev/hdb2 etc., whiich you can **mount** in a directory and examine the contents.

Here's some help: [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs) Alternatively, you could post the result of your fdisk command and we could help you with mounting, partitioning etc.,

Regards
Badri

---

### Post by wingdom on 2005-07-15
```
Disk /dev/hdb: 8037 MB, 8037679104 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         933     7494291   83  Linux
/dev/hdb2             934         977      353430    5  Extended
/dev/hdb5             934         977      353398+  82  Linux swap / Solaris
```

alright, cool, mounting time i guess, right?

---

### Post by badrinarayan on 2005-07-15
Alright!
```
sudo mkdir -m 777 ~/hdb1
sudo mount /dev/hdb1 ~/hdb1
```

Now navigate to your home directory, locate the hdb1 directory and copy away...

Simple, ain't it?

Regards
Badri

---

### Post by Wide on 2005-07-15
You could insted of adding to your fstab, Just mount the partition you want, if you add the partition with the boot sector of the windows,  you may not be able to boot.


What I do is very simple, first see what partitions you have


with


```
sudo df -T -h
``` 


Then choose what partition you want to mount


with  


```
sudo mount /dev/hdb2  /media/windows -t vfat
``` 


Of course change the "/dev/hdb2" to whatever partition you want.


Hope this helps 


:grin:

---

### Post by badrinarayan on 2005-07-15
[QUOTE=Wide]You could insted of adding to your fstab, Just mount the partition you want, if you add the partition with the boot sector of the windows,  you may not be able to boot.

What I do is very simple, first see what partitions you have

with

```
sudo df -T -h
``` 

Then choose what partition you want to mount

with  

```
sudo mount /dev/hdb2  /media/windows -t vfat
``` 

Of course change the "/dev/hdb2" to whatever partition you want. ;-) 

Hope this helps 
:grin:[/QUOTE]

His second hard drive does not have windows partitions... ;-)

---

### Post by wingdom on 2005-07-15
theyre mounted, but theres nothing in them. i dont see anything, and it says theres no files in it

---

