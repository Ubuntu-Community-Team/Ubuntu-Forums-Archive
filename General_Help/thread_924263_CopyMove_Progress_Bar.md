---
title: "Copy/Move Progress Bar?"
date: 2008-09-19
forum: General Help
---

### Post by TheWired on 2008-09-19
I often use the command line to move and copy files from drive to drive. I like the GUI progress bar that Nautilus uses when copying files from one folder to another. Are there any command line flags/programs/packages that I could use that would give me a progress bar inside the terminal?

---

### Post by bingoUV on 2008-09-19
Midnight commander. Type "mc" at the command prompt. Switch between the 2 directory panels with ctrl-ci. Use F1 help for more details.

---

### Post by TheWired on 2008-09-19
I was more interested in something I might be able to script with. I have a large number of files that I want backed up from drive to drive and would like to see a progress bar when I run my script, preferably something that just ran on the command line (like when grabbing a package or using wget).

---

### Post by bodhi.zazen on 2008-09-19
Interesting, this came up in another thread as well.

For the command line : [http://clpbar.sourceforge.net/](http://clpbar.sourceforge.net/)

If you wish to use X, go with zenity.

---

### Post by DanCar on 2012-02-18
rsync

rsync -rv <src> <dst> --progress 
r = recursive 
v = verbose

---

### Post by oldos2er on 2012-02-18
Closed, necromancy.

---

