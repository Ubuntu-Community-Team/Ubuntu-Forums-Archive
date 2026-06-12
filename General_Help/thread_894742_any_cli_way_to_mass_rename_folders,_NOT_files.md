---
title: "any cli way to mass rename folders, NOT files?"
date: 2008-08-19
forum: General Help
---

### Post by moore.bryan on 2008-08-19
subject line says it all...

---

### Post by septekin on 2008-08-19
You may have a look at the man pages for rename.

---

### Post by jeffk on 2008-08-19
If you have a formula for the renaming, then either learn a bit of bash or python and loop over your folders in a script. The command "find -type d" will return directories only, and python has functions to determine the same, just as a starting point.

If you have less defined renaming needs, you can do a lot with emacs and dired, find-dired, wdired modes. Used properly, you get an editable text buffer of the files or folders you want, and can use regular expressions to match patterns.

Tip: Make a backup before you attempt any of this. Make several :)

---

### Post by moore.bryan on 2008-08-19
> **septekin said:**
> You may have a look at the man pages for rename.
yeah, that was my first step... alas, rename only works with files. thanks, though.
> **jeffk said:**
> If you have a formula for the renaming, then either learn a bit of bash or python and loop over your folders in a script. The command "find -type d" will return directories only, and python has functions to determine the same, just as a starting point.
i guess my formula would be simply replacing spaces with underscores... the man page for find was not very helpful, although i read it suggested on other threads.
> If you have less defined renaming needs, you can do a lot with emacs and dired, find-dired, wdired modes. Used properly, you get an editable text buffer of the files or folders you want, and can use regular expressions to match patterns.

Tip: Make a backup before you attempt any of this. Make several :)
good tip, but i've always found emacs an unnecessary PITA; no offense to all of the wonderful people who use emacs!
;-)

---

### Post by septekin on 2008-08-19
Do I understand that you wish to change spaces in the names of several folders with underscores?

I've just tried:
   rename 's/\ /_/' *

and it changed the folder names from "ABCD X" to "ABCD_X".

---

### Post by sisco311 on 2008-08-19
```
find **path/to/folders** -maxdepth 1 -type d | rename 's/ /_/'
```

To rename the folders recursively, remove the -maxdepth flag:
```
find **path/to/folders** -type d | rename 's/ /_/'
```

---

### Post by ajgreeny on 2008-08-19
> **septekin said:**
> Do I understand that you wish to change spaces in the names of several folders with underscores?

I've just tried:
   rename 's/\ /_/' *

and it changed the folder names from "ABCD X" to "ABCD_X".
If you have more than one space in the folder or file name how can you remove all spaces, short of re-running the command, which I know works OK, having just tried it.  This could be useful as when song titles are ripped from CDs they often have lots of spaces in them which I try to remove manually.  This would be a great trick to do it quickly.

---

### Post by indiv on 2008-08-19
To change all space to underscores, put a 'g' on the end:

rename 's/\ /_/g' *

---

### Post by ajgreeny on 2008-08-19
WOW, Thanks for that.  So simple and quick and just the ticket!

---

### Post by sisco311 on 2008-08-19
*rename* examples: [http://ubuntuforums.org/showpost.php?p=5210607&postcount=2](http://ubuntuforums.org/showpost.php?p=5210607&postcount=2)

---

### Post by ghostdog74 on 2008-08-19
rename is not available everywhere. If you don't have it, simple bash or using standard tools 
```

find . -maxdepth 1 -type d | while read line ; 
do  
  new=`echo $line|sed 's/ //g'`
  mv "$line"  "$new"
done                                 

```

---

### Post by moore.bryan on 2008-08-21
> **indiv said:**
> To change all space to underscores, put a 'g' on the end:

rename 's/\ /_/g' *
could you explain what rename is doing here?
thanks!

---

### Post by unutbu on 2008-08-21
's/\ /_/g'  a perl substitution.   

s means substitute.
The stuff between the forward slashes, /, are perl regexp patterns.
The first pattern, '\ ', means "find a space in the filename". A backslash is sometimes needed protect special characters. When put in front of a special character, it means "I literally mean a..." In this case it is superfluous. "rename 's/ /_/g' *"
works just as well.

The second pattern, '_', is just a literal underscore.

The 'g' at the end means 'match globally' -- so if a filename has more than one space, each space is changed into an underscore in turn.

For more info on perl regexp's, type
```

perldoc perlretut
perldoc perlreref
perldoc perlre
```

---

### Post by moore.bryan on 2008-08-21
excellent; thanks. now i'm trying to play around with what the command would look like to replace the parenthesis...
;-)

---

