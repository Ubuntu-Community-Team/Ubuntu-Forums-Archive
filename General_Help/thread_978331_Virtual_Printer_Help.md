---
title: "Virtual Printer Help"
date: 2008-11-11
forum: General Help
---

### Post by Sollertian on 2008-11-11
In case it's relevant - I'm using Ubuntu 8.10 and CUPS 1.3.9

This problem has been driving me crazy so hopefully somebody can help.  A few days ago I decided that I needed to figure out how to print multiple pages per sheets in Ubuntu. I came across the program GtkPSproc and have been attempting to install it.

For some reason, there's something wrong when the backend I need to use for the virtual printer is copied to the /usr/lib/cups/backend folder.  When trying to add the printer using that backend, an error occurs.  Morever, when I try running the lpadmin command manually (it is normally run through a makefile), psproc_backend does not autocomplete when I have partially typed it and press tab (all the other backends do autocomplete).  The permissions on the backend is 755, same as the others. I am at a lost at what to do.  

Here's the error when I run it through the make file:
[B]lpadmin -p GtkPSproc -E -v psproc_backend:/
lpadmin: Bad device-uri "psproc_backend:/"![/B]

I've attached psproc_backend.py.  Any help is much appreciated. Thanks!

---

### Post by Sollertian on 2008-11-11
Just to add, I ran "lpinfo -v" in terminal and "psproc_backend:/" was listed.

---

### Post by moritzbonn on 2008-11-30
Hi,

I had the same problem while installing gtkpsproc. The solution for me just was to rename the file (to for example psproc). You can also do this in the Makefile and reinstall everything.

Do not ask why this helps or why the name psproc_backend does not work. :)

---

