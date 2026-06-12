---
title: "Dual Boot Multiple Linux Distros"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by sizzlefire on 2009-01-25
Hello, I am wondering if it is possible to install multiple linux distros with minimal work? I currently have ubuntu 8.10, and would also like to get damn small linux (and try linuxmint) without having to use a CD (cause I don't have any blank CD's), is this possible?

---

### Post by mikewhatever on 2009-01-25
Well, 'minimal work' is a relative term, so it's hard to advise. I'd suggest exploring a virtualbox option.

>  Dual Boot Multiple Linux Distros  

Not sure you can dual boot many distros, perhaps multi boot.

---

### Post by Jose Catre-Vandis on 2009-01-25
Have a look here
[http://ubuntuforums.org/showthread.php?t=153169](http://ubuntuforums.org/showthread.php?t=153169)
and
[http://ubuntuforums.org/showthread.php?t=629386](http://ubuntuforums.org/showthread.php?t=629386)

for some ideas of what to do.

You can also just install in a certain order, ending up with a final grub on your mbr that "picks up" all the other distros. A good partition plan before you start is essential, and probably easy not to share /home, but you can share /swap.

---

### Post by linux_tech on 2009-01-25
You should be able to boot several linux os, as long as you have the hard drive space.
Automating the switch from os to os also looks interesting
[http://www.ibm.com/developerworks/linux/library/l-osswitch/](http://www.ibm.com/developerworks/linux/library/l-osswitch/)

---

### Post by Shazaam on 2009-01-25
To keep from running into the 4 primary partition limit I recommend that you do this...
1. ALL Windows os should be primary partitions.
2. Linux doesn't care either way so make an Extended partition in the remaining space to hold a shared logical swap partition and as many logical linux partitions that you have room for. Point them all to the one logical swap partition when installing.
So you would end up like this...
```
Primary Partition one= Windows
Extended Partition two=linux Logical partitions.
```
Here is a shot of one of my two drives (Windows XP is on sdb)...
sda6 is PuppyLinux, sda7 is Mepis, sda8 is Hardy, and sda9 is Intrepid.

---

