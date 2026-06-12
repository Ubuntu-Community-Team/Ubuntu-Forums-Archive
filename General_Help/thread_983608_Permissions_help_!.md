---
title: "Permissions help !?"
date: 2008-11-15
forum: General Help
---

### Post by Comzee on 2008-11-15
I have Ubuntu 8.10 installed on my master harddrive mounted as /dev/sda. I have a second drive set to slave mounted as /dev/sdb. For some reason only root has permissions to /dev/sdb drive which would be my 320gb harddrive. Can somebody give me a chmod command to give my account (comzee) permissions to the /dev/sdb mount.

Thanks in advance!!

---

### Post by Mardoct909 on 2008-11-15
```
gksudo nautilus 
```

Opens the file browser as root. Navigate to the drive and change permissions graphically.

---

### Post by taurus on 2008-11-15
It should be /dev/sdb1, not /dev/sdb.  What filesystem is /dev/sdb1 and where do you mount it?  

Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by Comzee on 2008-11-15
Yea it is /dev/sdb1 sorry and /dev/sda1. I changed the permissions in nautilus. I should probably read a chmod tutorial though :/ !

Thanks for the help though!

---

### Post by Mardoct909 on 2008-11-15
```
man chmod
```

Documentation to the rescue! man <command here> will give you info on it.

---

