---
title: "[SOLVED] Simple bash script to update when file is larger"
date: 2008-08-24
forum: General Help
---

### Post by brent113 on 2008-08-24
Hi again all,

I wrote a program a long time ago for Windows that would take a folder and compare it's contents to another, similar to a cp -u, but instead of checking timestamps it checked filesize and kept the larger.  It also deleted permanently the smaller of the two files.  I know there has got to be an easy way to script this, but I'm having trouble figuring this out.

So here's what this needs to do:
- Enumerate the current directory's contents (should not be recursive into subdirectories).
- Take an argument for the destination folder to compare against.
- For each file in the current directory:
- - If it does not exist in the destination, move it
- - If it does exist in the destination, overwrite the destination file if it is larger, otherwise delete the original.

I was hoping there was an option for cp to do this, but a bash script would work equally well.  Thanks in advance!

--
Brent Scrivner

---

### Post by aloshbennett on 2008-08-24
or you could look into rsynch which is the linux favourite.

---

### Post by brent113 on 2008-08-24
I have, as far as I can tell it doesn't do filesize

---

### Post by ghostdog74 on 2008-08-24
> **brent113 said:**
> 
So here's what this needs to do:
- Enumerate the current directory's contents (should not be recursive into subdirectories).

you can use ```
ls -l *
```, or ```
 for files in * 
```

> 
- Take an argument for the destination folder to compare against.

use read to take an argument. eg ```
 read choice 
```

> 
- For each file in the current directory:
- - If it does not exist in the destination, move it

to check for file exist, use ```
test -e file
``` , or if/else 

> 
- - If it does exist in the destination, overwrite the destination file if it is larger, otherwise delete the original.

to check for size, you can use comparison. eg ```
 if [ $size -gt 10000 ];then .... 
```
please see my sig for link to bash scripting.

To get you started
```

printf "Enter destination directory: "
read destdir
destdir="/destination"
IFS=":"
currentdir="/source"
find $currentdir -maxdepth 1 -type f -printf "%f:%s\n"  | while read FILENAME SIZE
do
   if [ ! -f ${destdir}/$FILENAME ];then
     echo mv "$FILENAME" ${destdir} #remove the echo to use
   else
     destsize=$(stat -c "%s" ${destdir}/${FILENAME})
     if [ $SIZE -gt $destsize ];then
        echo "$SIZE greater than destination"
        # i leave to you to do the rest. Read the manual
     fi 
   
   fi 
    
done
unset IFS

```

---

