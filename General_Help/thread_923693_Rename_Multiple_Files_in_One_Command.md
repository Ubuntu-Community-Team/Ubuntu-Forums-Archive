---
title: "Rename Multiple Files in One Command"
date: 2008-09-18
forum: General Help
---

### Post by CarlosinFL on 2008-09-18
I have several files that have .JPG extension and I want to chane all of them to .jpg (lower case) and would think I could do this with the "mv" command but can't seem to find out how.

```
carlos@mako:~/Desktop$ ls -l
total 15100
-rwx------ 1 carlos users 1387010 2008-09-13 21:51 IMG_0430.JPG
-rwx------ 1 carlos users 1451744 2008-09-13 21:51 IMG_0431.JPG
-rwx------ 1 carlos users 1342028 2008-09-13 21:52 IMG_0433.JPG
-rwx------ 1 carlos users 1985966 2008-09-13 22:14 IMG_0434.JPG
-rwx------ 1 carlos users 1898912 2008-09-13 22:14 IMG_0435.JPG
-rwx------ 1 carlos users 1666252 2008-09-13 23:48 IMG_0439.JPG
-rwx------ 1 carlos users 1686149 2008-09-14 00:25 IMG_0444.JPG
-rwx------ 1 carlos users 1892719 2008-09-14 00:41 IMG_0446.JPG
-rwx------ 1 carlos users 2054236 2008-09-14 00:41 IMG_0447.JPG

```

Why is this not working?

```
carlos@mako:~/Desktop$ mv *JPG *jpg
mv: target `*jpg' is not a directory

```

---

### Post by mb_webguy on 2008-09-18
I don't think you can use wildcards (*) in the target field of the mv command.  You can use the -exec option of the find command to mv each file, but I'm not sure about the syntax.

Personally, I'd just use GPRename ("sudo apt-get install gprename").  It's a batch file renaming utility that's pretty versatile and easy to use.  While there is power in using the command line, I don't see much point of figuring out the right command for something when there's a GUI app that can get the job done just as well.

EDIT:  You can also use the rename command.  "rename 's/JPG/jpg/' *.JPG" should work.  I'd still rather use GPRename.  By the time I'd looked up the syntax of the rename command, I could have already renamed the files with GPRename, and this was a fairly straightforward example.  I can put together a regular expression if I have to, but I'd rather not if given the choice.

---

### Post by bodhi.zazen on 2008-09-18
use find ... 

[http://www.codecoffee.com/tipsforlinux/articles/21.html](http://www.codecoffee.com/tipsforlinux/articles/21.html)

find the files and use exec to mv them.

---

### Post by Bakon Jarser on 2008-09-18
I like pyRenamer for that sort of thing.

---

### Post by sisco311 on 2008-09-18
> **Carlwill said:**
> I have several files that have .JPG extension and I want to chane all of them to .jpg (lower case) and would think I could do this with the "mv" command but can't seem to find out how.

```
carlos@mako:~/Desktop$ ls -l
total 15100
-rwx------ 1 carlos users 1387010 2008-09-13 21:51 IMG_0430.JPG
-rwx------ 1 carlos users 1451744 2008-09-13 21:51 IMG_0431.JPG
-rwx------ 1 carlos users 1342028 2008-09-13 21:52 IMG_0433.JPG
-rwx------ 1 carlos users 1985966 2008-09-13 22:14 IMG_0434.JPG
-rwx------ 1 carlos users 1898912 2008-09-13 22:14 IMG_0435.JPG
-rwx------ 1 carlos users 1666252 2008-09-13 23:48 IMG_0439.JPG
-rwx------ 1 carlos users 1686149 2008-09-14 00:25 IMG_0444.JPG
-rwx------ 1 carlos users 1892719 2008-09-14 00:41 IMG_0446.JPG
-rwx------ 1 carlos users 2054236 2008-09-14 00:41 IMG_0447.JPG

```Why is this not working?

```
carlos@mako:~/Desktop$ mv *JPG *jpg
mv: target `*jpg' is not a directory

```
[FONT=monospace]
```
[/FONT]cd /path/to/folder/
rename -v 's/\.JPG$/\.jpg/' *.JPG
```

---

### Post by ghostdog74 on 2008-09-18
> **Carlwill said:**
> I have several files that have .JPG extension and I want to chane all of them to .jpg (lower case) and would think I could do this with the "mv" command but can't seem to find out how.

```
carlos@mako:~/Desktop$ ls -l
total 15100
-rwx------ 1 carlos users 1387010 2008-09-13 21:51 IMG_0430.JPG
-rwx------ 1 carlos users 1451744 2008-09-13 21:51 IMG_0431.JPG
-rwx------ 1 carlos users 1342028 2008-09-13 21:52 IMG_0433.JPG
-rwx------ 1 carlos users 1985966 2008-09-13 22:14 IMG_0434.JPG
-rwx------ 1 carlos users 1898912 2008-09-13 22:14 IMG_0435.JPG
-rwx------ 1 carlos users 1666252 2008-09-13 23:48 IMG_0439.JPG
-rwx------ 1 carlos users 1686149 2008-09-14 00:25 IMG_0444.JPG
-rwx------ 1 carlos users 1892719 2008-09-14 00:41 IMG_0446.JPG
-rwx------ 1 carlos users 2054236 2008-09-14 00:41 IMG_0447.JPG

```

Why is this not working?

```
carlos@mako:~/Desktop$ mv *JPG *jpg
mv: target `*jpg' is not a directory

```

you can use the script [here](http://www.linuxquestions.org/linux/blog/ghostdog74).
eg usage
```

./filerenamer.py -p ".*" -e "a-z" -l "IMG*.JPG" #use -l to list files to be changed 
./filerenamer.py -p ".*" -e "a-z"  "IMG*.JPG" #remove -l to commit

```

or if you want to learn how to do it
```

for files in IMG*
  do  newname=`echo $files | tr 'A-Z' 'a-z'`
  mv "$files" "$newname"
done

```

---

### Post by 73ckn797 on 2008-09-18
I have to rename several hundred photo files weekly and found "Thunar" to work quite well with the built-in renamer. It makes for an all-in-one app. I believe that the GPrename mentioned will work within the Nautilus file manager as well.

---

