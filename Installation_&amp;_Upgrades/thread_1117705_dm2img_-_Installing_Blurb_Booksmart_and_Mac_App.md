---
title: "dm2img - Installing Blurb Booksmart and Mac App"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2009-04-06
Hi,

I try to install Blurb Booksmart software following [this guide]("http://www.flickr.com/photos/mydailycommute/391528303/#comment72157605398264838"). I have to install [dmg2img]("http://vu1tur.eu.org/tools/") to access the Mac version.

But I fail at installing dmg2img. I follows [this guide on Ubuntuforums]("http://ubuntuforums.org/showpost.php?p=3358268&postcount=3"), which is for an older version. But gcc won't compile the source code. This is the output:

```
timo@aristoteles:~/Desktop$ tar -zxvf ./dmg2img-1.3.tar.gz 
dmg2img-1.3/
dmg2img-1.3/Makefile
dmg2img-1.3/README
dmg2img-1.3/vfdecrypt.1
dmg2img-1.3/vfdecrypt.c
dmg2img-1.3/vfdecrypt.h
dmg2img-1.3/dmg2img.c
dmg2img-1.3/dmg2img.h
dmg2img-1.3/base64.c
dmg2img-1.3/base64.h
dmg2img-1.3/COPYING
timo@aristoteles:~/Desktop$ cd dmg2img-1.3
timo@aristoteles:~/Desktop/dmg2img-1.3$ make all
gcc -O2 -Wall -c dmg2img.c
In file included from dmg2img.c:30:
dmg2img.h:20:18: error: zlib.h: No such file or directory
In file included from dmg2img.c:30:
dmg2img.h:36: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »z«
dmg2img.c: In Funktion »main«:
dmg2img.c:75: Fehler: »Bytef« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:75: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
dmg2img.c:75: Fehler: für jede Funktion in der er auftritt.)
dmg2img.c:75: Fehler: »tmp« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:75: Fehler: »otmp« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:75: Warnung: linker Operand des Komma-Ausdrucks hat keinen Effekt
dmg2img.c:163: Fehler: expected expression before »)« token
dmg2img.c:164: Fehler: expected expression before »)« token
dmg2img.c:206: Fehler: »z« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:206: Fehler: »alloc_func« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:206: Fehler: expected »;« before numeric constant
dmg2img.c:207: Fehler: »free_func« nicht deklariert (erste Benutzung in dieser Funktion)
dmg2img.c:207: Fehler: expected »;« before numeric constant
```

Any idea what is missing?

Timo

---

### Post by gillespiea on 2010-02-24
no idea if you have got this sorted, and i know this is an old post. but i have found the lovely answer and i couldnt find it anywhere for a while. but here it is :)

[http://packages.ubuntu.com/lucid/dmg2img]("http://packages.ubuntu.com/lucid/dmg2img")

---

