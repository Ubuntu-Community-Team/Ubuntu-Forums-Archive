---
title: "newbe mistake with firefox"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by sandmouse on 2009-11-12
Ubuntu 9.04 desktop

Ok I made the mistake of installing firefox 3.5.5 with the help of some web page! It worked till today when I updated my software. Something installed and firefox dosen't work now! I tried to de-install it and re-install but no luck! If we dont play we don't learn!

---

### Post by mikewhatever on 2009-11-12
Is it possible to provide the link to the 'some web page'? Can you try launching Firefox from Terminal, but typying firefox, and post the output.

---

### Post by sandmouse on 2009-11-12
Sorry I can not find The web page. When I type firefox in a terminal windows it opens shiretoko. Yes I need to read more, linux is not windows! LOL

---

### Post by mikewhatever on 2009-11-12
Hmm...,  thought you said Firefox didn't work. Did you know that Shiretoko is Firefox 3.5 with different branding, and its current version in the repositories is indeed 3.5.5.

---

### Post by winotree on 2009-11-12
Delete the file .mozilla in your /home/user -- if you can't see it click Ctrl+h [show hidden files].  This contains the Firefox configuration files.  Anything you do will remain the same as long as it's there -- *but be sure to save your bookmarks first*.

Then use Synaptic Package Manager to reinstall **Firefox-3.5** [version 3.5.4] and add your bookmarks.  That ought to do it.

EDIT - what **mikewhatever** said!  And it's very polished for a pre-release, too.  ;)

---

### Post by aysiu on 2009-11-12
> **sandmouse said:**
> Ubuntu 9.04 desktop

Ok I made the mistake of installing firefox 3.5.5 with the help of some web page! It worked till today when I updated my software. Something installed and firefox dosen't work now! I tried to de-install it and re-install but no luck! If we dont play we don't learn!
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here: ```
cat /etc/lsb-release
uname -a
dpkg -s firefox
dpkg -s firefox-3.5
ls -l /usr/bin/firefox
ls -l /opt/
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by wojox on 2009-11-12
Is this 9.04, 9.10? Did you add any ppa's?

---

### Post by mikewhatever on 2009-11-12
> **winotree said:**
> Delete the file .mozilla in your /home/user -- if you can't see it click Ctrl+h [show hidden files].  This contains the Firefox configuration files.  Anything you do will remain the same as long as it's there -- *but be sure to save your bookmarks first*.

Then use Synaptic Package Manager to reinstall **Firefox-3.5** [version 3.5.4] and add your bookmarks.  That ought to do it.


Renaming .mozilla is a better idea, for example, .mozilla-old or something like that.

---

### Post by winotree on 2009-11-12
> **mikewhatever said:**
> Renaming .mozilla is a better idea, for example, .mozilla-old or something like that.
Mmm -- that's true.  I didn't consider that and didn't think at the moment that it was appropriate to talk about a back-up [I do grsync of /user every evening].  Wonder how **sandmouse** is getting along??

---

### Post by sandmouse on 2009-11-12
thanks for all The idea's, I got it to work! I had 3 versions installed 3.0 something 3.5 and 3.55, but a mixture of supporting files, with that said I had to sudo and command line delete everything because GUI package manger really doesn't totally remove files! Once I did that I re-installed 3.5.5 witch is now supported and everything works fine! Once again thanks for all the help!

SandMouse | Former windoze user and Lego Builder guru

---

