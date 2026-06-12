---
title: "Multiple computer sync to NAS"
date: 2008-09-08
forum: General Help
---

### Post by g7kse on 2008-09-08
I've spent about an hour searching around but couldn't find an answer to what I was looking for.

I have an Advent 4211 netbook (belongs to the wife really)- windows XP , A desktop Ubuntu and a 16Gb pen drive. Lastly a WD Mybook NAS.

I'd like them all to have the same contents to certain folders - call it the  documents folder. I can sync the netbook to the NAS (Goodsync) and the pendrive to the NAS using a portable app thats on the pendrive that I use on my work PC (Winmerge). This runs ok under wine but I'd like to use a native app for the pen drive. But there doesn't appear to be anything obvious for the desktop. Or can i not see the wood for the trees?

I'm sure there must be a gui app that does this but perhaps I'm looking in the wrong place. Any suggestions greatly appreciated.

Alex

---

### Post by vanadium on 2008-09-08
To mirror directory trees, you can use

```

rsync -av --delete <source> <destination>

```

The utility unison allows to really "synchronize", i.e. make two directory trees similar where changes occurred on both sides.

---

### Post by g7kse on 2008-09-09
Thanks for the info. appreciated

Alex

---

### Post by kostkon on 2008-09-09
A very good GUI synchronisation app is [*Conduit*]("http://www.conduit-project.org/"). Although, I don't know if it will cover your needs. You can install it from the repos or get the latest version from [*getdeb.net*]("http://www.getdeb.net/app/Conduit").

---

### Post by g7kse on 2008-09-09
They both look promising. Thanks for your help

Alex

---

