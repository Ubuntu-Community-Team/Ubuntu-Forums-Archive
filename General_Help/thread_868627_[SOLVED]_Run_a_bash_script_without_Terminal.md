---
title: "[SOLVED] Run a bash script without Terminal"
date: 2008-07-24
forum: General Help
---

### Post by borobudur on 2008-07-24
Hi, 
I have this mini shell script which I call from the panel via a button (launcher):
```
#!/bin/bash
realplay http://dms-cl-013.skypro-media.net:8080/ramgen/encoder/drs1.rm
```

In the launcher I need to chose the type* Application in Terminal*. Like this a terminal opens too aside of the realplayer. With typ *Application* nothing happens. 

Does anyone know how to run the script without the need of opening an terminal?

---

### Post by tomcheng76 on 2008-07-24
assume the name of the script is ramgen
put the script into /usr/local/bin
chmod 755 /usr/local/bin/ramgen

then alt+f2 => type ramgen

---

### Post by angry_johnnie on 2008-07-24
```
#!/bin/bash
realplay -n http://dms-cl-013.skypro-media.net:8080/ramgen/encoder/drs1.rm
```

you missed the -n flag (new window). :-)

---

### Post by borobudur on 2008-07-24
Thanks for your advises but this isn't what I'm looking for.

tomcheng76: I just want to press the button, don't want to type anything.

angry_johnnie: with the new flag I still have the open terminal which I need to make an extra click later, and having an extra window open...

---

### Post by justleen on 2008-07-24
you can easily create a shortcut to the command.. doenst matter if you type it in the ctrl-f2 window, or enter the command in a new shortcut

edit: right click on the menu bar > add to panel > custom app launcher

or

right click the ubuntu logo > edit menus > go the the menu you want,  and choose new item

---

### Post by borobudur on 2008-07-24
Got it! Made a link in the bin directory to my script. Perfect!!

---

### Post by PhosPhoton on 2011-05-21
I have a script that is run from a .desktop file, but the script seems to require a terminal window. How do I make a script run without it needing a terminal window? If I set Terminal=false then the script does not even run. The script is in /usr/local/bin

Please advise, the terminal window popping up is just plain annoying.

---

