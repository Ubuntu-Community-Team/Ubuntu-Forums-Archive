---
title: "Resizing my / (reiserfs) partition..."
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by zond on 2005-07-27
](*,)  Hello, I need to add more space to my ubuntu but i don't want to have to reinstall it.
I have a hd in this situation:

## Windows C (10GB) ## Windows D (5GB) ## Swap ##  Ubuntu 5GB ## Free 10 GB  ##

I'd like to know if i can add that 10GB so ubuntu become 15 GB. Can it be done with LVM?? If yes, how?? 

Tks a lot.

---

### Post by jones_jj on 2005-07-27
zond-

Is that 10 GB free space formatted or is it still unformatted?  I would just mount that last 10 GB of free space and go from there.  So you will have 5 GB for Ubuntu and an extra 10 GB that you could call /files or whatever you wish to call it.

Run fdisk on that unused partion:  fdisk /dev/hdxy, where "x" is either a for primary, b for secondary, and "y" stands for the partition.  To get a listing of all of the options type "m"

After creating the partition if it is not created you will want to mount the partition.  You will probably want to have mount on start up.  To mount you would do:  mount -t <filesystem> /dev/hdxy /mnt/<whaterver you want to name it>.  To get this to mount on bootup you will have to modify the fstab file.

I hope this kind of helps.

---

### Post by zond on 2005-07-28
Tks, but I know the mount stuff, i think I wasn't clear.

What I wanna do is resize the space of the / partition.
Do you know how (without data losings)??

Sorry about my english... i'm brazilian...
TKS!!

---

### Post by Soulfly on 2005-07-28
Are you using LVM (which Ubuntu install lets you do).. Then it's your lucky day, just extend the logical volume with lvextend, then resize the filesystem. With some filesystems (like reiserfs) you can even do it while the filesystem is online.

[http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

---

### Post by zond on 2005-07-29
[QUOTE=Soulfly]Are you using LVM (which Ubuntu install lets you do).. Then it's your lucky day, just extend the logical volume with lvextend, then resize the filesystem. With some filesystems (like reiserfs) you can even do it while the filesystem is online.

[http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html)[/QUOTE]
 Actually I found a very easy way to do it:
I just booted mandriva installantion cd and used its partition manager!!
No data losses!! Very easy!!

---

