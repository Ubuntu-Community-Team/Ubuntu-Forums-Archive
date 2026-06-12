---
title: "change permissions for my 2nd hard drive"
date: 2008-11-19
forum: Hardware
---

### Post by cnaqe1 on 2008-11-19
How can i change the permissions for my second hard drive so i can add music ,videos and pics to it.  Can any one help me? thanks

---

### Post by dabl on 2008-11-19
Drives are normally owned by root, by design and for good reasons.

Probably what you need to do is make a directory (aka "folder") on that drive for your music, and set the ownership of the folder to the users (aka you).

How?

Assuming your drive is mounted at /media/disk2, open your console window and 

```
cd /media/disk2
``` {Enter}

```
sudo mkdir music
``` {give password}{Enter}

```
sudo chmod 777 music
```

That's it.  Exit the console, open the /media/disk2/music folder and have fun.  :guitar:

---

### Post by taurus on 2008-11-19
What is the filesystem of that second harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

