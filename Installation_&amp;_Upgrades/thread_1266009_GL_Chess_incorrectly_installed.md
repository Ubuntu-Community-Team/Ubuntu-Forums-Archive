---
title: "GL Chess incorrectly installed"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by orsenthil on 2009-09-14
I like GL Chess program better than other alternatives. In my ubuntu 9.04, when I try to start GL Chess, a dialog box comes up and says, GL Chess is Incorrectly Installed.


> Chess is not able to start because required application files are not installed. If you are currently upgrading your system please wait until the upgrade has completed.
I try uninstall/purge and install of gnome-games and nothing happens.

Any troubleshooting steps?

---

### Post by earthpigg on 2009-09-14
run it from a terminal, and take a look at the output there?

i have run into stuff that did not have things it should have listed as dependancies before:

[http://ubuntuforums.org/showpost.php?p=7105928&postcount=3](http://ubuntuforums.org/showpost.php?p=7105928&postcount=3)

---

### Post by earthpigg on 2009-09-14
i'd look for places *other than debian and ubuntu websites*, such as this, that list dependancies.

[http://www.gtkfiles.org/app.php/glChess](http://www.gtkfiles.org/app.php/glChess)

if the folks that wrote glchess list something as a dependancy, but the folks at debian and ubuntu did not include that as a dependancy then... well.... i suppose we can forgive debian for making a mistake or two considering the tens of thousands of packages they need to maintain, right? :D



it may not be a depen issue at all, of course. need to see terminal output and make sense of it.

---

### Post by orsenthil on 2009-09-15
Thanks for the reply. There isn't any terminal output when I typed glchess in the terminal. The error log is hidden or swallowed by the gui, I guess. But I did look around the links that you mentioned.
I see the problem could be that, glchess too much depends upon Python2.4.
while in Ubuntu 8.10, the Python2.4 was listed in the supported versions in /usr/share/python/debian_defaults from Ubuntu 9.04 onwards, this is no longer the case.

I can install python2.4 and edit the above file and try again.
Or try to complie glchess using Python2.5 ( i am trying to do that now).

I have raised a bug report to glchess to upgrade the support to python2.5.

Thanks again!

---

