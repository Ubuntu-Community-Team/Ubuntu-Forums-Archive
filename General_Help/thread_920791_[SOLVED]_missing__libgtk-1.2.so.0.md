---
title: "[SOLVED] missing  libgtk-1.2.so.0"
date: 2008-09-15
forum: General Help
---

### Post by Tom Atkins on 2008-09-15
I am trying to run an ELF program which needs the above shared library. Synaptic can not find it. Where do I look?

---

### Post by phidia on 2008-09-15
How did you install the program? Is there a README file to follow and what version of Ubuntu are you running?

---

### Post by Tom Atkins on 2008-09-15
I downloaded a tar gz file. Here is the beginning of the README file:

> CheckBook Tracker Copyright (c) 2002-2003 Anthony Maro
This program is covered under the GPL license (see license.txt)

This is the ELF executable (that means, you run the program "cbtracker" 
from the command prompt or make an icon for it with the included icon 
file in your desktop environment.)

I am running the Heron version with all updates applied.

---

### Post by mdecler2 on 2008-09-15
Did you try installing any of these packages from the repos?
```

sudo apt-get install libglib1.2-dev libgtk1.2-dev

```

---

### Post by Tom Atkins on 2008-09-15
I ran those two and now I get > ./cbtracker: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory

---

### Post by mdecler2 on 2008-09-15
Try:
```
sudo apt-get insall libgtk2.0-dev libgtk2.0-common libgtk2.0-dev
```
You can find all of these doing an
```
 apt-cache search <SOME_SEARCH_STRING>
```
where <SOME_SEARCH_STRING> is your search string to look for in the repos.

If you still have problems, please answer these questions:
Have you recently upgraded to Hardy? Did you upgrade over the interent (do-release-upgrade)?

---

### Post by Tom Atkins on 2008-09-16
I ran those installs and still get the same error.

I was running Suse 10.0 and purchased the Hardy DVD from Amazon and installed it on its own disk a couple of weeks ago. I have had nothing except linux on my PC for about 5 years.

---

### Post by mdecler2 on 2008-09-16
As far as I know, you just don't have the right dependencies installed.

Again, using the apt-cache search command I find packages libgdk-pixbuf-dev and libgdk-pixbuf2.

---

### Post by Tom Atkins on 2008-09-16
I used Synaptic and found those libs, and another, and the program worked. Thank you!!!!

Tom

---

