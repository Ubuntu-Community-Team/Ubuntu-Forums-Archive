---
title: "Upgrade from Jaunty (9.04) to Karmic Koala (9.10) corrupts Banshee 1.4.3 database"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by forward_swept_wings on 2009-11-05
When I upgraded from Jaunty to the official release of Karmic Koala (9.10) (not alpha / beta or RC), Banshee was upgraded from 1.4.3 to 1.5.1.

As a result, some of my tracks failed to play reporting the following error:

> Problem with Player Engine

Object reference not set to an instance of an object


I came across this post: [http://ubuntuforums.org/showthread.php?t=1288125]("http://ubuntuforums.org/showthread.php?t=1288125") which inspired me to look deeper into the problem. I discovered that the root cause appeared to be how the location of each file was being stored.

For example the file path in 1.4.3 is:
> Urban/Michael Jackson/2009 - King Of Pop/Michael Jackson - 46 - Smooth Criminal (Ext Dance Mix).mp3

Whereas for 1.5.1 it takes the following format:
> file:///path/to/music/folder/Urban/Michael%20Jackson/2009%20-%20King%20Of%20Pop/Michael%20Jackson%20-%2046%20-%20Smooth%20Criminal%20(Ext%20Dance%20Mix).mp3

The two key differences are the absolute path (i.e. inclusion of file:///path/to/music/folder/) and spaces replaced with "%20".

As a work around, I wrote this short python script:

```
import sqlite3

con = sqlite3.connect('banshee.db')
c = con.cursor()
a = con.cursor()
c.execute("SELECT TrackID, Uri from `CoreTracks`")

for row in c:
    original = unicode(row[1])
    id = str(row[0])
    if original.find("file:///path/to/music/folder/") < 0:
        original = "file:///path/to/music/folder/" + original
        
    if original.find(" ") > -1:
        original = original.replace(" ","%20")
    
    print id + "  " + original
    
    t = (original, id)
    
    a.execute("update `CoreTracks` set Uri=? where TrackID=?", t)

print "all done"
con.commit()
```

Save the file as say: update.py and place it in the same place as the banshee database in your home folder:

```
/home/userid/.config/banshee-1/
```

Then open a terminal in the folder, and type the following:

```
python update.py
```


I hope you found this useful. I'll make sure that the Banshee team are informed if they haven't been already.

---

