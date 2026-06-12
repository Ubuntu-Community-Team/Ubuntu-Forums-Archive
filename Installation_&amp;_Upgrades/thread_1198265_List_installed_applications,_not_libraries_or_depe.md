---
title: "List installed applications, not libraries or dependancies"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by irw on 2009-06-27
I am about to move to a new laptop and switch to 64-bit Ubuntu.

Is there a way to list what applications I have installed, but not all of the dependencies and libraries.?

I want to try to duplicate my existing (32-bit) system, but suspect generating a complete list of installed packages and trying to install this on the new (64-bit) system will cause problems.

Any ideas?

---

### Post by swisstone198 on 2009-06-27
sudo dpkg --list 


EDIT

sorry, didn't read your post correctly. This will show all including libs.

---

### Post by NiN on 2009-06-27
Well,

I did migrate from 32bit to 64 bit using ```
 dpkg --get-selections >list.txt 
``` and ```
 dpkg --set-selections <list.txt 
``` without any major problems (this was a view years ago). This method does install all applications and libraries you have installed currently on the new system, so I don't know, if this will break things for you.
But as far as I understand, there shouldn't be any problems, as the 64bit version of ubuntu uses the same package names as the 32 bit version, so the right one gets selected.

Hope this information can help you, and don't forget to backup before migrating ;)

---

