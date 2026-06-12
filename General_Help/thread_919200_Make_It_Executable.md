---
title: "Make It Executable"
date: 2008-09-13
forum: General Help
---

### Post by raywood on 2008-09-13
I have a text file that begins as follows:
> 
#! /home/ray/Desktop/SLSites

firefox-2 [http://www.google.com](http://www.google.com)
firefox-2 [http://www.yahoo.com](http://www.yahoo.com)

When I double-click on this file on the Desktop, I get an option of running or displaying.  I think that means chown +x made it executable.

When I choose Run, nothing happens.

What am I missing?

---

### Post by mb_webguy on 2008-09-13
> **raywood said:**
> I have a text file that begins as follows:


When I double-click on this file on the Desktop, I get an option of running or displaying.  I think that means chown +x made it executable.

When I choose Run, nothing happens.

What am I missing?

Well, that first line should point to a shell or interpreter, not the location of the file.  Change it to:```
#! /bin/bash
```

---

### Post by raywood on 2008-09-13
You learn something new every day.

Now, for tomorrow:  when I double-click on the file or type ./SLSites (i.e., the name of the file), nothing happens.  This is after running chmod +x (filename).  Am I missing something else?

---

### Post by cmay on 2008-09-13
[PHP]#! /bin/bash

firefox-2 http://www.google.com
firefox-2 http://www.yahoo.com[/PHP]

i dont know if it is this you are trying to do
but if its a bash shell script to open some pages then i would have done this way.chmod 755 ./the_file to ,make it a executable. then run ./the_file
edit:
this do not work however. i did not test it.before posting. never mind this.

---

### Post by mb_webguy on 2008-09-13
I created the following file on the Desktop and changed the permissions using "chmod +x ff".```
#! /bin/bash
firefox http://www.google.com

```

(I'm not using Firefox 2, which is why I just have "firefox" in the commands.)  When I double-clicked the file on the desktop, it prompted me to run it or open it.  When I ran it, it worked just fine.

HOWEVER, if you just want an icon on the desktop to open a certain website or websites in Firefox, then you need a launcher, not a script.  Right-click on the desktop and select "Create Launcher".  In the Command box, enter the commands from your script separated by a semi-colon.  Give it a name and select an icon if you want, then click OK.

---

