---
title: "How can I mount my USB harddisk in rw ??"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by patrick295767 on 2005-09-19
Hi 

I tried : 

mount -t ntfs -rw /dev/sda1 /mnt/sda1
(that i made /mnt/sda1 (the folder))


Plz could someone help me ?

Thx a lot 

patt

---

### Post by mlomker on 2005-09-19
Take a look [at this.](http://ubuntuforums.org/showpost.php?p=355988&postcount=8) Let me know if you have any trouble.

---

### Post by patrick295767 on 2005-09-20
First of all, thank you of your help 
===============


/dev/sda1        /mnt/sda1       ntfs         defaults ... and so on 0   2


I entered that into the file 

did 
mount /dev/sda1 /mnt/sda1

it mounted it ... 
but still only READ 

Maybe rebooting pc ... 
I dont konw what to do 


thanks if you have additional ideas !!

pat '

---

### Post by mlomker on 2005-09-20
> 
mount /dev/sda1 /mnt/sda1


I'd be just **mount /dev/sda1**.

Post the output of this after you mount it:

```

cat /etc/fstab
mount

```

---

