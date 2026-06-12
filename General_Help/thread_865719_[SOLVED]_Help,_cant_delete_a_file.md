---
title: "[SOLVED] Help, cant delete a file"
date: 2008-07-20
forum: General Help
---

### Post by Drizzel on 2008-07-20
I used alien to convert a rpm file to a deb file so I could use it on ubuntu.. In the process of converting, it left a file on my desktop that I cannot delete. It has a lock on the icon and everytime I try to delete it I get a permission denied error. What can I do to get rid of this file?

---

### Post by PurposeOfReason on 2008-07-20
Get root permissions to delete it. In a command line do a 
```
sudo rm /home/USERNAME/Desktop/FILE
```if it's a folder it'd be
```
sudo rm -rf /home/USERNAME/Desktop/FILE
```

You could also 
```
gksudo nautilus
``` for a GUI solution.

---

### Post by Drizzel on 2008-07-21
Thank you so much :) The command worked, Thanks for giving me the command for both folders and files. /me saves.

I did however try to do it via Nautilus first and got an error which is pasted below. When nautilus did finally come up it didnt show the file I wanted to delete. Is there something wrong with my Nautilus installation? I noticed I dont have a shortcut to Nautilus anywhere and it doesnt show up under the applications menu. That normal?


Initializing nautilus-share extension

** (nautilus:9566): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///

(nautilus:9566): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:9566): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown

---

### Post by CatKiller on 2008-07-21
> **Drizzel said:**
> I noticed I dont have a shortcut to Nautilus anywhere and it doesnt show up under the applications menu. That normal?

Perfectly normal. All of those shortcuts in the Places menu will open Nautilus. If you especially wanted one, you could right-click on the Menu, select Edit Menus and tick the box next to File Browser in Accessories. It's exactly the same as Places -> Home, though.

---

### Post by enchance on 2008-07-21
Darn. PurposeOfReason beat me to it. :)

---

### Post by Potatoj316 on 2008-07-21
You should be careful with that sudo rm -rf command, the f forces it to delete everything in the directory without asking for your permission.  I would sugest using a sudo rm -r to delete directories.

---

### Post by Drizzel on 2008-07-21
Thanks for all the help guys. Learning more everyday.. This is a great community! :)

---

