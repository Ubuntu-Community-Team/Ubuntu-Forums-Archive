---
title: "Swap memory NOT working ?"
date: 2008-08-08
forum: General Help
---

### Post by Masterart on 2008-08-08
I resized the swap space using Partition editor. ( swapoff ,resize .....)

Now swap memory is TURNED OFF BY DEFAULT when I boot to ubuntu :(.

I have to turn it on with parted > swapon everytime.

somebody knows what went wrong ?

---

### Post by dje on 2008-08-08
please post the output of the following commands from a terminal (applications >> accessories >> terminal):
```
cat /etc/fstab
```
and
```
sudo blkid
```

dje

---

### Post by Masterart on 2008-08-08
etc/fstab says :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c58f606a-4e40-440e-83f6-e5613b992669 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=f0613dcc-63aa-423a-ae3d-95b945d2af9a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

blkid says :

```

/dev/sda1: UUID="E484781E8477F182" LABEL="xxxxxxx" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="cbb1946f-b2d5-40e2-a6ec-90a6127d189f" 
/dev/sda3: UUID="01C8641B13414B80" LABEL="xxxxxxxxx" TYPE="ntfs" 
/dev/sda4: UUID="c58f606a-4e40-440e-83f6-e5613b992669" TYPE="ext2" LABEL="xxxxxxx" 


```

---

### Post by dje on 2008-08-08
ok do the following in a terminal:
```
gksu gedit /etc/fstab
```
now replace this line (underneath "# /dev/sda2"):
> UUID=f0613dcc-63aa-423a-ae3d-95b945d2af9a
with this:
> UUID=cbb1946f-b2d5-40e2-a6ec-90a6127d189f
save and close the file and then do:
```
sudo swapon /dev/sda2
```
OR reboot

dje

---

### Post by Masterart on 2008-08-08
Yays. that works now. thanks.

BTW: linbaku project looks interesting.

---

