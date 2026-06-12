---
title: "Applications menu empty!"
date: 2008-09-23
forum: General Help
---

### Post by fjodork on 2008-09-23
Hi


Today, when I started using my computer, I noticed that the APPLICATIONS menu is empty. When you press on it, it only shows a small grey dot. as there is nothing to show. The PLACES and the SYSTEM menu work as they should. But not the APPLICATIONS menu. Also, it seems that config file for DELUGE is gone/reset. When I run deluge now, its empty and all my settings and tweaks are reset to defaults. 

Whan could be the reason for this and how can this be fixed? 

Thanks!

---

### Post by ashmew2 on 2008-09-23
Hi , 

No ideas about Deluge..Maybe your home directory was damaged somehow ? 

Btw , Regarding Applications Menu , open a terminal and :
```

alacarte
```

Check in it if the things you want are ticked.

---

### Post by fjodork on 2008-09-23
This is what i get when trying to run alacarte. And a popup dialog that main manu closed unexpectedly.


```
fjodork ~  $  alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
fjodork ~  $  
```

As for the homedir, nothing else seems to be missing and all other programs that i frequently use are working as they should. Havent tested all off them though.

---

### Post by ashmew2 on 2008-09-23
Have you tried Right Clicking on Top Panel > Add to Panel > Main menu ? See if it has some elements ?

---

### Post by fjodork on 2008-09-23
I get the same popup when trying to click the main menu in the rightclick dropdown menu.. and same error again when trying to open the main menu in System - Preferences

---

### Post by m10 on 2008-09-25
try to go to /home/user_name/.config/menus there u should find:
 -one applications.menu
 -plenty applications.menu.undo-## (## is a number)
 -some other files
try to replace the applications.menu file with one of the applications.menu.undo-## files (i used the one with the greatest ## ).

It worked for me, i hope it does for you too.

PS the reason this happened is that your original applications.menu got corrupted or emptied

---

