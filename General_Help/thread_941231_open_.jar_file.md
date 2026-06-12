---
title: "open .jar file"
date: 2008-10-07
forum: General Help
---

### Post by newbemac on 2008-10-07
I have downloaded a .jar file into user/bin.
the file will open when selected from that location.  how do I create a way to open the application from applications/ office??
thanks newbemac

---

### Post by Athanasius on 2008-10-07
If you mean opening it for editing then gedit (the GNOME text editor) is good. 

```
gksudo gedit /usr/bin/foo.jar
```

---

### Post by ju2wheels on 2008-10-08
A jar file is typically an uncompressed zip file. Open it with an archive manager if you want to see the files in it. If you just want to create a shortcut to launch the application then create a shortcut as normal and enter the following as the command:

```

java -jar /usr/bin/app.jar

```

---

### Post by jocko on 2008-10-08
> **newbemac said:**
> I have downloaded a .jar file into user/bin.
the file will open when selected from that location.  how do I create a way to open the application from applications/ office??
thanks newbemac

To add a shortcut in your menu:
Right click somewhere on the menu buttons on your panel, click "edit menus".
In the menu editor, highlight "Office" (or any other place you want to place your starter), click "New item" (or whatever the english version says).
Give the new menu item a name and add:
```
java -jar /usr/bin/*filename*.jar

```in the "command" field.

---

### Post by newbemac on 2008-10-08
thanks, worked great!

---

