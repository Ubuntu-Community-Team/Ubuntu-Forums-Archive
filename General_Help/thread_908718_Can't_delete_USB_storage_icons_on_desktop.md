---
title: "Can't delete USB storage icons on desktop"
date: 2008-09-02
forum: General Help
---

### Post by eyehatehippies on 2008-09-02
For some reason Ubuntu recognizes the USB flash drive right away and i can transfer the files to my Linux computer. The only problem is every time i insert the storage device it throws a new icon onto the desktop and the system is not letting me delete the icons. What gives?

---

### Post by rossjman1 on 2008-09-02
Does the icon go away after removing the usb device? It should. To get rid of volume icons on the desktop do this:
type "gconf-editor" in the terminal (w/o quotes)
go to apps > nautilus > dekstop
uncheck volumes visible (from this screen you can also enable/disable other icons as well)

---

### Post by DapperMe17 on 2008-09-02
Likely, your drive is "mounted". You simply need to "unmount" by right-clicking on the drive. The icon will dissappear automatically.

---

### Post by Jonie on 2008-09-02
What's inside your /media folder (ls -l /media)? What version of Ubuntu are you using?

---

