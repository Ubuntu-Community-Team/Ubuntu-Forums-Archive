---
title: "[SOLVED] extract multiple .7z files"
date: 2008-08-12
forum: General Help
---

### Post by brohmes on 2008-08-12
Hi,

I have about 300 .7z files all in one directory.  Each file contains 1 .avi file.  I want to extract the avi's, keeping them in this same directory.

Is it possible from the command line in Ubuntu to extract all these files in one go?

I have installed p7zip-full, but I can't figure out the syntax.

Thanks

Ryan

---

### Post by mb_webguy on 2008-08-12
Have you tried something like:

*7z x ./**

---

### Post by brohmes on 2008-08-12
Thanks for the response.

Tried:

7z x ./*

which produces:

"Error:
Cannot use absolute pathnames for this command"


Tried

7z x * 

which produces:

No files to process



Though if I specify a file, such as in:

7z x "Yoshi.7z" 

it will extract.

I must be missing something?

Thanks again

---

### Post by sea_monkey987 on 2008-08-12
change directory into the one with your .7z files.  Then run this command:
```

find . -name "*.7z" -type f| xargs -I {} 7z x {}

```

---

### Post by brohmes on 2008-08-12
Thanks for the response sea monkey.

That extracted one file out of the list.  Not the first, not the last, but one from in the middle?

i then modified the command to be:

find . -name *.7z -type f| xargs -I {} 7z x {}

(removed quotes on *.7z)  and it now extracts the 1st, 3rd, 4th, 5th and 6th files in the directory (as sorted by name)??


thanks for the help

---

### Post by sea_monkey987 on 2008-08-12
I'll have to see.  Try to extract the 2nd file (or which ever one that didn't extract) by its specific name.  It might be corrupt.

---

### Post by brohmes on 2008-08-12
I got it.

Tried what you said, didn't work without quotes, as there were spaces in filenames.  So I then tried:

7z x "*.7z" 

which did it for me.


Thanks sea_monkey, you got me on the right track!

---

### Post by sea_monkey987 on 2008-08-12
Out of curiousity, why did you compress .avi files individually?  It shouldn't have resulted in much, if any, smaller files.

---

### Post by brohmes on 2008-08-13
It was a set of nintendo ROMS, along with a set of avi's showing gameplay.  For use with an emulator frontend.

I'm not entirely sure why they were zipped, but that's how i got them. :)

---

