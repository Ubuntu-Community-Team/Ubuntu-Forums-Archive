---
title: "command isn't working, what am i doing wrong?"
date: 2008-07-18
forum: General Help
---

### Post by sugarplumfairy on 2008-07-18
done it now

---

### Post by hal8000 on 2008-07-18
You will get a message from the terminal after typing the command, did it give you an error?

---

### Post by sugarplumfairy on 2008-07-18
It said directory does not exist
and i tried to do something similar and got incorrect command. 
I'm just trying to delete the log inside the folder, i'm trying not to delete the whole folder.

---

### Post by Potatoj316 on 2008-07-18
Ok first be careful with that sudo rm -rf command, if used incorrectaly you can wipe out your whole computer.  Second, find the log file you want to delete. (using cd to get into the directory, using ls to see your files/directories) then do a rm [log file name] you might have to do sudo rm [log filename]

The rm -rf deletes directories and their contents

---

### Post by jerome1232 on 2008-07-18
yeah I would probably always run that as ```
sudo rm -rfvI
```, that way it asks once for confirmation, review your command make sure it's right, then it will tell you what it deletes as it does so.

That way if you see some folders scroll past you don't want to delete you can hit ctrl+c and at least have a only partial mess on your hands, not a complete mess.

---

