---
title: "How to use new harddrive?"
date: 2008-08-23
forum: General Help
---

### Post by Eyvind on 2008-08-23
Hi! I've just installed another harddrive for my pc, and I used gparted to format it into an ext3 filesystem. But how can I use the disc? I can't see it, and I don't know how to mount it...

Can anyone help me, so I can see and use the disc just as I use the disk were Ubuntu is installed?

Thanks :)

---

### Post by Elfy on 2008-08-23
Hi - can you run

```
sudo fdisk -l
sudo blkid
```

---

### Post by carolinason on 2008-08-23
assuming you formatted it ext3; you need to know disk postion and partition number. you'll find this in gparted probably be something like sdb1

as root or sudo
mkdir /mnt/new_disk
mount -t ext3 /dev/sdb1 /mnt/new_disk

of course you don't have to name it new_disk

---

### Post by Eyvind on 2008-08-23
> **carolinason said:**
> assuming you formatted it ext3; you need to know disk postion and partition number. you'll find this in gparted probably be something like sdb1

as root or sudo
mkdir /mnt/new_disk
mount -t ext3 /dev/sdb1 /mnt/new_disk

of course you don't have to name it new_disk

Ok, I've tried, but it won't work. Or I can't get the rights to do it.
If I'm writing ```
sudo mount -t et3 /dev/sdb1/mnt/data

```
Then it just comes up a list about usage...
If I'm writing just ```
mount -t et3 /dev/sdb1/mnt/data

```
It says that "only root can do that".

---

### Post by Elfy on 2008-08-23
sudo mount -t [COLOR="Red"]et3[/COLOR] /dev/sdb1/mnt/data

should be ext3 :)

Try and post the error message you get with the command you ran it can help.

You know that doing it that way you will need to do it each time you boot.

---

### Post by meindian523 on 2008-08-23
To make it do the mounting automatically every time you boot,add that partition to the /etc/fstab file.Do that by entering ```
gksudo gedit /etc/fstab
```Then,at the end of the file,enter
> /dev/sdb1 /mnt/data ext3 relatime 0 2
Save and exit.

---

### Post by Eyvind on 2008-08-23
Haha! sorry that I forgot the "e[COLOR="Red"]x[/COLOR]t3" :lolflag:

But it still doesn't work. I'm only getting this usage-stuff...

---

### Post by Too Late on 2008-08-23
There must be a space between the device name and the mounting point (directory):
```
sudo mount -t ext3 /dev/sdb1 /mnt/data
```
Btw it should work fine without that "-t ext3" section, too. (It should be able to auto-detect the filesystem.)

---

### Post by Eyvind on 2008-08-23
I think I got it. A folder, data, was created in the mnt-folder, and it was just above 200 GB free space here so it must be the disc.

---

