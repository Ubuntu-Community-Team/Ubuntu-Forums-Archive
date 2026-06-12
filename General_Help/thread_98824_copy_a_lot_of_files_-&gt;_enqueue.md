---
title: "copy a lot of files -&gt; enqueue"
date: 2005-12-04
forum: General Help
---

### Post by caplod on 2005-12-04
for example: you want to copy a lot of different files (like folders of mp3s). 
Is there a way (in Nautilus?) to enqueue these files instead of drag ´n drop them and copying them simultaneosly?

(like totalcommander for windows, where you can do that)

---

### Post by kamagurka on 2005-12-04
In the commandline, simply "cp -r"ing them should copy them over one by one. If you want to make sure, you can do
```
for i in *; do cp -r $i /foo/bar; done
```Dunno how to do it in GUI, tho.

---

