---
title: "[SOLVED] Mount Points for Connect To Server Shares"
date: 2008-11-03
forum: General Help
---

### Post by MikeyDL on 2008-11-03
I've been connecting to windows server shares at work using the "Connect to Server" option in the "Places" menu.  This creates a desktop mount point that I can click into and read/copy/move files from.  However, in some applications (such as Gnomebaker) and others I can't seem to click my way into these shared mount areas.  There doesn't seem to be a reference in the /mnt or /media folders for these shares.  So to burn an ISO on one of these shares I've been manually copying over to my local drive.  Is there a reference for these types of shares on my main / folder that I just don't know about?

Thanks!

---

### Post by Iowan on 2008-11-03
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a way to make a permanent mount - probably not what you had in mind, though,

---

### Post by MikeyDL on 2008-11-03
Thanks!

I'm probably going to permanently mount them, but sometimes I just connect to less used folders and wondered if there were any mount points for those type of quick shares.

---

### Post by FrostyFlames on 2008-11-03
I personally have a few shell scripts that I have to mount my windows 2003 shares. It requires a username and password and I like having them mounted instead of whatever the heck gnome does to mount them (I usually play videos off the shares and some programs hate shares and only like mount points).

Make sure you have some kind of valid mount point in /media. I usually mount my stuff inside a folder called server (/media/server/<shares>). To mount your shares you can do the following.

```
sudo mount -t cifs -o user=<USERNAME_FOR_SHARE>,password=<PASSWORD_FOR_SHARE> //192.168.1.200/<shared_storage_name> /media/server/<shared_storage_name>
```

If your shares don't require a username/password, omit them and the -o. To unmount:
```
sudo umount /media/server/<shared_storage_name>
```

---

### Post by MikeyDL on 2008-11-05
Thanks your suggestion is probably the best idea for my situation.  Creating some scripts to mount shares to /media is probably the best workaround for my situation.  Too bad the nautilus mounts don't show up in allot of the app file open menus cause that would help a bit.

Thanks!

---

