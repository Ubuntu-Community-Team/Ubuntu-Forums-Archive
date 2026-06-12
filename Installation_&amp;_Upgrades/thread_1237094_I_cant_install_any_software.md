---
title: "I cant install any software"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by dieauserwalte on 2009-08-11
I cant install any software after an attempt at installing wine following the correct procedure for the actual app on the official website.This attempt failed installing wine and thereafter ubuntu wont install no software anymore.It was not my first time installing wine,i had done it in some other pc,i dont know what is happening now.The error message im being promted with is thus:
    
   
    'E:Type 'For' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


It appears everytime i try to install a new app,or when i try opening the synaptic package manager ,inclusively.Thanks in advanced! Im very new to Linux and im enjoying it to the maximum,in fact, i love it,please help me with this minor problem.

---

### Post by bhaverkamp on 2009-08-11
Very strange. Your source.list file should look as follows. See if you can find a line that has an E: in it somewhere. Sounds like a windows drive specifier got into your sources.list file somehow.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

---

### Post by roharme on 2009-08-11
Try updating Binaries and Libraries.
 
Wait for some good replies.
Just making this thread to ly on top

---

### Post by dieauserwalte on 2009-08-11
i cant even run the uodate manager!! oh man..

---

### Post by madhavhmk on 2009-08-11
please post your sources.list here...

---

### Post by P4man on 2009-08-11
In case you dont know where or what sources.list is, run this command from a terminal:

```
gksudo gedit /etc/apt/sources.list
```

Paste the contents of that file here, so we can tell you how to fix it.

---

