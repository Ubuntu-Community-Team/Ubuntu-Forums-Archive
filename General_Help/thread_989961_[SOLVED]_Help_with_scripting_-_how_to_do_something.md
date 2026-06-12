---
title: "[SOLVED] Help with scripting - how to do something for all files in a directory"
date: 2008-11-22
forum: General Help
---

### Post by djbushido on 2008-11-22
I could use some help with performing an operation on all files in a directory.
For example, adding an album tag to all the mp3 files in a folder.
Any help would be appreciated, thank you!

---

### Post by geirha on 2008-11-22
If the command only accepts one file at a time, then a for loop is generally what you use
```

for file in *.mp3; do
  echo run some command on "$file"
  echo maybe even two commands on "$file"
done
# You can also do that on one line by using ; instead of newlines.
for file in *.mp3; do echo run some command on "$file"; echo maybe even two commands on "$file"; done

```

EDIT:
And if you want to do it on all mp3 files in all subdirectories as well, you can use find in this way:
```
find -name "*.mp3" -exec echo run some command on {} \;
```

---

### Post by djbushido on 2008-11-22
Thanks!, looks good
I just haven't done much scripting other than using it as a macro pretty much...

---

### Post by djbushido on 2008-11-22
Thanks!, looks good
I just haven't done much scripting other than using it as a macro pretty much...

---

