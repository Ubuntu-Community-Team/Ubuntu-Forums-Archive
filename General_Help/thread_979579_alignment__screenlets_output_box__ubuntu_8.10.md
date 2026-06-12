---
title: "alignment / screenlets output box / ubuntu 8.10"
date: 2008-11-12
forum: General Help
---

### Post by p.becks on 2008-11-12
Hello,

I am running screenlets on ubuntu 8.10. One of my favourite screenlets is the OUTPUTBOX. In this box i can run a (or more) linux/unix command at various intervals. I run, for instance, the command:  

sudo du -h -x --max-depth=1 /usr/ (i like to keep an eye on some fast growing folders!)

in this box and the output looks like this: (IN A TERMINAL!)

25M	/usr/src
151M	/usr/bin
32K	/usr/local
14M	/usr/include
1.1G	/usr/lib
14M	/usr/sbin
986M	/usr/share
0	/usr/X11R6
2.3M	/usr/games
2.2G	/usr

In the outputbox it looks more like this:

25M sr/src
151M    /usr/bin
32K  /usr/local
14M   /usr/include
1.1G  /usr/lib
14M  /usr/sbin
986M   /usr/share
0 /usr/X11R6
2.3M    /usr/games
2.2G  /usr

Now i figure the reason that it looks like this is: because the outputbox can't handle the TAB very well.. (so i figure lets replace the tabs with a number off spaces:

 sudo du -h -x --max-depth=1 /usr/|sed 's/\t/        /g'

Now it looks better (but not perfect!)

it sorta looks like this right now:

25M     /usr/src
151M     /usr/bin
32K     /usr/local
14M     /usr/include
1.1G    /usr/lib
14M/    /usr/sbin
986M     /usr/share
0   /usr/X11R6
2.3M    /usr/games
2.2G    /usr


Can somebody help with getting the alignment right!

---

### Post by p.becks on 2008-11-12
sudo du -x --max-depth=1 /usr/|sort -g -k1

(works better!)

---

