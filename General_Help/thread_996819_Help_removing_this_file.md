---
title: "Help removing this file"
date: 2008-11-29
forum: General Help
---

### Post by b3n0 on 2008-11-29
Hey guys,
I've got a stubborn one! Its a directory on my desktop with a padlock icon on it. This is what Ive tried.
Shift + Delete lol no go there
and this
```
concorde@BenjaminsLappy:~/Desktop$ sudo rmdir thefile
rmdir: failed to remove `thefile': Directory not empty
concorde@BenjaminsLappy:~/Desktop$ 
```

Any ideas?

Thanks for your help.

---

### Post by IHATEDLINK on 2008-11-29
> **b3n0 said:**
> Hey guys,
I've got a stubborn one! Its a directory on my desktop with a padlock icon on it. This is what Ive tried.
Shift + Delete lol no go there
and this
```
concorde@BenjaminsLappy:~/Desktop$ sudo rmdir thefile
rmdir: failed to remove `thefile': Directory not empty
concorde@BenjaminsLappy:~/Desktop$ 
```

Any ideas?

Thanks for your help.

Try typing on terminal:

```
 gksudo nautilus 
```

Enter your admin password and navigate to your desktop. Then just delete your file.

Enjoy!

---

### Post by Libux on 2008-11-29
try to become a root and then delete it
(sorry for bad english)

---

### Post by davidbilla on 2008-11-29
'rmdir' will only remove a directory if it is empty.
If you want to do it in the command line you can use

$ sudo rm -r dir-name

The '-r' option is for 'recursive' i.e., to delete the files&dirs inside dirs and those within them... ad infinitum! (Well, not exactly!)

---

### Post by b3n0 on 2008-11-29
> **IHATEDLINK said:**
> Try typing on terminal:

```
 gksudo nautilus 
```

Enter your admin password and navigate to your desktop. Then just delete your file.

Enjoy!
I tried this but for some reason the file was not visible when i navigated to thee desktop. 
> **davidbilla said:**
> 'rmdir' will only remove a directory if it is empty.
If you want to do it in the command line you can use

$ sudo rm -r dir-name

The '-r' option is for 'recursive' i.e., to delete the files&dirs inside dirs and those within them... ad infinitum! (Well, not exactly!)

Worked perfectly! Thanks

---

### Post by albandy on 2008-11-29
Edited: sorry I don't saw the solved tag

sudo chmod 777 thefile -R
sudo rm -rf thefile

---

### Post by lukjad on 2008-11-29
> **b3n0 said:**
> I tried this but for some reason the file was not visible when i navigated to thee desktop.
That's because you when to the wrong desktop. I had this trouble as well. When you type:
```
gksudo nautilus
```
You will notice that it says Root on the top left.

This means that the folder "Desktop" you are looking at is the one that you would see if you logged in in recovery mode. In fact, the "Trash" link you see on the far left is also the Root trash. 

To navigate to your regular desktop click the "Up" button located near the top of the window once. You can also click the File System link on the Places menu that is located on the left of the screen. 

From here, you should see a file called Home. Double click on it.

Usually, you will see two folders, one called *lost + found* and one with your username. If you have multiple users, you will see all the usernames as well. Double click yours and you will be put into your home folder. From there, you should see a folder called *Desktop*. Double click it and then right click the file and choose *Move to Trash*. 

Once you have Moved it too trash, you need to delete it from the Root Trash. On the Places menu to the right, click the link to the Trash. When you are in the Root Trash, delete the file. Just so you know, in Hardy, this last step doesn't seem to be needed, or possible, at least for me.

Just be careful not to fiddle with any other files while you are there since you could mess up permissions.

---

### Post by b3n0 on 2008-11-29
Thanks for that. I'll keep it in mind for next time. As a noob I still prefer the gui way of doing things. I'm still taking baby steps in the terminal. So that will help greatly. At least the folder has been deleted now. 
Thanks eveyone for your help.
:D

---

### Post by lukjad on 2008-11-30
There's nothing wrong with the GUI way, it just takes so much text to explain it. ;)

Anyway, glad to be of sevice. Hope to see you around.

---

### Post by binbash on 2008-11-30
rm -rf foldername

---

