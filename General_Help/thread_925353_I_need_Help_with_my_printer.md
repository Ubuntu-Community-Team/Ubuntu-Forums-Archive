---
title: "I need Help with my printer"
date: 2008-09-20
forum: General Help
---

### Post by coolguy01 on 2008-09-20
I switched from Windows Vista to Ubuntu, and everything is working great except my Lexmark z645 printer.  I tried all the tutorials that I found while searching these forums, but none of them seem to work because I receive multiple errors every time I attempt to try one of them.  And for the record my printer does show up, but it will not print anything.  I really hope I can get this fixed in the next day or two because I have to print something for college, and I really don't want to have to switch back to Windows Vista.

---

### Post by Friek on 2008-09-20
It would be useful if you could post the error messages it is giving ;)

---

### Post by jcwmoore on 2008-09-20
what tutorials have you tried and what errors do you get?

---

### Post by coolguy01 on 2008-09-20
I followed this tutorial here, [http://ubuntuforums.org/showthread.php?t=616097](http://ubuntuforums.org/showthread.php?t=616097) and I got up to the extract the driver part, and then I got this error.

tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by phidia on 2008-09-20
Maybe try [this howto]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z645_Ubuntu_Install")?

The error you listed looks to be because the fliename typed doesn't match the actual filename.
The terminal (bash) has commandline completion so use that-that is only type part of the file name and press the tab key bash should autofill in the rest. Are you using uppercase where there should be lower?

---

### Post by jcwmoore on 2008-09-20
make sure you are in the correct directory, type 
```
ls
```
and make sure you can see the tar file.  you could also extract the file from the desktop by right clicking and selecting "extract here"

---

### Post by coolguy01 on 2008-09-20
I done as you said and right clicked and selected extract here, and now I get an error on the next step.  I typed cd lexmark, so I have to be in the right directory.

tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory

---

### Post by galvinate on 2008-09-22
> **coolguy01 said:**
> I done as you said and right clicked and selected extract here, and now I get an error on the next step.  I typed cd lexmark, so I have to be in the right directory.

tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory
Ok this is what you should type in the terminal to get to the Lexmark directory

cd Desktop/LEXMARK # that should get you  to the directory you need.

---

