---
title: "Laptop shuts down when loading after adding p4_clockmod to etc/modules"
date: 2008-10-01
forum: Hardware
---

### Post by inordinate on 2008-10-01
Is there some way i could remove the line from the recovery terminal?

I try gedit but i'm sure its because it can't open up a window in the terminal :( 

so how can i remove this line?

---

### Post by ajgreeny on 2008-10-01
Check that there isn't already a backup of the file in /etc by using ```
cd /etc && ls -a
``` and looking for modules~ in the list that appears.  If it is there restore it, having checked it is the right file first with ```
cat /etc/modules~
```, with the command ```
mv /etc/modules~ etc/modules
```In recovery mode, ie terminal mode, if you need to, you can use ```
nano /etc/modules
``` and edit out the line easily.  After doing this, save the edited file by using Ctrl+X to save the new version.  Just make sure you backup first in case it all goes wrong.

---

### Post by inordinate on 2008-10-01
thank you so much, you saved me from having to reinstall all the wireless drivers and everything

---

