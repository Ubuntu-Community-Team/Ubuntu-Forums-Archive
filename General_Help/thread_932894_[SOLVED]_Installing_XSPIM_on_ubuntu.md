---
title: "[SOLVED] Installing XSPIM on ubuntu"
date: 2008-09-28
forum: General Help
---

### Post by ymf on 2008-09-28
Hi,
I recently tried to install xspim on my ubuntu machine, but i get the following error when i type in 'make'
```

flex -I -8 ../CPU/scanner.l
/bin/sh: flex: not found
make: *** [lex.yy.c] Error 127

```

I have installed bison as required, and is flex another parser that i should have?

Any help would be appreciated :)

---

### Post by ThrobbingBrain66 on 2008-09-28
```
sudo apt-get install flex
```

That should fix your problem. :)

---

### Post by ymf on 2008-09-28
Thanks a lot for that!

It was able to bypass the that error, but now i get this:

```

gcc -g    -I. -I../CPU     -Dlinux -D__amd64__ -D_POSIX_C_SOURCE=199309L 				-D_POSIX_SOURCE -D_XOPEN_SOURCE 				-D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 				  				  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER="\"/usr/local/lib/exceptions.s\"" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o xspim.o xspim.c
xspim.c:31:27: error: X11/Intrinsic.h: No such file or directory
xspim.c:32:28: error: X11/StringDefs.h: No such file or directory
xspim.c:33:23: error: X11/Shell.h: No such file or directory
xspim.c:34:22: error: X11/Xlib.h: No such file or directory
xspim.c:35:31: error: X11/Xaw/Cardinals.h: No such file or directory
xspim.c:36:27: error: X11/Xaw/Paned.h: No such file or directory
xspim.c:37:31: error: X11/Xaw/AsciiText.h: No such file or directory
xspim.c:38:26: error: X11/Xaw/Text.h: No such file or directory
xspim.c:39:28: error: X11/Xaw/Dialog.h: No such file or directory
xspim.c:40:24: error: X11/keysym.h: No such file or directory
....
...
....
xspim.c:972: error: expected ‘)’ before ‘w’
make: *** [xspim.o] Error 1

```

Can I please ask what else I'm missing ?

Thanks in advance!

---

### Post by ThrobbingBrain66 on 2008-09-29
I don't have tons of compiling experience, but it's complaining about X11 stuff.  You may need to install libx11-dev from the repos as well.

EDIT:  After Googling your errors, it seems you need the following two packages (but maybe not libx11-dev): libxt-dev libxaw-headers

---

### Post by ymf on 2008-10-01
Thank you very much ! I realised I had to install some packages, which includes the ones you mentioned. That should do the trick :)

---

### Post by pondator on 2008-11-10
hello!
I did make xspim, too. I didn't make install it because it wants to create /usr/unsup/bin (although I changed the entries in makefile.std).

My problem is I can start xspim an then get a window with 3 insertion fields and one field that contains 12 rectangels. I can't write or insert anything :(


Any ideas?


thx
pondi

---

