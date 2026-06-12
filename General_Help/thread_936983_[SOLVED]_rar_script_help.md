---
title: "[SOLVED] rar script help"
date: 2008-10-03
forum: General Help
---

### Post by jdusablon on 2008-10-03
I have about 8000 jpg files that are scans from comics. I have them organized by volume/chapter/*.jpg.

I'd like to rar the contents of each subdirectory into it's own rar.

I've tried this:

```
find -iname *.jpg -exec rar a "`dirname {}`.cbr" {} \;
```

but the it keeps creating only one file called ..cbr

I know I just need a little push in the right direction...

Can anyone help me?

---

### Post by mooseydoom on 2008-10-03
The shell expands the `dirname {}` before find can exec the command, so the expanded command looks like
```
find -iname *.jpg -exec rar a "..cbr" {} \;
```

Try using this:
```
for file in `find -iname "*.jpg"`; do rar a "`dirname $file`.cbr" $file; done
```

---

### Post by jdusablon on 2008-10-03
Hey, thanks! That worked beautifully!

I thought it didn't at first, but the rar command doesn't like spaces in filenames, which I can probably fix with quotes or something "escapy"

---

