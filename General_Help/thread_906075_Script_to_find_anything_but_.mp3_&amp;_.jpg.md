---
title: "Script to find anything but .mp3 &amp; .jpg"
date: 2008-08-31
forum: General Help
---

### Post by etereo on 2008-08-31
Hi,

I'm rather new to Ubuntu, and I've been trying to make a script that will list me all the files from a folder (recursively) which aren't .mp3 nor .jpg (album covers).  My portable player can only handle .mp3 and since I have some .wma (et al) in my collection I need to select all those and convert to .mp3

Any help would be greatly appreciated!

Brgds,

E.

---

### Post by jespdj on 2008-08-31
I think something like this should work:
```
find /some/directory ! -regex '\(.*\.mp3\)\|\(.*\.jpg\)'
```
See 'man find' for details. Replace '/some/directory' with the name of the directory where you want to find files.

'find' uses the [Emacs syntax for regular expressions](http://jamesthornton.com/emacs/node/emacs_97.html).

---

### Post by ghostdog74 on 2008-08-31
no need to use regexp. 
```

 find /path -type f \( ! -name "*.THM" -a ! -name "*.jpg" \)

```

---

### Post by etereo on 2008-08-31
Excellent!  Thnx for both responses.  

This was exactly what I needed.

---

