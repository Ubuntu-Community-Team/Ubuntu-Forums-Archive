---
title: "How to mount ext4 formatted volume"
date: 2008-11-25
forum: General Help
---

### Post by RMSe17 on 2008-11-25
Hi, I formatted an external iscsi volume as ext4 by using 
sudo mkfs.ext4 /dev/sda1

but when I go to mount it, I get an error, something about ext4 not being recognized by mount..

I tried  
sudo mount -t ext4 /dev/sda1 /iscsi  

and got an error saying that it does not know ext4 type.  Is there a special mount command for ext4?  I assume if mkfs supports ext4, so should some mount command?

Thanks for your help.
RMSe17

---

### Post by RMSe17 on 2008-11-25
This is on Ubuntu 8.10 32bit btw, I didn't specify...

---

### Post by crazyness003 on 2008-11-25
> **RMSe17 said:**
> This is on Ubuntu 8.10 32bit btw, I didn't specify...

according tot he wiki on wikipedia, ext4 should be backwards compatable as long as the 'extents' feature is not used. See [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4). Other than that...i have no idea

---

### Post by z35 on 2008-12-04
tune2fs -E test_fs /dev/sda1

---

### Post by psusi on 2008-12-05
It is "ext4dev" not "ext4", because it is still in development and it's use is discouraged.

---

