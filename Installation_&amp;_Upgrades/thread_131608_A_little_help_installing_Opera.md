---
title: "A little help installing Opera"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-16
Trying to get Opera installed. Went to the Wiki entry and followed the directions:

1) DLed the Opera file for Ubuntu (opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) to desktop.
2) Opened a terminal and typed: sudo dpkg -i opera_blahblahblah (the opera file name as noted above).
3) Entered password.

4) Received error:

> 
dpkg: error processing opera_8.51-20051114.6-shared-qt_en_etch_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_8.51-20051114.6-shared-qt_en_etch_i386.deb


What do I need to do? Do I need to put the file into a directory (if so, which one)? Or is the command wrong?

Oh, and as an aside: how come my Tab key doesn't fill in the file name if I type opera<Tab key> , where <Tab key> means I just press the Tab key, not actually type it  (is it something I need to configure)?

Thanks for any insight.

---

### Post by bluevoodoo1 on 2006-02-16
Code looks good, but if you're going to leave it on the desktop, you have to... 

cd Desktop

first, to get to the desktop. Or, you could move the file to your home folder then just go ahead with sudo dpkg .....

---

### Post by Coelocanth on 2006-02-16
[QUOTE=bluevoodoo1]Code looks good, but if you're going to leave it on the desktop, you have to... 

cd Desktop[/quote]

D'oh! Rookie mistake!

> first, to get to the desktop. Or, you could move the file to your home folder then just go ahead with sudo dpkg .....


Thanks for the help... again. ;)

---

### Post by bluevoodoo1 on 2006-02-16
hehe, no problem!

---

