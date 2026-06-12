---
title: "Can't empty my trash is staying full, more small problem"
date: 2008-10-01
forum: General Help
---

### Post by Turge on 2008-10-01
Hello.
I'm trying to empty my trash and i get this error "Error removing file: Permission denied".
Because from a long time i delete my desktop in a mistake.
I didn't mount any media so it can't be that my usb be pulled out.

What should I do?

And I have 1 more small problem, I want to change my quit icon ( the icon that you turn off the computer).
So I tried to right click and then properties but the properties option is not there like in any folder.
So I tried to look at usr/share folder and to change there the icon but I didn't find him.

How can I change him?

Thank you.

---

### Post by kokkus on 2008-10-01
To empty the trash you can go to terminal, type the code
```
gksudo Nautilus
```
to get root promission.
Now, the trash is under root/.local/share/trash.
Delete the trash folder and create a new one.

To change your guit icon, go to usr/share/icons, use CTRL+F to search files under that folder, write quit to get all the quit icons up, now replace them with your own. (png format)
Use gksudo nautilus for thisone too to get promission to replace the files.

Good luck:)

---

### Post by drs305 on 2008-10-01
In the previous entry, it was probably meant to be:
```
gksudo nautilus
```

The following link will take you to a tutorial on finding and deleting trash on your system. In your case, the trash is probably owned by root and thus you can't delete it as a normal user.[Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

Opening nautilus with 'gksudo' will allow you to delete trash from the trash bins. Normal locations in hardy are:
~/.local/share/Trash/files
/root/.local/share/Trash/files

---

### Post by Turge on 2008-10-01
Thank you all guys now the trash is empty.

About the icon i make a search there but I didn't find the quit icon.

Maybe someone knows?

---

### Post by drs305 on 2008-10-01
In the Hardy Human theme, the logout icon (red circle) is:
/usr/share/icons/Human/24x24/apps/gnome-logout.png

Here is how I would change it.
Backup the current icon:
```

sudo cp /usr/share/icons/Human/24x24/apps/gnome-logout.png /usr/share/icons/Human/24x24/apps/gnome-logout.original.png

```

Edit the icon you want to use to 24x24 pixels (this isn't absolutely necessary but may allow better presentation on your screen).

Replace the current icon with your new one. Change the first path/name to the one you would like to use:
```

sudo cp */your.path/your.icon.png* /usr/share/icons/Human/24x24/apps/gnome-logout.png

```

Refresh the icon panel:
```

sudo /etc/init.d/dbus restart

```
Note: I tested the above. The first time I selected the icon it took about 50 seconds for the quit menu to appear. Subsequent selections took the normal amount of time. I don't know if this was related to the icon change but I wanted to mention it...

Don't forget to mark this thread solved if you have no more questions.

---

### Post by Turge on 2008-10-02
> **drs305 said:**
> In the Hardy Human theme, the logout icon (red circle) is:
/usr/share/icons/Human/24x24/apps/gnome-logout.png

Here is how I would change it.
Backup the current icon:
```

sudo cp /usr/share/icons/Human/24x24/apps/gnome-logout.png /usr/share/icons/Human/24x24/apps/gnome-logout.original.png

```

Edit the icon you want to use to 24x24 pixels (this isn't absolutely necessary but may allow better presentation on your screen).

Replace the current icon with your new one. Change the first path/name to the one you would like to use:
```

sudo cp */your.path/your.icon.png* /usr/share/icons/Human/24x24/apps/gnome-logout.png

```

Refresh the icon panel:
```

sudo /etc/init.d/dbus restart

```
Note: I tested the above. The first time I selected the icon it took about 50 seconds for the quit menu to appear. Subsequent selections took the normal amount of time. I don't know if this was related to the icon change but I wanted to mention it...

Don't forget to mark this thread solved if you have no more questions.
It's says Error moving file: Permission denied.
When I try to replace it.

---

### Post by drs305 on 2008-10-02
> **Turge said:**
> It's says Error moving file: Permission denied.
When I try to replace it.

Did you use the "sudo" command when you tried to move your icon into the icon folder? You are placing the new icon (file) into a system folder so you cannot do this as a normal user. 

Try renaming gnome-logout.png before attempting to copy the new icon into the folder. The command follows. ( I modified the backup filename just to make sure this replacement command would not conflict with the previous one). The original icon will be named *gnome-logout.png.bak*:
```

sudo mv /usr/share/icons/Human/24x24/apps/gnome-logout.png /usr/share/icons/Human/24x24/apps/gnome-logout.png.bak

```
Then try copying your icon to the system folder. Make sure you change the path and filename to match where your new icon is located:
```
sudo cp **/your.path/your.icon.png** /usr/share/icons/Human/24x24/apps/gnome-logout.png
```


If command line doesn't work for you, you might try opening nautilus with 'gksudo' to gain adminstrative rights to change files. Then copy/paste or drag you icon to the correct location:
```
gksudo nautilus
```

---

### Post by Turge on 2008-10-02
> **drs305 said:**
> Did you use the "sudo" command when you tried to move your icon into the icon folder? You are placing the new icon (file) into a system folder so you cannot do this as a normal user. 

Try renaming gnome-logout.png before attempting to copy the new icon into the folder. The command follows. ( I modified the backup filename just to make sure this replacement command would not conflict with the previous one). The original icon will be named *gnome-logout.png.bak*:
```

sudo mv /usr/share/icons/Human/24x24/apps/gnome-logout.png /usr/share/icons/Human/24x24/apps/gnome-logout.png.bak

```
You might try opening nautilus with 'gksudo' to gain adminstrative rights to change files. Then copy/paste or drag you icon to the correct location:
```
gksudo nautilus
```

Thank you it's work.

---

