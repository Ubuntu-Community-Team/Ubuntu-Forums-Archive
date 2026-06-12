---
title: "Removing locked folders from &quot;home&quot;"
date: 2008-07-27
forum: General Help
---

### Post by rtrdom on 2008-07-27
Tried installing Office2000 collection from CD to wine. It is now stuck
as a folder in the home directory. Cannot remove it or purge using
either apt-get or aptitude. How can I remove the (four) folders with padlocks from the home directory? Any help appreciated.

---

### Post by JasonWalton on 2008-07-27
The "lock" just means that the folders are either write protected or are owned by another user.  If you can find the folders in a terminal window, then you can delete them with:

  sudo rm -rf [foldername]

Be careful with "rm -rf".  If you do "rm -rf /", it will delete everthing on your hard drive.  This is the power tool of file deletion.

---

### Post by NineseveN on 2008-07-27
If you right click on the folders and select properties, there should be a "permissions" tab. The padlock means you don't have write access to it.

Give yourself access to create and delete files in the drop down options instead of access only. Click the button at the bottom of that tab that says "apply permissions to enclosed files".

Then delete away.

---

### Post by AnonCat on 2008-07-27
You can also go to the terminal and type:

sudo nautilus

That will bring up the file manager window again with the permissions to delete any files and directories.

---

### Post by cariboo on 2008-07-27
Using Alt-F2 then entering:

```
gksu nautilus
```

Will open Nautilus as root, you can delete locked folders and files.

Jim

---

### Post by todlangweilig on 2008-07-27
If you use nautilus as root, don't forget to empty the trash while you are at it, to recover your disk space. When deleting as root, the files won't show up in the normal user trash bin. 

Or from the command line, using the interactive flag, just to be extra safe:
```
 
sudo rm -ri /root/.Trash/*

```

---

