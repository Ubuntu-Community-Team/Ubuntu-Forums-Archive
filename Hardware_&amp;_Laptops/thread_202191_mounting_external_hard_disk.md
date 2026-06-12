---
title: "mounting external hard disk"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by DSABH on 2006-06-23
hey,

im running ubuntu linux on my acer laptop. 
ive got a 3.5' hard disk which i put in an hard disk case so i can link it via usb to my computer. ubuntu detects it automatically but since i come from windows this hard disk has ntfs format which means that i can read but not write on it.

i copied the content from one partition to a local one on my laptop so i can format the partition and convert it to ext3. i did so and it worked out, but the userrights are set to root which means i can access the disk but not write on it.. how can i fix the problem??

---

### Post by oldmanstan on 2006-06-23
ok, i'm really not sure if this is such a hot idea for a drive but i did this with a scanner once. if you change who "owns" the device itself you can then use it when you are logged in as your regular user. so if your usb harddrive is /dev/hdc type
```
sudo chown /dev/hdc
```
get some confirmation on whether that is a bad idea or not before you try it though, it won't wreck anything up or anything like that but it might make the system less secure.

i think that should solve your problem, you might also want to look at where it is being mounted, you may need to change some permissions on its mount point

did you try looking up usb harddrives in the wiki?

---

### Post by DSABH on 2006-06-23
hey,

i did search at the wiki, without success, however.

thanks for your reply, first of all. but actually i want to set specific user rights for a certain user - not for all.

can anyone help again?

---

### Post by oldmanstan on 2006-06-23
well when you use chown you don't change the permissions, you just change who "owns" the device, which in this case would be your user

you could also use chmod which would change the permissions but then you would have to give everyone the right to use it if you wanted to be able to use it as a non-root user

---

### Post by DSABH on 2006-06-24
hey

```
sudo chmod -c 0777 /media/usbdisk/
```

solved the problem

---

