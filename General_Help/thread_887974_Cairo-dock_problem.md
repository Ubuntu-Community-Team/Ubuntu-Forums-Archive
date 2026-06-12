---
title: "Cairo-dock problem"
date: 2008-08-12
forum: General Help
---

### Post by chaosdesigner on 2008-08-12
Hi,

I have a problem running cairo-dock on my Ubuntu 8.04 64 bit Machine. I know there is a how-to but nothing worked for me. I have installed it exacly the way it said and i get this message:

```
cairo-dock: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

```

I have already tried to install this library with this command:

```
getlibs -l libdbus-glib-1.so.2
```

But i get tis message:

```
Looking up libdbus-glib-1.so.2 on web interface: 
No match
Using mirror http://ch.archive.ubuntu.com/ubuntu/

```

Does anyone know what i can do?

Thank you

---

### Post by chaosdesigner on 2008-08-13
*bump*

Doesnt anybody have a solution for this?

---

### Post by BuDDhaZ on 2008-08-13
Same problem here... using Hardy..

---

### Post by BuDDhaZ on 2008-08-13
I am also having problems, only it is a different lib

cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

According to my package manager libglitz-glx1 is installed...

I am pretty much a newbie when it comes to linux though... maybe I am missing something obvious here.

---

### Post by chaosdesigner on 2008-08-13
Ok, i got it working now.

For everyone who hasnt got it, look at this page, it really helped me: [http://ubuntuforums.org/showthread.php?t=613087](http://ubuntuforums.org/showthread.php?t=613087).

What I did: I upgradet getlibs, and then I removed cairo dock and installed it with this command again:

```
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

I dont know it just worked, on the page I mentioned are alot of ways that it can be done.

---

### Post by cleopete on 2008-08-15
I found this elsewhere in the forum, run this (assuming you've installed getlibs):


 getlibs /usr/bin/cairo-dock c

then enter:

 sudo apt-get -f install

Worked for me after much fruitless Googling.

Good luck.

---

