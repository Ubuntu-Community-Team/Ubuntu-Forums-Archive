---
title: "Using fdupes to backup before a drive format"
date: 2008-10-12
forum: General Help
---

### Post by Brime on 2008-10-12
I am a little lost and if anyone can help that would be great.:)

Ok I want to backup a single copy of all duplicate pictures on my computer.
The problem is i have had many installs and reinstalls with bad backup polices. so some of the images have up to 27 copies. I also want to either preserve the dir structure or rename the files so theres no over rights. The camera I was using at the time made this necessary because it restarted the file numbering after every battery change. So I have multiple different files with there copies under the same name (eg 001.jpg can be 2 pictures of a cat and 3 of my house). 

I at first was using find with xargs, md5, uniq, and sed.
I cant remember the command I was using at the time and have sence lost it. So I started googleing it and heard about fdupes. So heres what I've been trying with no results.

First this is how I get a list

```
fdupes /media/disk/ /media/Storage/ -rn >/home/brime/dupes.txt
fdupes /media/disk/ /media/Storage/ -rfn >/home/brime/dupes.omit.txt
diff /home/brime/dupes.txt /home/brime/dupes.omit.txt >diff.txt

```
Now I have a list of only one copy of all the duplicate files.

then i clear out the junk from diff

```
awk '{if ($2 != ".") print$2,$3,$4,$5,$6,$7,$8,$9,$10,$12,$13,$14 }' ./diff.txt >list.txt 
```
(I am aware that this is ugly but i dont know anyother way)

next i clear the wight space after every line (I think :-? )

```
cat ./list.txt | sed 's/^[ \t]*//;s/[ \t]*$//' >list2.txt
```

So after that i thought that running this would work.

```
#!/bin/bash  
    
 filelist='/home/brime/list2.txt'  
 copylocation='/home/brime/backup'  
 for files in `cat $filelist`;  
 do cp -v $files $copylocation$files;  
 done  
```

but all i get is a bunch of "cp: cannot stat" errors.

so I tried fixing the spaces in the list.

```
sed 's/ /\\ /g' ./list2.txt >list.fix.txt

```
but running again gives the same err....

As all of the code I'm using was found in other posts that are similar to what I'm trying to do and I don't completely understand it yet I dont even know if I'm barking up the wrong tree here. :confused:

Thanks is advance.

---

