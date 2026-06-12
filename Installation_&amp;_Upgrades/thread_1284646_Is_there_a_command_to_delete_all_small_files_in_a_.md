---
title: "Is there a command to delete all small files in a specified folder?"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by afeasfaerw23231233 on 2009-10-06
For example, there is a folder call "data" in my home directory. If I want to delete all the files that are smaller than 20KB in that "data" folder (including sub-folders), which parameter of mv command should I run?

---

### Post by terazen on 2009-10-06
```
rm `find /home/some/folder/ -size -20k -type f`
```

You may want to run the find command first just to see what you're looking at deleting before you actually do it. ```
ls -lah `find /home/some/folder/ -size -20k -type f`
```

The -name option of find is good too if you want to delete certain files like *.jpg or something.

---

### Post by afeasfaerw23231233 on 2009-10-06
Thanks for the help. But it doesn't work with file name with spacing. 
For example, there's is a file named "text file" in the folder "data" and is smaller than 20K, 

```
ls -lah `find data -size -20k -type f`
ls: cannot access data/text: No such file or directory
ls: cannot access file: No such file or directory

```
```
rm  `find data -size -20k -type f`
rm: cannot remove `data/text': No such file or directory
rm: cannot remove `file': No such file or directory
```

---

### Post by lloyd_b on 2009-10-07
```
find /home/some/folder/ -size -20k -type f | while read FILENAME; do rm "$FILENAME"; done
``` should do the trick.  You can replace the "rm" with a "ls" to see what's happening (but be sure to leave the "$FILENAME" in quotation marks!).

Lloyd B.

---

### Post by afeasfaerw23231233 on 2009-10-07
Thanks. It works but not on the filename with Simplified Chinese characters. 
May I ask what is **-type f** for? This [site]("http://linux.about.com/od/commands/l/blcmdl1_find.htm") said it stands for regular file? How can I delete the files with Simplified Chinese characters?

**EDIT:** Oh, sorry. It seems to be my mistake. The files with Simplified Chinese characters are now gone. Thanks for help!

---

