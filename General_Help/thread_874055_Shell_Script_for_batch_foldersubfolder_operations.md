---
title: "Shell Script for batch folder/subfolder operations"
date: 2008-07-29
forum: General Help
---

### Post by shouraku on 2008-07-29
Hi everyone,

I am rather new when it comes to shell scripts, and have come across a situation that I am not sure how to handle.

I have a folder that has a series of subfolders in it. Each subfolder has a series of files in it that need to be put into a single subfolder (within the subfolder). Each of the sub-subfolders needs to have the same name "spectra".

So basically, I want to turn:

/big_folder/subfolder/(lots of random files)

into

/big-folder/subfolder/spectra/(lots of random files)

and do this for all the 124 subfolders that lay within big_folder.

Note: the subfolders and files have unrelated names.

I know that there has to be a way to create a shell script or something to do this, i just don't know how to do it myself. Any help would be greatly appreciated!

---

### Post by DagMan on 2008-07-29
only do this if you backup big_folder and everything in it first as I don't have anything handy for this and maybe I'll screw something up, but it should go like this and you'lle need to substitute the path and name for big_folder, so if it's /home/me/folder then it would be cd /home/me/folder as the second thing after #!/bin/bash

```
#!/bin/bash

q=`pwd`

cd big_folder
for i in * ; do
if [ -d "$i" ] ; then
 cd $i
    mkdir spectra
    for x in * ; do
    if [ "$x" != "spectra" ] ; then
    mv "$x" spectra
    fi
    done
 cd ..
fi
done

cd "$q"

```

if all goes well that will give you big_folder/subdirectory/spectra/files
note however, that this will move all files and folders in the subdirectory to subdirectory/spectra.  if you only want files, but not folders then you need to add more and I think this would work (I hope):

```
#!/bin/bash

q=`pwd`

cd big_folder
for i in * ; do
if [ -d "$i" ] ; then
 cd $i
    mkdir spectra
    for x in * ; do
    if [ "$x" != "spectra" ] && [ -f "$x" ] ; then
    mv "$x" spectra
    fi
    done
 cd ..
fi
done

cd "$q"

```

Please backup that big folder beforehand.

---

### Post by shouraku on 2008-07-30
DagMan, you are my hero! You have no idea how much time you saved me. as a bonus, I know a bit more about shell scripting then when I started.

Really, thank you very much. You are a life saver!

---

