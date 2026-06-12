---
title: "problem when i open Guitar Pro 5"
date: 2008-11-22
forum: General Help
---

### Post by eitan3 on 2008-11-22
when i try to open GP5 it says something about gdiplus.dll and stuck

[http://s4.tinypic.com/11aesyc.jpg]("http://s4.tinypic.com/11aesyc.jpg")

---

### Post by cillino25 on 2009-01-03
Hi.
I had that problem too, and I resolved it reading in the wine forums.
I post here the passes you have to do, but you can go here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782&iTestingId=34553](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782&iTestingId=34553) for a more comprehensive solution.

Enter winecfg -> [Application] tab -> adding application "GP5.exe" -> while being choosen "GP5.exe" go to -> [Libraries] tab and choose in "New override for library" [gdiplus.dll] -> Press [Edit] button -> in the appeared popup-window choose "Builtin then Native" -> accept [OK] in all previously opened windows of winecfg.

Hope it'll be useful.

Stefano

---

### Post by bryncoles on 2009-01-03
if this is still an issue, why not try tuxguitar? it plays guitar pro files and can be installed from the repo's. 

you might need a little help setting it up, but you'll find that on the forums if needs be!

---

