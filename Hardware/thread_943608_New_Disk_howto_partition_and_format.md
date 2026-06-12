---
title: "New Disk howto partition and format"
date: 2008-10-10
forum: Hardware
---

### Post by fj1200 on 2008-10-10
Hello
My harware:
I have just installed a new controllercard (sunix sata4000 It neaded a new bios to work used dos and now its working i think, at least my computer a HP VL400 found the disk's) and 2 1Gb samsung sata disks.
After searching the forum i really dident find what i was looking for:

The question:
How do i partition and format a new disc in Ubuntu/Kubuntu 7.10, can i do that in X?

Weird stuff:
One disc is /dev/fd0 and the other is /dev/sd1

---

### Post by caljohnsmith on 2008-10-10
Have you tried using the Ubuntu partition editor? If you press ALT + F2 from the desktop, type:
```
gksudo gparted
```
You can run that from the Ubuntu live CD.

---

### Post by cariboo on 2008-10-10
You can use gparted to partition and format your hard drives. If you haven't installed gparted it is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it. Once you have installed it you can find it under System-->Administration-->Partion Editor

Jim

---

### Post by fj1200 on 2008-10-10
Im using Kubuntu.
So i used  "apt-get install gparted" to install it and "sudo gparted" to run it from a shell/promt.
The disc's was shown as /dev/sdb and /dev/sdc.
And im formating them to ext3.
I Know that raiserfs is superior but can someone please explain in short why?
And the + and - of these filesystems. (like: + safe relilable - cant defrag)

Thank you for the fast and accurate replies!


PS: this maby will fit better in the newbie forum, if so, move it please.

---

### Post by fj1200 on 2008-10-10
Hello again.
There still strange things going on whit my computer...
gparted says there's a new /dev/sdb and a new /dev/sdc.
But kde calls it /dev/sdc and /dev/scd......
Whats going on???

---

### Post by fj1200 on 2008-10-10
Im still stuck.........
How can i trust the filesystem?
2Gb and it still seams random, what is the mount point?
What am i mounting?
Can i read my disc's?
This feals really buggy!

---

### Post by cariboo on 2008-10-11
In a terminal type:

```
sudo fdisk -l
```

This will show the correct device numbers. Then to mount the partition in a terminal type:

```
sudo mount /dev/sdc1 /media/disk
```

I haven't used KDE for several years, but I'm sure there is some sort of auto mounter, do the partitons show up in your file manager?

Jim

---

### Post by fj1200 on 2008-10-11
xbox@xbox-desktop:~$ sudo fdisk -l | /home/xbox/xbox.txt
bash: /home/xbox/xbox.txt: Filen eller katalogen finns inte

VARNING: GPT (GUID Partition Table) upptäcktes på "/dev/sdb"! Verktyget fdisk saknar stöd för GPT. Använd GNU Parted.


VARNING: GPT (GUID Partition Table) upptäcktes på "/dev/sdc"! Verktyget fdisk saknar stöd för GPT. Använd GNU Parted.


Sorry, im from Sweden so this may be mumbo-jumbo...
but cant i pipe the answer to a file?

xbox@xbox-desktop:~$ sudo gparted
======================
libparted : 1.7.1
======================

xbox@xbox-desktop:~$ I rightklick on the volyme and chose format ext3 and nothing happens

---

### Post by fj1200 on 2008-10-11
sudo mount /dev/sdb1 /home/share/disk1
mount: okänd filsystemstyp "LVM2_member"

---

### Post by fj1200 on 2008-10-12
Hello again.
I feal a bit stupid for missing the green V in gparted.
But now that i know of it there's a new problem, when i start to format the computer hangs.
After about 30sek after the formating started it time for a hard reboot.

Does anyone know if theres a limit for a partition size? (ext2)
Can this be something about the controller is SATA150 and the discs SATA300?

---

