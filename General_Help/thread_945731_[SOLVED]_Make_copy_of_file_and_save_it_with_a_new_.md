---
title: "[SOLVED] Make copy of file and save it with a new name via cli"
date: 2008-10-12
forum: General Help
---

### Post by _sAm_ on 2008-10-12
I have a large collection with music, and have saved it like this:
Music folder:
  Folder1(with artist name)
   -Cdname1
   -Cdname 2
  Folder2(with artist name)
    -Cdname1
    -Cdname 2
And so on

In each cdfolder there is a picture called **cover.jpg**

Is it possible in cli to make a _copy_ of every «cover.jpg» and save it as **folder.jpg** in the same folder?

I just got an mp3player that can show coverart if it is named folder.jpg

Thanks for any help

---

### Post by Topsiho on 2008-10-12
It is easy: use the command cp (short for copy)

cp cover.jpg newname.jpg

To understand what you are doing read the man page for cp:

man cp

Topsiho

---

### Post by PsychedelicReaction on 2008-10-12
this is pretty the same thing i did yesterday with my mp3 collection :)

try this script

```
#!/bin/bash

for f in */*/cover.jpg ;do

$new="folder.jpg"
        echo cp -v "$f" "$new"
done
```

put it in your collection directory, give it the +x permission and run it. since i don't trust in my own coding capabilities, as it is it doesn't produce any effect. if the output of this script is something like
```
cp Artist1/Album1/cover.jpg Artist1/Album1/folder.jpg
```
remove echo and run it again.

---

### Post by PsychedelicReaction on 2008-10-13
ehm i forgot a couple of lines, so it should be


#!/bin/bash

for f in */*/cover.jpg ;do


base=`basename "$f"`
direx=`echo $f | sed 's/'$base'//g'`
$new="folder.jpg"
        echo cp -v "$f" "$direx""$new"
done

---

### Post by vanadium on 2008-10-13
You can also use find:

```

find . -name "cover.jpg" -execdir cp "{}" folder.jpg \;

```

---

### Post by _sAm_ on 2008-10-13
_Thank you all for your kind help!_

@Topsiho
The collection is to big to do this manually, it would take days with cp for each folder.

@PsychedelicReaction
I have never made any script before, so today I have spent some time reading about hit here; [http://www.linuxcommand.org/](http://www.linuxcommand.org/)
Very interesting, and I learned something new. That being said, I didn't get it to work, I guess I did something wrong. But now I know a little about alias and scripts, dosnt hurt:-)

@vanadium
As advertised – very nice indeed, now I can enjoy coverart on my player:-D I promise to never ever criticize the terminal in any way he he

---

