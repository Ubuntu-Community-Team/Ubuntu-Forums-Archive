---
title: "Associate file type with application by default"
date: 2008-10-09
forum: General Help
---

### Post by Phil Airtime on 2008-10-09
For some reason, all MS Word documents are trying to open in GIMP when I double-click them from Nautilus. To open in OpenOffice, I have to right-click and use Open With..., which I invariably forget to do. How do I change it back to OpenOffice by default?

---

### Post by _sAm_ on 2008-10-09
Right click on the *.doc file > Properties > "Open With" tab > and choose OpenOffice.

---

### Post by noob5000 on 2010-10-26
how about associating text files with gedit? (ubuntu 9.04)

when i rightmouseclick on a textfile and go to > Properties > "Open With" tab >
gedit is already chosen, but when i double-click on a text file i get a warning message:

```
Do you want to run "example.txt", or display its content? 
example.txt is an executable file
```
... together with 4 option buttons: "Run in Terminal", "Display", "Cancel" and "Run"

i assume there is a simple way of changing this and associating text files with gedit via terminal, but i don't know the command...

---

### Post by gustav.franzsen on 2011-03-15
Your problem has nothing to do with associations.

1. Right-click on file.
2. Choose Properties
3. Click on Permissions tab
4. You will notice an option lower down 'Allow executing file as programme'
5. De-select it
6. Click Close


Try opening the file again ... :)

---

