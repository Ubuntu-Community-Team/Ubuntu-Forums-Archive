---
title: "Putting python script to main menu bar"
date: 2008-11-29
forum: General Help
---

### Post by kartal on 2008-11-29
Hi

I am having a little issue with putting one python script to menu bar for quick access. When I drag and drop the script, I cannot run it from the menubar. It relies on some other scripts and libraries in its own folder. I have tried hardlinks, links, python xxx.py link etc. None is working for me. Is this possible? 

I can run the script inside the original folder but looks like outside invoking call is not possible.

thanks

---

### Post by Submicro on 2012-04-24
I'm resurecting this thread because I'm having the same problem, any ideas?

---

### Post by stinkeye on 2012-04-24
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1959485") for adding scripts to the unity launcher.

---

### Post by Jay Christnach on 2012-04-24
I haven't tried it. But I suggest you use the Main Menu Editor and add an application launcher. As the command to run you would choose:

cd /your/script/directory ; /usr/bin/python yourscript.py

kind greetings

---

