---
title: "Only allow &quot; a-zA-Z0-9()- &quot; in filenames with autoconvert. How?"
date: 2008-08-13
forum: General Help
---

### Post by dinca on 2008-08-13
Hi!

I would like to convert all my files in a certain directory so the filenames only include " a-zA-Z0-9()- ". How can I do this? Or is it impossible?

The best would be if someone(over smb or nfs) tries to name a file "it's.file" it will automatically be named "its.file"

And maybe only allow a certain amount of characters. So any file with more than the allowed amount would be cut off. So that "123456789.file" would be named "123456.file". 

As a side question: what is the safe amount of characters in a filename on a ext3 system? 255? And is there any other I should think of if im running a raid 5 or 10 system?


Thanks!

---

### Post by cariboo on 2008-08-13
Have a look at GPRename, It is available in the repositories.

JIm

---

### Post by dinca on 2008-08-14
> **cariboo907 said:**
> Have a look at GPRename, It is available in the repositories.

JIm

Will do!

But I am also interested in configuring my system so that it will make the changes on the fly. Especially since im running ubuntu server with no graphical interface.

---

### Post by decoherence on 2008-08-14
here's a script. in its current form it must be run from within the directory your files are. as far as triggering it, i would imagine the simplest thing to do would be to schedule it to run frequently with cron. i'm sure there is a way to trigger the script whenever something new is added to the folder but it escapes me at the moment

```
#!/bin/bash
IFS=$'\n'
fileList=`ls -1`
for file in $fileList
                do renamedFile=`echo $file | sed 's/[^[:alnum:]]//g'`
                if [ $file != $renamedFile ]; then {
                        mv "$file" $renamedFile
                        }
                fi
                done
IFS=$' \t\n'

```

Not sure if that last line is absolutely necessary, but better safe than sorry. Also, you may want to replace the "mv" with a "cp" until you're sure it behaves as expected.

---

