---
title: "Change multiple files names"
date: 2008-08-08
forum: General Help
---

### Post by change_mode on 2008-08-08
I want to remove a part of the file name for 100+ files at once. Is there a command to do this over the terminal?

Example:

picture001_vacation.png
...
picture100_vacation.png

Now I want 'vacation' to be removed from all these files.

---

### Post by damoxc on 2008-08-08
```

for picture in $(ls | grep picture*.png); do mv $picture $(echo $picture | sed 's/_vaction//g'); done;

```

If you just run that in the directory that will do the trick.

---

### Post by mikewhatever on 2008-08-08
Try purrr, <sudo apt-get install purrr>.
For guides, look here [http://mathrick.org/software/purrr.html](http://mathrick.org/software/purrr.html).

---

### Post by howlingmadhowie on 2008-08-08
i'd try mmv.

have a look here: [http://debaday.debian.net/2007/06/13/mmv-mass-moving-and-renaming-files/](http://debaday.debian.net/2007/06/13/mmv-mass-moving-and-renaming-files/)

the command you want is:

mmv "picture*_vacation.png" "picture#1.png"

---

### Post by sisco311 on 2008-08-08
```
rename -v 's/_vacation//' *
```

you can test the command first:
```
rename -n 's/_vacation//' *
```
-n shows what files would have been renamed

You can bulk rename files from the GUI with thunar file manager
or krename.

---

### Post by ghostdog74 on 2008-08-08
> **change_mode said:**
> I want to remove a part of the file name for 100+ files at once. Is there a command to do this over the terminal?

Example:

picture001_vacation.png
...
picture100_vacation.png

Now I want 'vacation' to be removed from all these files.


@OP, no need to download anything. also mmv/rename may not be available on some platforms. The usual way is simply write a script.
```

for pic in picture*.png
do
 newfile=${pic/_vacation/}
 mv $pic $newfile
done

```

---

### Post by ghostdog74 on 2008-08-08
> **damoxc said:**
> ```

for picture in $(ls | grep picture*.png); do mv $picture $(echo $picture | sed 's/_vaction//g'); done;

```

If you just run that in the directory that will do the trick.

useless use of ls and grep.

---

### Post by change_mode on 2008-08-08
> **sisco311 said:**
> ```
rename -v 's/_vacation//' *
```

you can test the command first:
```
rename -n 's/_vacation//' *
```
-n shows what files would have been renamed

You can bulk rename files from the GUI with thunar file manager
or krename.

Worked great, ty.

---

### Post by change_mode on 2008-08-14
I have one more problem. I want to remove a part of a file name that includes **[** and **]**. 
What code do I have to enter for those characters? I can't enter them directly, that gives me a syntax error.

---

### Post by GabrielWolff on 2008-08-18
I'd like to remove a lot of "the"s at the beginning of folder names, but ONLY at the beginning. For example:

- I'd like the folder "The Prodigy" to be renamed to "Prodigy"
- The folder: "In The Hourglass", though, should stay the same way
- And the folder: "The Prodigy - The Fat Of The Land" should become: "Prodigy - The Fat Of The Land"
- The folder Therion must stay that way, rather than becoming "rion"

Any chance?

---

### Post by mb_webguy on 2008-08-18
While it still helps to know something about regular expressions, the program gprename ("sudo apt-get install gprename") makes batch file renaming easy.  You can do matching and replacement without having to figure out the regular expression(s).

---

### Post by Loaded.len on 2008-08-18
Thunar (which is in the repos) has great support for batch file renaming, but you mentioned you need to do it in a terminal... I occasionally rename a bunch of files on my mythbox in an ssh -X session.
```
ssh -X hostname
``` then run 
```
thunar -B
```

Don't know if that helps you at all.

---

### Post by change_mode on 2008-08-31
And how do I use wildcards?

I want to remove [***]. *** is random text.

I got to:

```
rename -n 's/\[\]//' *
```

but what wildcard symbol do I have to use to delete the characters inbetween []?

________________

edit: \w is what I was looking for.

[http://www.go2linux.org/rename-bulk-files-with-linux-console-command](http://www.go2linux.org/rename-bulk-files-with-linux-console-command)

Very helpful.

---

### Post by efvalder on 2009-06-04
I have more than thousands of files with the character [COLOR=Red]:[/COLOR] in different folders, and when i try to put this files in a usbdisk, dont allow me do this, 
ex.:
cp: cannot create regular file `/media/Cruzer/PAPERS/CARBON/aC_DLC/2008_Effects of radio frequency powers on the characteristics of a-C:N p-Si photovoltaic solar cells prepared by plasma enhanced chemical vapor deposition.pdf': Invalid argument

so i need to change every single file with the character [COLOR=Red]:[/COLOR] to made the copy without problem
but i have too many files in different folders

Exist some scripts to look for in different folders?

---

### Post by leandromartinez98 on 2009-06-04
> **efvalder said:**
> I have more than thousands of files with the character [COLOR=Red]:[/COLOR] in different folders, and when i try to put this files in a usbdisk, dont allow me do this, 
ex.:
cp: cannot create regular file `/media/Cruzer/PAPERS/CARBON/aC_DLC/2008_Effects of radio frequency powers on the characteristics of a-C:N p-Si photovoltaic solar cells prepared by plasma enhanced chemical vapor deposition.pdf': Invalid argument

so i need to change every single file with the character [COLOR=Red]:[/COLOR] to made the copy without problem
but i have too many files in different folders

Exist some scripts to look for in different folders?


I'm not sure if the problem is the ":", because I've tested here and it does not seem to cause problems copying files. Anyway, you can do what
you want with:

```

#!/bin/bash

# This sets the separator between data as the "return" instead of space
IFS=$'\n'

# This finds all files containing the ":" in subdirectories of
# the current one and moves them to files with the same
# name but with a "-" instead of the ":"

for file in `find ./ -name "*:*"`; do
  mv $file ${file/:/-}
done

```

Always check with a test sample the script...

---

### Post by sisco311 on 2009-06-04
> **efvalder said:**
> I have more than thousands of files with the character [COLOR=Red]:[/COLOR] in different folders, and when i try to put this files in a usbdisk, dont allow me do this, 
ex.:
cp: cannot create regular file `/media/Cruzer/PAPERS/CARBON/aC_DLC/2008_Effects of radio frequency powers on the characteristics of a-C:N p-Si photovoltaic solar cells prepared by plasma enhanced chemical vapor deposition.pdf': Invalid argument

so i need to change every single file with the character [COLOR=Red]:[/COLOR] to made the copy without problem
but i have too many files in different folders

Exist some scripts to look for in different folders?

You can use the find command to search for the files recursively in a directory hierarchy:
```
find /media/Cruzer/PAPERS -type f -name "*:*"
```
then pipe the output and rename the files:
```
find /path/to/dir -type f -name "*:*" | \
while read file; do
  echo "\"${file}\" ---> \"${file//:/-}\""
# uncomment the next line to actually rename the files 
# mv -b "${file}" "${file//:/-}" 
done

```

---

### Post by Ultra Cronic on 2011-11-13
> **mikewhatever said:**
> Try purrr, <sudo apt-get install purrr>.
For guides, look here [http://mathrick.org/software/purrr.html](http://mathrick.org/software/purrr.html).


PURRR doesn't work in most cases, the problem is an arbitrary character in the middle of the file name in my case it's 00_00001.jpg through 350 pics.
Trying to remove the character "_" is impossible, the input end stops at the hard space and includes it in the output name throwing mencoder in a tizzy. I find it incredible week in the intelligence department.

---

### Post by oldos2er on 2011-11-14
Closed, necromancy.

---

