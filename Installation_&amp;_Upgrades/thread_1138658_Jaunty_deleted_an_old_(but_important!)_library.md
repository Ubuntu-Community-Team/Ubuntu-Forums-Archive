---
title: "Jaunty deleted an old (but important!) library"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by russellchamp on 2009-04-26
Hey!  So I upgraded to Jaunty (worked great thru the software updates manager) but Jaunty just decided that one of the libraries that mplayer uses just wasn't necessary anymore and deleted it. 
Whenever I start mplayer, I get the message

```
mplayer: error while loading shared libraries: libartsc.so.0: cannot open shared object file: No such file or directory
```

I've looked all around the package manager (using both the graphical interface and apt-cache) and online but I cannot find any place where I can get this library back.  Any help?  Please?

---

### Post by russellchamp on 2009-04-26
Well, nevermind... I solved the problem on my own and with a little help from the IRC room.  I ended up compiling mplayer from the latest source myself and it ended up working just perfect!  So, for anyone else having the same problem... try that!

---

### Post by Poyntz on 2009-05-09
I did, but it didn't work for me :/

---

### Post by ticket on 2009-08-15
I had the same problem - but recompilation does work - if you do it carefully.

The first thing to do is clean out your existing compile.  Go to the directory where you compiled mplayer and do a

```
sudo make uninstall
```

Then delete the whole mplayer compilation directory.

Get a fresh mplayer using svn.

Redo the mplayer compilation and install, as normal.
There you go!

The problem seems to arise when you try to upgrade an existing mplayer compilation directory.  You really do have to throw the old one away and start anew.

And you don't need that libartsc.so (whatever it does).

---

### Post by charding on 2009-09-17
I think if you do a 'make distclean' after the 'make uninstall' this should help. Do the distclean instead of removing the whole svn directory and re-downloading it, which probably takes a lot more time.

---

