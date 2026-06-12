---
title: "Delete characters from many file names at once"
date: 2008-09-14
forum: General Help
---

### Post by Astronomerob on 2008-09-14
Hello again everyone,

I was wondering if there is a way to remove the first few characters from every file in a folder.

I created several hundred files with a numbering system that has messed up the order that they show up in. Each file is part of a series and there are many files within that series, for example a file may be named:

01 series 01 file 01
01 series 02 file 01
02 series 01 file 02

Hopefully you can see my problem here. It's that first set of numbers that is screwing up the order they show up in. So, again, is there any way to delete those first numbers from all the hundreds of files without manually renaming all of them?

Thanks.

---

### Post by aloshbennett on 2008-09-14
This is what I understand as your problem. You have some files with names like
> 01 series 01 file 01
01 series 02 file 01
02 series 01 file 02

that you want to rename to
> series 01 file 01
series 02 file 01
series 01 file 02


If thats the case, this script would help. Here, I am renaming all files starting with numerals by stripping off the leading digits and any space that might follow.
> 
#!/bin/bash

for i in * ;
do
  echo "$i" | grep '^[0-9]\+' >> /dev/null;
  if [ "$?" -eq 0 ]
    then
      echo "found: $i"
      new=`echo "$i" | sed 's/^[0-9]\+ *//'`
      echo "renaming to $new"
      mv "$i" "$new"
    fi
done;


The for statement lists all files under the directory.
You are then looking for any file that starts with digits
> '^[0-9]\+'
The new variable contains the name after stripping off the leading digits and subsequent spaces
> sed 's/^[0-9]\+ *//'

Play around with it and modify it to suite your need.

---

### Post by Astronomerob on 2008-09-14
Yep, that's what I wanted to do (sorry I didn't clarify that earlier).

I'll give it a go ASAP and get back to you.

Also, what should I do if there are letters at the beginning as well? (Should this come up in the future for me)

Thanks!

---

### Post by Astronomerob on 2008-09-14
Ah, running into a problem. Should have caught this earlier.

Some names are like this:

SD01 - series 01 file 01

And the others are like this:

01 - series 01 file 01

The " - " is causing problems in the renaming. But otherwise it would seem to be working, so that's a step in the right direction!

Thanks again.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi Astronomerob,

You could also try (on a backup) :

rename 's/^.*(series\s+\d+\s+file\s+\d+.*)$/$1/' *

---

### Post by aloshbennett on 2008-09-14
So lets refine it a bit by renaming ALL files which doesnt start with 'series' by clipping off everything preceding series.
Our matching condition would be
> grep -v '^series'
instead of 
> grep '^[0-9]\+'
(Matching everything that doesnt start with series)

And the new name would be 
> sed 's/.*series/series/'
Instead of > sed 's/^[0-9]\+ *//'
(Replacing everything before series + series, with just series)

---

### Post by Astronomerob on 2008-09-14
Excellent! That last one worked.

Thank you very much for your help. You saved me SO much time!

---

### Post by ghostdog74 on 2008-09-16
> **Astronomerob said:**
> is there any way to delete those first numbers from all the hundreds of files without manually renaming all of them?

you can use the script [here.](http://www.linuxquestions.org/linux/blog/ghostdog74/2008-09-13/Mass_File_Renamer_By_Pattern_Substitution)
eg usage
```

# ./script.sh -s "^[0-9][0-9] " -e "" -d #display files to be renamed.
# ./script.sh -s "^[0-9][0-9] " -e "" # remove -d to do actual rename

```

---

