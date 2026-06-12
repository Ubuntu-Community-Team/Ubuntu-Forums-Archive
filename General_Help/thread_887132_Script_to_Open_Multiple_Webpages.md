---
title: "Script to Open Multiple Webpages?"
date: 2008-08-11
forum: General Help
---

### Post by raywood on 2008-08-11
In Hardy 8.04 64-bit,

(1) What would be the Ubuntu equivalent of this WinXP DOS batch command:

start firefox.exe "http://freerice.com/index.php"

(2) What would I need to add, to that command, in order to have a script with clickable icon capable of opening new tabs in Firefox for that and other specified webpages?

Cheers!

---

### Post by unutbu on 2008-08-11
For concreteness let's call the script firebatch:
```

#!/bin/sh
firefox http://freerice.com/index.php &
sleep 1
firefox http://google.com 
firefox http://yahoo.com 
```

Make it executable:
```

chmod 755 firebatch
```

To make a launcher:
 
Right-click on the background -- anywhere there is no window. Select "Create Launcher...".
A dialog box will pop up asking for a Name, Command, and Comment.
Name and Comment can be anything you like.
Command should be the full path to the firebatch script.

---

### Post by raywood on 2008-08-25
That worked.  Thanks.

In case anyone else is interested in command lines to open different kinds of files and folders, try this:

    > firefox-2 [http://www.thehungersite.com](http://www.thehungersite.com)
    gnome-open "/media/DATA/Name of Folder to Open"
    gnome-open "/Path/File Name.ext"


---

