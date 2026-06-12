---
title: "Add/Remove not Working?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Runefoger on 2009-05-09
i am trying to add some new games using Add/Remove, but whatever i tell it to download, it brings back similar errors to this:

> [I]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb)
  404 Not Found[/I]

either that, or it installs half of something, then tells me that some packagaes were unretreivable...

the same happens when trying to install with Synaptics.

any help would be greatly appreciated!

---

### Post by Partyboi2 on 2009-05-09
Hi, open up Software Sources (System>Admin>Software Sources) and try changing your download server under the first tab to another one.

---

### Post by Runefoger on 2009-05-09
well, thats just revealed a whole new problem...

when i changed it from UK to Main it said that the data was out of date and i needed to reload the info the continue, when i did that, it told me it was downloaded 50-something packages, none of which worked...

heres the first 2 on the list as an example:
> [i][http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80][/i]
along with this Error Info:
> *The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.*

messed with other download servers besides UK and Main, and got the same thing...

---

### Post by Partyboi2 on 2009-05-09
What version of Ubuntu are you using? If you are using Gutsy I highly recommend  upgrading to a later release as Gutsy has reach its end of life.

---

### Post by Runefoger on 2009-05-09
im using Ubuntu 7.10 - the Gutsy Gibbon

Linux is stopping downloads to gutsy now? why's that?


::EDIT::

right, im about to upgrade now, but does upgrading delet any files on my harddrive besides the 7.10 packages? as if it does, i will back them up first...

---

### Post by Runefoger on 2009-05-09
this still hasnt been solved... can someone please answer my question? haha

but yeah, has linux stopped allowing downloads to anything below 7.10? and will upgrading delete any files in my user area?

---

### Post by Partyboi2 on 2009-05-09
Every version of Ubuntu has a end of life date, when that date is reached it is no longer supported and you will not receive any new updates as well as the repos move to  **old**-**releases**.ubuntu.com. You can still install packages but you will need to comment out your current repo entries in your sources.list and add
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
```


Upgrading will not remove anything from your /home

---

### Post by Runefoger on 2009-05-09
brilliant! upgrading fixed the problem

cheers man! i appreciate it!

---

