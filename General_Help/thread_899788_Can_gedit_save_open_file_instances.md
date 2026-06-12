---
title: "Can gedit save open file instances?"
date: 2008-08-24
forum: General Help
---

### Post by Griff on 2008-08-24
Subject line says it all.  I use gedit to modify about 7 or so files for a mysql/php project.  Opening them all individually is annoying.  I know editors I've used in the past (like kate) could remember all the open files.  I can't seem to find this functionality in gedit.  Is it there?

---

### Post by Diabolis on 2008-08-24
Gedit is intended to be a lightweight text editor, so probably the closest to the feature that you want is the "Recent files" list that you have under the File menu.

You can also use the command line, write a shell script or set an alias that will open all the files that you need when you start gedit.

For example, if you execute it like this:
```
gedit file1 file2 file3 file4
```

It will open all the files in the same window. Don't forget that you need to put the full path to every file.

Probably a small shell script would be the easiest thing to do. It will look similar to this:
[PHP]#!/bin/sh
folder="path to where your files are"
gedit $folder"file name 1" $folder"file name 1" $folder"file name 3" &
done
[/PHP]

Then you can add a launcher to your gnome panel or to your menus that will execute the script.

---

### Post by Griff on 2008-08-25
Ah. Excellent idea.  I love using little shell scripts whenever I can.  I made a little one to move all my php file changes to /var/www and send backups to another machine.  Thanks for the idea.

-Griff

---

### Post by antonydck on 2008-10-14
whats that done used for

---

### Post by Gourgi on 2008-12-13
i just found a gedit plugin that kinda does what you need
```
sudo apt-get install gedit-plugins
```
and enable the 'session saver' plugin from edit->preferences->plugins

---

