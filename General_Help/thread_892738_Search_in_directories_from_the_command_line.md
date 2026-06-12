---
title: "Search in directories from the command line"
date: 2008-08-17
forum: General Help
---

### Post by colobix on 2008-08-17
Is it possible to search from the command line insted of now when I have to go to Places to search for files? 
That would go so much faster.
Or is it possible to add "search" to the right click menu like in windows?

Thanks :)

---

### Post by Naatan on 2008-08-17
search in the right click menu? I've never had that but I reckon it's fairly easy to do with Nautilus scripts.

The easiest way to find files from the terminal is with the following command

$ find . | grep 'filename'

This would look in the current folder and all subfolders you are in.

---

### Post by colobix on 2008-08-17
Thanks but I didnt mean in the terminal. I ment the address line in the file browser below the icons for back, stop. update, home etc,
Or if its possible to add search in the right click menu.

---

### Post by Naatan on 2008-08-17
Simply press CTRL+F in Nautilus? :)

Or add the "Search for Files" applet to the gnome panel

---

### Post by colobix on 2008-08-17
thanks, but how do I add the "Search for Files" applet to the gnome panel

---

### Post by Naatan on 2008-08-17
Right click the Gnome Panel, click Add to Panel, select "Search for Files.." and click "Add"

---

### Post by colobix on 2008-08-17
OH that panel, I though u ment the right click menu, but ok.
Thank you so much for you help ;)

---

### Post by Naatan on 2008-08-17
I didnt find any existing Nautilus scripts to search for files but it should be quite easy to create yourself, just find an existing Nautilus script and modify it to launch a file and folder searching app when you click the menu link.

I don't really see the point though.. ctrl+f is much easier and you can use the panel applets for anything more advanced.. I guess that's why no one has taken the time to create a nautilus script :p

---

