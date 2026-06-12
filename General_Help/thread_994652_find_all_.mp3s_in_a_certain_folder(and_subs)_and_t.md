---
title: "find all *.mp3s in a certain folder(and subs) and the copy them in some other folder"
date: 2008-11-27
forum: General Help
---

### Post by essell55 on 2008-11-27
find all *.mp3s in a certain folder(and subs) and the copy them in some other folder?


Edit : But in the second folder i want to lose the folder hierarchy... you know like going From
mp3s/band 1/songi.mp3
mp3s/band 2/song 35.mp3

to
secondfolder/songi.mp3
secondfolder/song 35.mp3

lol thx in advance

---

### Post by sisco311 on 2008-11-27
try:
```
find */path/to/mp3* -type f -iname "*.mp3" -exec cp {} */dest/folder*/ \;
```

---

### Post by essell55 on 2008-11-27
thx ill try tonight

---

### Post by essell55 on 2008-11-27
thx it works! lol but its slow.. maybe its cuz im doing it from USB FAT32 to NTFS :P

---

### Post by sisco311 on 2008-11-27
you can try:
```
find */path/to/mp3* -name '*.mp3' -type f \
  -exec sh -c 'exec cp -f "$@" */dest/folder*' find-copy {} +
```

---

