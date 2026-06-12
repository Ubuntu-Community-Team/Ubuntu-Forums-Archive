---
title: "Sharing between vista &amp; ubuntu"
date: 2008-08-26
forum: General Help
---

### Post by Fxy on 2008-08-26
Hi recently i installed the latest version of ubuntu on my laptop dulebooting alongside vista. My problem is that i want to be able to view my vista folders in ubuntu without having to place them in my vista shared folder. You help will be much apprichated :)...

---

### Post by WRDN on 2008-08-26
Can't you view all files on the Vista partition? Click Places > Computer then select the drive/ partition with Vista on it. If it doesn't show up there, open the Terminal and type:

```
sudo fdisk -l
```

Identify the Vista partition (easy to identify usually using the filesystem type e.g. NTFS).

Now, create a mount point by typing:

```
sudo mkdir /media/vista
```

Finally, mount the drive by typing:

```
sudo mount /dev/[device] /media/vista
```

---

### Post by lackoblacko on 2008-08-26
you can mount the partition in ubuntu to view your vista drive.

sudo fdisk -l
sudo mount [vista device] [where you want to mount]

---

### Post by Fxy on 2008-08-27
Sry guys i got it sorted my windows folders come under "HOST" is ubuntu...  So now i can view all my vista files etc etc under ubuntu :)...

---

