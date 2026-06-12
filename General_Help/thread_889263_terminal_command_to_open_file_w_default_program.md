---
title: "terminal command to open file w/ default program?"
date: 2008-08-13
forum: General Help
---

### Post by dracule on 2008-08-13
Is there a command to open a file w/ the default program?

I ask because in python on windows there is os.startfile()
on linux there isnt one. 

It is simply impossible to get the default program for all the files which my program will open, especially if it goes multi distribution

so basically I can call a terminal command w/ os.system()

so is there a command that can open it with the default program associated with the file extension?

like open the default webbrowser if it is .html (i just cant simply use firefox since not all linux distros have firefox installed by default)
or if the extension is .pdf open the default pdf viewer
or if the extension is .doc open the appropriate viewer/editor.

---

### Post by unutbu on 2008-08-13
/usr/bin/xdg-open 
seems to almost fit the bill. (On my system it works with html, pdf, odg, jpg. It did not work with png, though I expect I just need to configure png somewhere.)

---

### Post by tech0007 on 2008-08-13
right click on the file, then properties, the click launcher..select the program of your choice, then click ok.

---

### Post by sdennie on 2008-08-13
On a gnome machine, you can try:

```

gnome-open some_file

```

That should be the equivalent of double clicking something in nautilus.

---

