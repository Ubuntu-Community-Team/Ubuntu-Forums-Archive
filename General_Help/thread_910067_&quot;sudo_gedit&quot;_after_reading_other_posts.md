---
title: "&quot;sudo gedit&quot; after reading other posts"
date: 2008-09-04
forum: General Help
---

### Post by nieve on 2008-09-04
Whenever hay try sudo gedit, like for instance with /etc/network/interfaces it goes very very slowly and when it shows up I can not write inside and it only shows a blank page
I have read other posts and I have tried gksu and gksudo, but does not work anyway, it just show the file page al white
what can I do? thank you a lot

---

### Post by Elfy on 2008-09-04
Sound like you are not getting the paths right and it's opening a new file. But if that's not the case will the files open with other editors.

Have you used nano - ctrl+X to exit

Try ```
nano /etc/network/interfaces
```

You could try to purge and reinstall gedit, but it might be worth moving the gedit file in home first

---

### Post by thestig_992 on 2008-09-04
try "sudo gedit" then open file> then navigate to the actual file

---

### Post by aloshbennett on 2008-09-04
I've heard this complaint before. You might be better of using nano or emacs instead of gedit with sudo

---

### Post by drs305 on 2008-09-04
The OP correctly mentions using "gksu" or "gksudo", but for others please use "gksu" or "gksudo" with graphical apps such as gedit. Reserve "sudo" for command line operations (which also don't open a gui-based app). While some gui programs will appear to run correctly with "sudo", others will actually hang if you don't use the proper form.

This command should work without problems:
```

gksu gedit /etc/network/interfaces

```

---

### Post by nieve on 2008-09-04
I have tried all tha options, the worse thing is tha after a long time the file opens, but then all hangs and I can not do anything

---

### Post by nieve on 2008-09-04
could someone tell me how to purge gedit and reinstall step by step?

---

### Post by drs305 on 2008-09-04
> **nieve said:**
> could someone tell me how to purge gedit and reinstall step by step?

```
sudo apt-get purge gedit
sudo apt-get update
sudo apt-get install gedit
```

---

### Post by Elfy on 2008-09-04
I'd be inclined to remove, or at least rename, the .gnome2/gedit folder as well before reinstalling it.

---

### Post by nieve on 2008-09-04
thanks a lot, and could you write me also the steps to do dat, or to move home o whatever?

---

### Post by Elfy on 2008-09-04
```
mv ~/.gnome2/gedit ~/gedit
``` will move it to a folder gedit in your home

then follow drs305

---

### Post by nieve on 2008-09-04
shal I get from synaptics also gedit-dev?
and, if I purge gedit, could it have any consequences in the changes I have done in other files?

---

### Post by nieve on 2008-09-04
it says to me:
 no se puede efectuar `stat' sobre «/home/carlos/.gnome2/gedit»: No existe el fichero ó directorio
in englihs more or less: it cant be done stat on «/home/carlos/.gnome2/gedit»: does not exist the file or directory

---

### Post by Elfy on 2008-09-04
Well if it's not there then you don't need to move it.

Check with ```
ls ~/.gnome2
```

No you won't need gedit-dev and purging won't have any effect on files you've edited.

---

### Post by nieve on 2008-09-04
accels           epiphany            Greenwich                panel2.d
accelsgedit      evince              keyrings                 seahorse
backgrounds.xml  file-roller         main                     share
Brasero          f-spot              monitors.xml             yelp
brasero.session  gedit-2             nautilus-scripts
eog              gedit-metadata.xml  network-admin-locations


that is what I got, thankl you very much for being there

---

### Post by Elfy on 2008-09-04
Well it's not there - so just do drs305 commands to purge and reinstall it.

---

### Post by nieve on 2008-09-04
I have done it but I am afraid nothing happens, I mean, now I have tried gksu gedit /etc/privoxy/config/
and I am still waiting for the file

---

### Post by nieve on 2008-09-04
it is all the same, now the file is white, and I can not write in it
if I do nano, then I get the file, but I do not now who to work with nano, I can not read the file

---

### Post by Elfy on 2008-09-04
can you open these files with any editor, try nano /etc/privoxy/config/

Maybe install mousepad and see if that works ok.

```
sudo apt-get install mousepad
```

---

### Post by Elfy on 2008-09-04
Nano - Ctrl+O, enter to save

Ctrl+X to exit - if file not saved it will ask - Y or N then give file name to save

---

### Post by nieve on 2008-09-04
I could try to make it with mousepad but I would like to now why gedit does not work
I have purged privoxy and when I install it again I get this error: E: Sub-process /usr/bin/dpkg returned an error code (1)
could it be the cause?
shall I creat a new thread or I may continue here?

---

