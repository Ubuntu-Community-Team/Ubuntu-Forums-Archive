---
title: "Find missing Files in directory"
date: 2008-12-01
forum: General Help
---

### Post by samuraix51 on 2008-12-01
I have about 1300 pictures that I am trying to organize.
They are numbered sequentially eg. ( 0001.jpg -> 1300.jpg )
The problem is that I seem to be missing some, when I highlight all of them, the number it shows is something around 1291 files.

Is there a fast way to be able to scan the directory to see which ones I am missing? Other than to do it manually, which would take a long time.

---

### Post by HalPomeranz on 2008-12-02
```

for i in $(seq -w 1 1300); do
    [ ! -f $i.jpg ] && echo $i.jpg
done

```

The above code will check all file names from 0001.jpg through 1300.jpg and print the names of the files in that sequence that are not there.

---

### Post by samuraix51 on 2008-12-02
Thanks, that did it, I found the missing ones.

---

