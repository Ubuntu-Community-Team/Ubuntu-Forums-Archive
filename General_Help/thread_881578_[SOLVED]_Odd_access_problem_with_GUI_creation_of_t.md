---
title: "[SOLVED] Odd access problem with GUI creation of text docs"
date: 2008-08-06
forum: General Help
---

### Post by soumo on 2008-08-06
Hi all,

I am having a bit of a situation creating new text docs by right clicking "create document --> new text file" in Hardy Heron.  this occurs if I use the GUI to create the "new text file" only, the "empty file" option works fine.  It doesn't matter if it's the desktop or some other folder.

If I use this method, the permissions for me (Owner) are read and execute, but not write.  The file icon will appear with a lock on it.  As well, the modified date always appears as "Mon 26 Nov 2007 03:45:51 AM EST", no matter when I create the doc.  The accessed date/time is correct.   

If I create the document in a terminal using "echo xyz > doc.txt" then there are no problems.  Similarly if i use the GUI to create an empty doc, there are no probs.

Any hints?  So far the workaround has been to right click, and click the write box under permissions...

-Thanks in advance.

---

### Post by pro003 on 2008-08-06
Hi, it actually might help you but I'm not so sure if you could try installing ubuntu tweak - try latest version. This tool gives you access to some powerful ubuntu features.

hope I helped you...

---

### Post by prshah on 2008-08-06
> **soumo said:**
> "create document --> new text file"

I don't seem to have this option (I have "Empty File") so maybe you are using a custom script for this; can you check in ~/.gnome2/nautilus_scripts ? If this is the case, you can easily modify the script to include the permission/ownership change commands. If you run into difficulties, post back here with the script (if any) for further advice.

---

### Post by limasierra on 2008-08-06
Open nautilus in your home folder and check the option to show hidden files by clicking View > Show Hidden Files or by pressing Ctrl+h. Go to the ".config" folder and open "user-dirs.dirs". Check the line with```
XDG_TEMPLATES_DIR="$HOME/"
```and replace it by```
XDG_TEMPLATES_DIR="$HOME/.templates"
```Open a new file in your text editor and save it blank in ```
/home/yourusername/.templates
```as```
new text file.txt
```

---

### Post by soumo on 2008-08-07
Thanks limasierra!


that did the trick, it turns out the template file was already there with the messed up permissions, I just had to repair it there!

---

