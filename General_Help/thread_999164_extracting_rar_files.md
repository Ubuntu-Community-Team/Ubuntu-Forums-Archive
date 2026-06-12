---
title: "extracting rar files"
date: 2008-12-01
forum: General Help
---

### Post by oilspot on 2008-12-01
I've dowloaded a few things that are in a rar format. It's nothing that I need to run on my computer, I just need to be able to unzip the files so I can put them on my stupid little psp.
 I used to just use winzip when I was running windows. Is there a equlivent for ubuntu (I'm sure there must be)

---

### Post by Idefix82 on 2008-12-01
```
rar x /path/filename.rar
```
with appropriate substitutions for /path/ and for filename.rar

---

### Post by MattBD on 2008-12-01
There is one, and it's called unrar. I think it's preinstalled in Ubuntu. However, it's command line only. If you have to install it, just enter sudo apt-get install unrar.

Try [this link]("http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux") for a simple guide to unrar.

---

### Post by binbash on 2008-12-01
unrar e asdasdasd.rar

---

### Post by noway on 2008-12-01
After installing the package unrar you can extract files as usual by either double clicking or right clicking and choosing the suitable option in the menu. No need for terminal unless you want to.

---

### Post by m_l17 on 2008-12-01
Change to the folder containing the *.rar file and extract it:
 
```
$ cd /location/of/folder/

$ unrar e filename.rar
```

[https://help.ubuntu.com/community/FileCompression]("https://help.ubuntu.com/community/FileCompression")

---

