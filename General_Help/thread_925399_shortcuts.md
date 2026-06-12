---
title: "shortcuts?"
date: 2008-09-20
forum: General Help
---

### Post by Monotoko on 2008-09-20
I was wondering if it was possible to put a shortcut to /var/www on my desktop, so i dont have to go through all the stuff to find it every time, i right clicked, and expected to find a "create shortcut" button (native windows user here) but didnt, so how exactly do you make shortcuts in linux?

---

### Post by Liolikas on 2008-09-20
read: [http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by Monotoko on 2008-09-20
sudo ln -s /home/monotoko/Desktop/www /var/www

why is that not working? (it gives no output, but i see no shortcut on my desktop)

---

### Post by issih on 2008-09-20
I'm not in my ubuntu install right now so I'm not 100% sure about this, but I think you can right click on any file in nautilus (the file browser) and make a shortcut from the drop down menu.

That shortcut will be created in the same directory as the original file, but you can then move it wherever you want by the usual methods...e.g. just drag and drop it on the desktop.

As for why your terminal commands failed, I think you have your source file and target file mixed up.... put the file you want to link to first and the file where you want the link to be second

Hope that helps

---

### Post by DrMelon on 2008-09-20
Make sure that the directory exists on your desktop, first of all. So make a new folder called "www" on your Desktop, and then use the command.

---

### Post by Monotoko on 2008-09-20
> **issih said:**
> I'm not in my ubuntu install right now so I'm not 100% sure about this, but I think you can right click on any file in nautilus (the file browser) and make a shortcut from the drop down menu.

That shortcut will be created in the same directory as the original file, but you can then move it wherever you want by the usual methods...e.g. just drag and drop it on the desktop.

As for why your terminal commands failed, I think you have your source file and target file mixed up.... put the file you want to link to first and the file where you want the link to be second

Hope that helps

Yepp, i got them the wrong way :P
and i cant see somewhere to make a shortcut....

Ahh, i see, the files i was trying to link to were owned by root, thats why

---

### Post by issih on 2008-09-20
Ah good, in that case you need to use
```
sudo ln -s ........
```

To do it from the file browser you just right click and select 'make link'. To be able to do that on a location with root privileges you would have to launch the file browser with:

```
gksudo nautilus
```

and be sure to close it as soon as possible to avoid doing something nasty by accident.

Hope that helps

---

### Post by Monotoko on 2008-09-20
ahhhh thank you, i was wondering if there was a way to do that

---

### Post by mb_webguy on 2008-09-20
Also, shortcut icons are called launchers in Gnome.  When you right-click on the desktop, the equivalent to "Create Shortcut" is "Create Launcher".  You can create a simple link to a folder by creating a launcher for Nautilus (the file manager) and putting the path to the folder you want to open after the command to launch Nautilus, for example "nautilus /var/www".  You may want to change the icon, though, since the default is the Nautilus shell icon.

---

