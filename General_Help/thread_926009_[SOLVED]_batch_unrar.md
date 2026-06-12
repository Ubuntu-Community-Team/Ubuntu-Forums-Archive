---
title: "[SOLVED] batch unrar"
date: 2008-09-21
forum: General Help
---

### Post by MasterAslan on 2008-09-21
Hi,

A while back I wanted a script to batch unrar all rar files in sub folders into the folder they were already in.  I have managed to put a small script together and thought I would share it.  

```
#!/bin/bash
for i in $(find $(pwd) -name '*.rar')
do
cd $(dirname $i)
unrar e $i
done
```

I hope that may help others.  this assumes that if it is a multipart rar at least one file has the extension .rar

---

### Post by Disident on 2009-04-05
Thank you, Aslan, usefull script!
Only, maybe sometimes it will be better to use "x" instead of "e"!

To all those who don't know how to use this:
1. make a new document ($ vim unrar.sh)
2. copy Aslan's code into it (or change "e" with "x" if you want to keep folers)
3. save it and exit (:wq)
4. make script executable ($ chmod +x unrar.sh)
5. copy script in folder where are archives you want to extract ($ cp /full/path)
6. run script ($ ./unrar.sh)

---

### Post by neoroses on 2011-01-25
Nice one man, just wot i needed peace x

---

### Post by thedemon13666 on 2012-01-14
Double post, sorry

---

### Post by thedemon13666 on 2012-01-14
Sorry to Resurrect an old thread however I have a question about the above script.

The path to the files (pwd) contain white space, for instance /home/user/storage 4tb/blah.rar

I have tried playing about with the above bash script a bit however it  does not seem to like the white space, is there away to incorporate such  paths into the script?

EDIT

I have rectified the problem, it requires the use of change the delimiter in the foor loop using IFS, viz,

```

#!/bin/bash

#newpart
SAVEIFS=$IFS
IFS=$(echo -en "\n\b")

#old part
for i in $(find $(pwd) -name '*.rar')

do
cd $(dirname $i)
unrar e $i
done

#new part again
IFS=$SAVEIFS

```It now works even for file paths that have white space in them

---

