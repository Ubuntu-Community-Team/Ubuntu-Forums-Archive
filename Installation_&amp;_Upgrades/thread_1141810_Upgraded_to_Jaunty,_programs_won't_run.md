---
title: "Upgraded to Jaunty, programs won't run"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by afderrick on 2009-04-28
So I just upgraded to Jaunty this past week.  now some of my kde based programs won't launch anymore.  Are there any settings I can tweek to get these apps working or am I stuck until an update is made to the app itself?  The error I am getting is:  

kmuddy: error while loading shared libraries: libartskde.so.1: cannot open shared object file: No such file or directory

Any help would be appreciated, I don't particularly want to go back to intrepid.  I guess I can, if I knew how. 

I have also looked for the libartskde package and cannot find anything.  Other people with the same issues (from the app's site forum) said it hasn't worked for them when they have found it.

---

### Post by afderrick on 2009-04-29
anyone have some suggestions?

---

### Post by vblanton on 2009-05-15
having a similar issue here.. So, the problem lies in the fact that its not possible to install kdelibs4-dev (kde3 development libraries) when kdelibs5 (kde 4 ones) is around.  If only we could install kdelibs4-dev, then everything would be alright.  Unfortunately, the kmuddy websites went down recently, but the development version of kmuddy (1.0rc2) is kde4 based and would work if we could get our hands on it..

All this i learned from here:
[http://209.85.229.132/search?q=cache:tpIIIm3IDMIJ:www.kmuddy.com/mercuryboard/index.php%3Fa%3Dtopic%26t%3D1390%26p%3D6353+kmuddy:+error+while+loading+shared+libraries:+libartskde.so.1:+cannot+open+shared+object+file:+No+such+file+or+directory&hl=ru&client=firefox-a&gl=ru&strip=1]("http://209.85.229.132/search?q=cache:tpIIIm3IDMIJ:www.kmuddy.com/mercuryboard/index.php%3Fa%3Dtopic%26t%3D1390%26p%3D6353+kmuddy:+error+while+loading+shared+libraries:+libartskde.so.1:+cannot+open+shared+object+file:+No+such+file+or+directory&hl=ru&client=firefox-a&gl=ru&strip=1")

---

### Post by vblanton on 2009-05-16
This is rather silly actually.  I think it should be possible to install kde3 development files alongside kde4 ones without any issue.  I'm thinking this is actually a bug and am considering filing it as such.. here is the output:

```
vblanton@ubuntu:~$ sudo apt-get install kdelibs4-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cvs gawk gettext-kde kdesdk-scripts libart-2.0-dev libaspell-dev libavahi-client-dev libavahi-qt3-dev libidn11-dev liblua50-dev liblualib50-dev libsasl2-dev lua50
Suggested packages:
  dmalloc kdelibs5-doc qt4-doc valgrind devscripts aspell-doc
[B]The following packages will be REMOVED:
  kdelibs5-dev libplasma-dev[/B]
The following NEW packages will be installed:
  cvs gawk gettext-kde kdelibs4-dev kdesdk-scripts libart-2.0-dev libaspell-dev libavahi-client-dev libavahi-qt3-dev libidn11-dev liblua50-dev liblualib50-dev libsasl2-dev lua50
0 upgraded, 14 newly installed, 2 to remove and 3 not upgraded.
Need to get 3061kB/4970kB of archives.
After this operation, 4674kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

UPDATE: The bug is filed at: [https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/287313]("https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/287313")

---

### Post by vblanton on 2009-05-17
There is so much new info that I decided to make a separate post.  The bug is unfixable. From the bug report:

> Sad to say, but this bug is not fixable. Both packages install files to
the same location, so there isn't a way we could get to coexist
peacefully.

so i emailed Tomas Mecir (created of kmuddy):

> There were some domain problems, and so the site now
runs at [www.kmuddy.com](www.kmuddy.com) ... - you can
get the latest version (1.0rc2) from the site.

so, from there you can get the latest kmuddy sources .. compile them.. and all should be well...

---

