---
title: "IDLE Python ImportError: No module named TestCommands"
date: 2008-07-14
forum: General Help
---

### Post by Mini Tux on 2008-07-14
[FONT="Franklin Gothic Medium"][SIZE="2"][COLOR="Indigo"]Okay. So I am a totally new user of IDLE and Python so I expect to have some issues. What I didn't expect was to have issues using exactly what I was told in the tutorial.

It said to create a new file (module) and name it *TestCommands.py* Within it there is a line that reads *msg = 'whatever I want to put'* then it said save it. So I did. Then it said to type in the command line of IDLE  from TestCommands import msg. And it came up saying  ImportError: No module named TestCommands

What do i have to do to fix this? I can't even find the answer in the book on Python. I'm ready to give up! :confused:

Thanks in advance...[/COLOR][/SIZE][/FONT]

---

### Post by todlangweilig on 2008-07-15
The problem is Python can't see your file. This is because the path to your file isn't not on Python's import path list. Python seems to be a bit of a pain when it comes to imports, but don't despair, it is possible to get python to see your file. 

Open IDLE and click the File menu and click on Path Browser, these are the places Python will look when importing. Almost certainly your file won't show up there. There are several ways to get Python to see your file, but I can't help there. Perhaps a more experience person can help you out with that. 

But in the mean time as a temporary fix, try moving your file to the your home directory, so the path will be /home/yourUsernameHere/TestCommands.py , Python should be able to find your file then.

---

### Post by Mini Tux on 2008-07-15
Thank you so much for your help. Even though it is a temporary fix, it totally worked. I gave you a "Thanks" to show my appreciation for your effort.

Thanks again.

Now I just need to find out how to add the Documents foler to that path thingie. That will make it a permenant fix. 

Anyone else have any ideas?

---

### Post by todlangweilig on 2008-07-16
Don't lose hope yet, I have some ideas. I'll make another post here when I can figure some things out.

---

### Post by Mini Tux on 2008-07-16
Ok. Thank you. Yet again. I really appreciate your help! :D

---

### Post by polpak on 2008-07-18
Importing modules in python is done by looking at a specific set of directories for module files. 

These directories can be seen in the sys.path variable:

```

#!/usr/bin/env python

import sys
for path in sys.path:
   print path

```

To modify what paths python uses to lookup modules you can either append/insert new paths to this variable

e.g:
```

sys.path.append('/opt/python-libs')

```

Or you can specify what additional paths python uses initially by setting an environment variable

$ export PYTHONPATH=/opt/python-libs

Hope that helps..

---

### Post by todlangweilig on 2008-07-18
I'm not trying to over whelm you with links and resources, but if you need some help, these might be useful. Just take your time and go through them when you need help. 

**Relating to ImportError**
You might also check out this page if you are looking for more information on importing errors. 
[http://docs.python.org/tut/node8.html](http://docs.python.org/tut/node8.html) look at > "The module search path" 

**Python Community**
If you need more help with Python, there are several places you can go. 
[http://mail.python.org/mailman/listinfo](http://mail.python.org/mailman/listinfo) 
Either 'Python-help' or 'tutor' are good places to go for help. 'comp.lang.python' is also another place that you can get help from. 

If you would like more immediate help, there is the #python channel on IRC
[http://www.python.org/community/irc/](http://www.python.org/community/irc/)

**Documentation**
You might also check out the documentation page here. There is a lot of info that might be what you need. 
[http://www.python.org/doc/](http://www.python.org/doc/)

Python beginners guides for those with no programming background, and with those with a background. I would check out both for completeness
[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers)
[http://wiki.python.org/moin/BeginnersGuide/Programmers](http://wiki.python.org/moin/BeginnersGuide/Programmers)

A large python FAQ that may be of use.
[http://effbot.org/pyfaq/](http://effbot.org/pyfaq/)

A website that has screen captured videos showing how to do various things in Python
[http://showmedo.com/videos/python](http://showmedo.com/videos/python)

---

### Post by Mini Tux on 2008-07-21
Thank you guys so much for your help. I send you both "Thanks" to show my appreciation for your help. I haven't tried them out yet but I certainly will as soon as I get the chance.

Thank you once again! :D

---

