---
title: "Command to start program in menu"
date: 2008-07-22
forum: General Help
---

### Post by von Stalhein on 2008-07-22
Hello all,
I've added a program to my menu items, but I can't get it to start.

It's a shell script.

I put it in the menu via the applications>edit menus but I don't understand what the command line should be.

The file name is cod.sh
If I want to run it from the CLI it goes ```
sh cod.sh
```but I'm not sure how to do that in the menu dialogue.

TIA

---

### Post by von Stalhein on 2008-07-22
I did a bit of fiddling, and what I had to do was put "sh" before the shell script location.

eg. the file was in /home/xxxx/check, so the code became
```
sh /home/xxxx/check/cod.sh
```

:redface:

---

### Post by AndyCee on 2008-07-22
In case you're interested:

if you add: ```
#!/bin/sh
``` to the top line of the script

and type: ```
chmod u+x /home/xxxx/check/cod.sh
```

you don't need the "sh" at the beginning.

---

### Post by von Stalhein on 2008-07-22
OK thanks!!
I will do that, it's neater.

---

