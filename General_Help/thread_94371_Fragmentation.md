---
title: "Fragmentation"
date: 2005-11-23
forum: General Help
---

### Post by Alpha_toxic on 2005-11-23
Please someone tell me wich are the tools for defragmenting in Linux. Some more detailed info on ext3 and how it's affected by fragmentation would also come in handy.

---

### Post by aysiu on 2005-11-23
[http://en.wikipedia.org/wiki/EXT3](http://en.wikipedia.org/wiki/EXT3)

---

### Post by Alpha_toxic on 2005-11-24
10x, exactly what I was looking for.
P.S. I should get used to searching the wiki first and then asking...
It loks like it's all there.

---

### Post by fourhead on 2005-11-24
Fragmentation? Whats this? ;-) Calm down, this is a Windows issue.

Well, all Linux filesystems (ext2, reiser etc.) do fragment a little, you'll see this when the filesystem check is done, but this fragmentation usually never rises over a few percent (it's 0.xx% most of the time). This little fragmentation is normal and there's absolutely no need to "defragment" this.

Tom

---

### Post by Alpha_toxic on 2005-11-24
I suspected sth like that, but I wanted to be sure... It never hurts to doble-check.

---

