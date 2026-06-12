---
title: "moving data directories"
date: 2008-11-09
forum: General Help
---

### Post by sardamil on 2008-11-09
I've got a second HDD. I still need to find out how to format and partition it, but that's not the reason for this post. I just need to check the help on that. I want to use this HDD to store my data.I'd like to move the current music- and other directories in my user directory to this new HDD, while retaining the current links. For example, if I'd go Places --> Music I'd end up on my music directory on the second HDD. Is that possible? Can I just move the directory?

Thanks for your help.

---

### Post by sardamil on 2008-11-10
I thought this was a beginner question. Or is everybody so swamped with questions, my question is burried by the load of questions? :confused:

---

### Post by justleen on 2008-11-10
you could create a symbolic link from /home/user/Music to the new drive.

---

### Post by geirha on 2008-11-10
Or, after moving it, open a nautilus window. In the left frame you will see all the bookmarks you have in the places menu. Right click Music and delete it, then browse to the place you moved the Music folder to and drag the Music folder to the left frame to create a new bookmark.

---

### Post by sardamil on 2008-11-12
Thanks.
Now I only need to find out how to grant myself permissions to the disk. Or better, how to login as root and grant permissions to my user.
*feeling like a true n00b* :(

---

### Post by geirha on 2008-11-12
Which filesystem did you make on it? ext3? fat32?

If ext3, then it is by default only writeable by root. If you are the only one who needs write access to it, simply set yourself as the owner of the drive. If you prefer gui, hit Alt+F2 and run "gksu nautilus" to get a nautilus window with root privileges (be careful). Browse to the mountpoint, typically inside /media (Filesystem -> media), right click the mountpoint, choose properties, then set your self as owner in the Permissions tab.

In the terminal you would do:
```
sudo chown $USER /media/*mountpoint*
```

---

### Post by sardamil on 2008-11-16
thanks, that helped me a lot.

---

