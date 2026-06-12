---
title: "How Do I remove Write Protection from Flash Drive"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by netgeeks on 2009-10-15
My Flash Drive got Write Protected after I ran Partition Editor and formatted it as FAT32 on Ubuntu. I can no longer access the drive on Ubuntu nor Windows Vista.  What can I do to make it work once again?  It worked previously before I tried to make an Ubuntu Bootable USB.

---

### Post by foerno on 2011-07-11
I'm having the same problem right now. What can I do?

---

### Post by ottosykora on 2011-07-11
I am having the same problem since update to 10.10, all advises given by many people failed to cure the problem properly.

---

### Post by Awes0meSauce on 2011-07-11
I'm a bit of a noob myself, but I think it would help if you found where your flash drive is mounted first. It should be in the /dev directory. If you open My Places you should see it listed on the left hand side. Click on it, then right click, and then click properties. It should give you the location /dev/XXXX
 
Then run the command:
 
```
ls -l /dev/XXXX
```Replacing XXXX with the actual location. 
 
You should get a listing like this:
 
```
-r-xr-xr-x      1 root    root   1000  Jul  11 10:20 file1
```Devices such as flash drives are simply files themselves so I would imagine that you could change the permissions using the command:
 
```
chmod
```If you want write permissions you'll have to change the existing permissions. To do this you can use numbers as it's much faster.
 
```

r or read = 4
w or write = 2
x or execute = 1

```So if I wanted write permissions for file1 I would run:
 
```
chmod 775 file1
```That's basically saying that with the first 7 I want to give the **user** (that would be me) rwx permissions. The second 7 gives the **group**  (if there are other accounts on my system that are in the same group as me) rwx permissions. And finally the 5 would give everyone else, or **Other**, only r and x permissions.
 
You'll most likely need to do this as root so use:
 
```
sudo
```Hope that helps :D

---

