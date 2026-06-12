---
title: "Error in kghostview related to x11 device"
date: 2008-08-15
forum: General Help
---

### Post by JimIvey on 2008-08-15
With Hardy Heron, I can't see postscript files in kghostview (or in konqueror with the filemanager profile).

I get the following error:
```
Unknown device: x11
Unrecoverable error: undefined in .uninstallpagedevice
Operand stack:
    defaultdevice
```

I've poked around the 'net for answers and found this:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462678](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462678)

However, other kubuntu hardy heron installations I have don't have this problem.  

Not sure where to look for answers beyond what I've already found.  Any clues?

Many thanks in advance.

---

### Post by pakrak on 2008-09-27
I had the same error. I followed the link you had, and the clue there was that ghostscript-x was needed. It hadn´t been installed on my (very minimal) system:
   sudo aptitude install ghostscript-x
fixed it for me.

---

