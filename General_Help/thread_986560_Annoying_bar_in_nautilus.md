---
title: "Annoying bar in nautilus"
date: 2008-11-18
forum: General Help
---

### Post by t4ggs on 2008-11-18
Hi, I'm having this annoying bar (see attached picture) when opening one of my ntfs partitions, the bar says: "These files are on a Picture CD" and then theres is a button that says: "Open F-Fpot"

So what i did first was unninstalling  F-Spot...but then the button says: "Open Brasero Disc Burning"

So i thought its maybe a problem with my partition, but I have other 3 ntfs partitions and the don't have the same issue....here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb8 :
UUID=da944462-d3b9-4c05-952c-49d8f3c7fcf1	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb9 :
UUID=2cc309ce-9819-4a69-a649-10d6f587c583	/home	ext3	relatime	0	2
#Entry for /dev/sdb6 :
UUID=2DAD34E22227FDBC	/media/Cruci	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=C53008BF82A12446	/media/Data	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=1278B11378B0F717	/media/Windows_HD	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb7 :
UUID=a03d762d-e6c4-4f0a-b28f-6ca1d9b650fa	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


```

The partition I'm having this problem with is sdb5 or Data.... but as you can see it has the same parameter as the other two partitions...

I thought that it's maybe  nautilus..but when doing sudo nautilus, I don't see the bar.. so I'm getting crazy and i don't know what it is...anyone have an idea?? thank u...

---

### Post by Marius Derekus on 2008-11-18
It looks like a KDE desktop enviorment (I use GnOME) so i couldn't help much, go to the top of the screen and click edit>prefrences, maybe there's somthing you can change in there.

---

### Post by t4ggs on 2008-11-19
no, it is gnome, I'm using ubuntu intrepid

---

### Post by Marius Derekus on 2008-11-19
Oh, well did you try what i said (If that doesn't work i don't know if i can help anyway, it looks like a default thing that will always be there. It was probably added for intrepid.)

---

### Post by kpkeerthi on 2008-11-19
Rename the folder 'Pictures' to something else (Photos ?) and the bar will be gone **after reboot**. I remember a bug report being filed in launch pad.

---

### Post by t4ggs on 2008-11-19
u r right, thank u
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936)

---

