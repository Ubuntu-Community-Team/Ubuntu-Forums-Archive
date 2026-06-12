---
title: "Downloading with WINE"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Celestika6 on 2009-03-21
I have a WINE beta version for Ubuntu 8.10 (intrepid). Do I do something special when downloading a windows program or does WINE just do it all itself. I'm sort of a n00b and I really want to download[ Perfect World. ]("http://www.perfectworld.com") <--- link for the site if you guys want to take a look at the file yourselves.

---

### Post by taurus on 2009-03-21
You need to configure wine first before you run/use it.  Look in Applications -> Wine -> Configure Wine.  If you don't have a menu for wine, then run it from a terminal.

Applications -> Accessories -> Terminal
```
winecfg
```
Wine will not download windows apps for you.  You have to do that yourself.  Then, use wine to either install it or run it.

```
wine filename.ext
```
And keep in mind.  Wine is _not_ the magic potion so don't except it to run every windows program out there.

---

### Post by Mark Phelps on 2009-03-21
To expand on what Taurus said ...

Wine is not the "miracle cure" that some fanatics claim, in fact, CodeWeavers keeps a database of application testing results that shows while some apps work great, others work poorly or not at all.

The link below is to their database page for Perfect World.  Given the Bronze and Silver ratings, there are some things that will not work. Read their detail pages to find out the limitations.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6191]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6191")

---

### Post by RIT_girl on 2009-03-21
When I was having trouble in WINE, I went to a bunch of WOW threads to see how they configured it. Hope that helps point you in the right direction!

---

