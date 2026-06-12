---
title: "Please Help - libtool: unrecognized option `-o'"
date: 2008-07-19
forum: General Help
---

### Post by Blam! on 2008-07-19
I am trying to run "make" for gtk+ 2.12.11 and when it finishes I get this error:

```
/bin/bash ../libtool --mode=link      -o autotestkeywords    
libtool: unrecognized option `-o'
Try `libtool --help' for more information.
make[2]: *** [autotestkeywords] Error 1
make[2]: Leaving directory `/home/will/Desktop/GTK+/gtk+-2.12.11/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/will/Desktop/GTK+/gtk+-2.12.11'
make: *** [all] Error 2

```

I have tried searching Google and this forum but have come up with nothing, libtool is already the latest version.

---

### Post by Blam! on 2008-07-20
bump from page 4

---

### Post by unutbu on 2008-07-20
I've downloaded gtk+-2.12.11 and typed
```

./configure
make
```
No problems on Gutsy.

The only non-default things I've installed (I think) is
```

build-essential
libtiff4-dev
```

I've also linked /bin/sh to /bin/bash:```

sudo ln -sf /bin/bash /bin/sh
```

The closest line I could find to the one you posted was
```

/bin/sh ../libtool --mode=link c++  -g -O2   -o autotestkeywords  autotestkeywords-autotestkeywords.o  
```
So it looks like the "c++ -g -O2" part got left out.
I have no idea why. Do you have c++ installed?

If 
```
which c++
```
does not return anything, then type
```

sudo apt-get install build-essential
```

---

