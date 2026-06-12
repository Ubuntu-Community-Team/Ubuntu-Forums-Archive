---
title: "terminal question"
date: 2008-09-18
forum: General Help
---

### Post by gishaust on 2008-09-18
what does it mean when a folder in the terminal has a green high-light surrounding it.

---

### Post by mb_webguy on 2008-09-18
Weeellll...  Since terminals can have different color schemes, it's a bit hard to say.  Can you post the output of "ls -lsh" where one of the folders is green (and indicate which one we're supposed to be looking at)?

EDIT:  My first guess would be that it's actually a symbolic link to a folder, rather than an actual folder.

---

### Post by jp73107 on 2008-09-18
I think i understand what the OP is saying, i've seen the same thing, but i'm not sure about it either.. i usually just ignore it and go on about my business. 

In gnome-terminal, on a default installation of ubuntu, when doing ls to list folders, some folders are highlighted in green, with black text, i.e. a green box with the folder name written in black text. I'd also like to know this answer :)

---

### Post by gishaust on 2008-09-18
that is exactly what i am talking about it never did until I setup my ftp server

---

### Post by mb_webguy on 2008-09-18
From "man dir_colors":```
       ls uses the following defaults:

         NORMAL   0       Normal (non-filename) text
         FILE     0       Regular file
         DIR      32      Directory
         LINK     36      Symbolic link
         ORPHAN   undefined       Orphaned symbolic link
         MISSING  undefined       Missing file
         FIFO     31      Named pipe (FIFO)
         SOCK     33      Socket
         BLK      44;37   Block device
         CHR      44;37   Character device
         EXEC     35      Executable file


```

However, as I said, colors are customizable.  The colors in my terminal won't match yours, so I can't really say which of the above is normally indicated by green highlighting.  

If you use the -F option for ls, it will append a character to the filename to indicate what type of file it is:```
Character  File type
nothing    regular file
/          directory
*          executable file
@          link
=          socket
|          named pipe
```

---

### Post by gishaust on 2008-09-18
where in the os could I find what mine are I know that blue is dir but this green I have never seen. There must be a place where it sets this out if it customizable.

---

### Post by mb_webguy on 2008-09-18
Well, it depends on your settings in your terminal application profile.  But that just shows a color palette, no labels as to what they're for.

As I implied in my previous post, the best way might be to use "ls -lsF", and see what symbol corresponds with green highlighting.

---

### Post by zenosdog on 2008-09-19
If that folder is set to 777 permissions, it will have the green highlight.  That's how it is for me, anyway.  I also believe it only happens after you set up ssh-server.  I think it's just a warning to let you know that the folder is question is world-readable, and world-writable.

---

