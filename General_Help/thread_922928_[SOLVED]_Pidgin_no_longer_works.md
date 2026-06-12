---
title: "[SOLVED] Pidgin no longer works"
date: 2008-09-17
forum: General Help
---

### Post by VTshredder on 2008-09-17
Not sure what to do here, but since yesterday i have been unable to use Pidgin.  After i start Pidgin, my buddy list shows up, shows me who is online, then just freezes and does the gray shade. It will continue to fade in and out until i force quite.  I will even get an IM during the process but i cant use or click on anything.
From the Terminal i get this:
eightvirtues@eightvirtues-desktop:~$ pidgin
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
Killed

---

### Post by y-lee on 2008-09-17
Try renaming the hidden folder .purple  to .purple.bak then see if this helps. This should make pidgin rebuild the folder.

---

### Post by VTshredder on 2008-09-17
Forgive me if i dont completelty understand, but all i could find was a .puprle-2 folder in the lib file.  Does that make any sense? 
Other than that, i am unable to locate .purple

---

### Post by y-lee on 2008-09-17
> all i could find was a .puprle-2 folder in the lib file. Does that make any sense?
Other than that, i am unable to locate .purple

if you mean .purple-2 and it is in your home directory and the folder looks like it contains pidgin stuff try rename it. be sure pidgin is closed when you do, tho. restarting pidgin should recreate a .purple or .purple-2 folder. I am not sure why it would be called .purple-2 on your machine :confused: but stranger things have happened. lol

---

### Post by VTshredder on 2008-09-17
I guess that explains my confusion as well.  purple.2 is located under File System>usr>lib.
It sure looks like it contains pidgin files, tons of .so files named ignore, auto accept, buddy note, etc etc.  
So i should rename that file purple.bak...

---

### Post by y-lee on 2008-09-17
> purple.2 is located under File System>usr>lib.

NO!

That is a system folder.

You don't have a .purple folder in your home folder? 
open a terminal and try

```
 ls -d .purple
```

That should list .purple

---

### Post by perlluver on 2008-09-17
You may have to press ctrl+h when nautilus is open to home.  That will show hidden folders, and look for .purple.

---

### Post by VTshredder on 2008-09-17
That is why i asked...did not think messing with a Sys file was the way to go.

I cannot find any file in my home directory named ".purple".  
In the terminal i get this:

eightvirtues@eightvirtues-desktop:~$ ls -d .purple
.purple

---

### Post by y-lee on 2008-09-17
> You may have to press ctrl+h when nautilus is open to home. That will show hidden folders, and look for .purple.

Indeed .purple is a hidden folder hit ctrl h to view hidden folders in nautilus or go to view in nautiluses menu and click show hidden files.

> n the terminal i get this:

eightvirtues@eightvirtues-desktop:~$ ls -d .purple
.purple 

This shows you do have the folder :)

---

### Post by VTshredder on 2008-09-17
Nice... was not aware of the ctrl-H.  Renamed the folder and Pidgin works like new.  Thanks to both of you for hookin it up!!

---

