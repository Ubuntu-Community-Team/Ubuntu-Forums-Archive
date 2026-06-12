---
title: "Don't know the location of program that I've downloaded"
date: 2008-09-21
forum: General Help
---

### Post by pounditflat on 2008-09-21
I don't know where programs that I download from the internet are, so I can't install or open. I need some help with instructions on how to open/install downloaded programs and/or their location. Thanks

---

### Post by lswest on 2008-09-21
If you don't know where it is just do this: ```
sudo updatedb
locate [filename]
``` then cd to the directory and execute.  (From a terminal)

Execution will vary depending on the filetype, if you need more help, post a bit more info about the files.

---

### Post by kokkus on 2008-09-21
Default firefox settings are Desktop.
You can see your current settings under edit > properties in firefox.

---

### Post by lisati on 2008-09-21
+1 for the "locate" command.....
If you use the Applications->Add/Remove method of installing software, it will usually tell you where to look on the menu. 
Common locations for downloading files include the desktop (there will be an icon on your desktop) and your "home" folder (check the "Places"->"Home" menu option)

---

