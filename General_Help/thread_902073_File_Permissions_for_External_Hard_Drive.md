---
title: "File Permissions for External Hard Drive"
date: 2008-08-27
forum: General Help
---

### Post by da1bu on 2008-08-27
Hi everyone. I'm still new to Ubuntu and need to copy files to my external hard drive but under properties-permissions it says that the permissions could not be determined.

When i try to drag files in the hard drive it says i don't have the permissions. Do i have to mount the drive / use sudo followed by a command? 

Any help appreciated, thanks.

---

### Post by Comzee on 2008-08-27
The easiest way to get past file permission is run Nautilus as root, Nautilus being the default file manager for Ubuntu. 

```
sudo nautilus
```

Then where your external harddrive will be mounted is in the /media directory.

---

### Post by sisco311 on 2008-08-27
> **da1bu said:**
> Hi everyone. I'm still new to Ubuntu and need to copy files to my external hard drive but under properties-permissions it says that the permissions could not be determined.

When i try to drag files in the hard drive it says i don't have the permissions. Do i have to mount the drive / use sudo followed by a command? 

Any help appreciated, thanks.

What kind of file system is on the hard drive?

Which version of ubuntu are you using?

---

### Post by jerome1232 on 2008-08-27
> **Comzee said:**
> The easiest way to get past file permission is run Nautilus as root, Nautilus being the default file manager for Ubuntu. 

```
sudo nautilus
```

Then where your external harddrive will be mounted is in the /media directory.

I would never recommend running nautilus as root, it's much better to learn how to properly mount and/or depending on the filesystem chown/chmod it so that it can be used normally.

---

### Post by Comzee on 2008-08-27
> **jerome1232 said:**
> I would never recommend running nautilus as root, it's much better to learn how to properly mount and/or depending on the filesystem chown/chmod it so that it can be used normally.



I said the easiest way. Which it is.

---

### Post by sisco311 on 2008-08-27
> **jerome1232 said:**
> I would never recommend running nautilus as root, it's much better to learn how to properly mount and/or depending on the filesystem chown/chmod it so that it can be used normally.

+1

and to run GUI applications as root use *gksu*.
ex.:
```
gksu nautilus
```

---

### Post by Comzee on 2008-08-27
> **sisco311 said:**
> +1

and to run GUI applications as root use *gksu*.
ex.:
```
gksu nautilus
```

I've never even heard of gksu, I guess I'm a noob :(. +1 for him, does that mean -1 for me? >.>

---

### Post by sisco311 on 2008-08-27
> **Comzee said:**
> does that mean -1 for me? >.>
+2 for you if you read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) :)

---

### Post by Comzee on 2008-08-27
> **sisco311 said:**
> +2 for you if you read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) :)

I now know the horrors of corrupting .ICEAuthority,thanks for the info. I'll start using gksudo for Gui stuff now!  :D

---

### Post by da1bu on 2008-08-27
lol thanks for the replies but i'm a little confused.

I'm using Ubuntu 8.04 and the file system is hfsplus, and yes it is mounted in the media directory.

Do i use gksu nautilus or sudo nautilus followed by the directory?

---

### Post by bryncoles on 2008-08-27
for graphical apps use gksu or gksudo (i use gksudo). this will open a file browser where you can fight your way to the folder and edit it to your hearts content. 

if you're using the default ubuntu window manager, you can also try using ```
gksudo nautilus
``` and taking yourself to the /media folder. right click the external hard-drive, selecting properties and change them so that you are the owner, and have read and write permissions. save those changes and (if ive remembered how to do that correctly) you wont need to use gksudo nautilus again. 

also: open a terminal and type ```
man chmod
``` this incomprehenisble gibberish is the instructions for changing file permissions in the terminal!

what this means for you is when you have a file / folder you dont have permission to access, open a terminal and type 

```
chmod u+rw -R 'FilePathToFolder'
```

where chmod changes the permissions of the file or folder, for you as the user (u), giving read and write access (+rw) recursively to the folder and all its sub-folders (-R). the easiest way to get the file path is to just drag and drop the file you're changing permissions to from the desk top into the terminal after you have typed ```
chmod u+rw -R 
```

hope thats clear and correct and useful to you!

---

