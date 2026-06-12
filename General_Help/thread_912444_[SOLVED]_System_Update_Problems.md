---
title: "[SOLVED] System Update Problems"
date: 2008-09-06
forum: General Help
---

### Post by celtic426 on 2008-09-06
Hi,

Is there a file which I can edit to delete updates from the update manager?  I have two updates right now "libmpeg3hv and libquicktimehv" that when I try to install it fails and messes stuff up.  So I want to get rid of those so that the update icon is not always in the gnome panel (I know I can set those settings to never display it but rather not).

Also,  I have about 5 updates in the update manager which I cannot click on or check.  Well I can click on them but it doesn't give me the option to check them.  They are just there.  

Please help.  Thank you.

---

### Post by Shazaam on 2008-09-06
Are there any error messages you can post here?
As for Update Manager do this...
Start Synaptic, click the "Reload" icon.

---

### Post by celtic426 on 2008-09-06
OK reloading worked for most the updates.  There are 4 more which I still cannot click on.  That's not a BIG deal but if I could resolve that it would be good.  

More important though, there are three updates which I  CAN click on and install.  But when I do that things get messed up so I just wanna delete those updates.  I added some lines to a file, a file I cannot remember the name of, and those lines I added added those updates.  Now I wish to delete those lines.  What file is this  do you know?  It is the file that you add stuff to to add updates.  I hope this makes sense.  Thanks.

---

### Post by Shazaam on 2008-09-06
Sounds like you added to your sources list. Go to System>Administration>Software Sources. Look around at the different tabs (hint-Third-Party Software) and you might find what you added. Uncheck the problem entries.
Another command that you might want to try....
```
sudo dpkg --configure -a
```
As it says, configures all unconfigured packages.

---

### Post by celtic426 on 2008-09-06
Thanks for another response.  I tried what you said but didn't full work.  

A while ago there was a file which I edited to add two lines of info in to add software sources.  I typed in the terminal like gedit /blah blah.  That blah blah is what I forget.  Isn't there a file which you can edit for software sources?  It I can find that file I can just delete the last two lines and be all set.

---

### Post by Shazaam on 2008-09-06
Yes there is.
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by celtic426 on 2008-09-06
thanks that worked.  thanks again.

---

