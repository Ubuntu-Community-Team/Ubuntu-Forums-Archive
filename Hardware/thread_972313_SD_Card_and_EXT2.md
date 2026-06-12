---
title: "SD Card and EXT2"
date: 2008-11-05
forum: Hardware
---

### Post by ratman99uk on 2008-11-05
Iv just tried formating an 2gb sd card to EXT2, however afterwards I don't have permission to write to the card. I use the following command to change the file system:

sudo umount /dev/mmcblk0p1
sudo mkfs.ext2 -L flashcard /dev/mmcblk0p1

How do I give all users permission to write to the card or just my account.

Im using a Dell Inspiron Mini 9 running Ubuntu 8.10.

Thanks
Ratman99UK

---

### Post by Coreigh on 2008-11-05
```
sudo chmod 777 /<mountpoint>
```

Where <mountpoint> = path to where the disk is mounted.

This gives *everyone* read/write access to the folder.

---

### Post by ratman99uk on 2008-11-05
Thanks for getting back to me so fast.
i entered the following:

sudo chmod 777 /media/flashcard

however the permissions tabs still says I am not the owner so can not change any permissions.

> **Coreigh said:**
> ```
sudo chmod 777 /<mountpoint>
```

Where <mountpoint> = path to where the disk is mounted.

This gives *everyone* read/write access to the folder.

---

### Post by Coreigh on 2008-11-06
Is the card removable? You have the computer started up and you are logged in and then you pop the card in and it auto-mounts in /media/flashcard.
You open the file browser (Nautilus) and got to the /media directory and right-click on the flashcard directory and choose Properties. Under the Permissions tab who is listed as Owner? and does that person have "Create and Delete Files" selected as folder access?

If you are not listed as the owner you can try this```
sudo chown username.username /media/flashcard
```
Important to note there is NO TRAILING / and username = your username

chown is the change owner command

---

### Post by ratman99uk on 2008-11-06
Thanks for your help
Using:
sudo chown username.username /media/flashcard
worked great.

Just so I understand, To repeat this process again in the future I need to: 
sudo chmod 777 /media/flashcard
folowed by:
sudo chown username.username /media/flashcard

having the effect of first changing the mountpoint permissions and secondly making me the owner of the mountpoint?

Is this correct?

Thanks Again
Ratman99UK

---

