---
title: "VentriloCrtl 0.4 doesn't work (Compilation problem)"
date: 2008-08-05
forum: General Help
---

### Post by tespio on 2008-08-05
I'm trying to compile ventriloctrl-0.4 and it seems like it doesn't want to work
(in the terminal)when i go to the ventriloctrl's folder and make the file 
```
make
```
I get this big error I don't know what's going on...
```

boris@boris-desktop:~/Documents/ventriloctrl-0.4$ make
gcc -Wall -O3 -o ventriloctrl ventriloctrl.c -lX11 -lXevie
ventriloctrl.c:14:22: error: X11/Xlib.h: No such file or directory
ventriloctrl.c:15:24: error: X11/keysym.h: No such file or directory
ventriloctrl.c:16:34: error: X11/extensions/Xevie.h: No such file or directory
ventriloctrl.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘createKeyEvent’
ventriloctrl.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ventriloctrl.c: In function ‘main’:
ventriloctrl.c:96: error: ‘Display’ undeclared (first use in this function)
ventriloctrl.c:96: error: (Each undeclared identifier is reported only once
ventriloctrl.c:96: error: for each function it appears in.)
ventriloctrl.c:96: error: ‘display’ undeclared (first use in this function)
ventriloctrl.c:97: error: ‘Window’ undeclared (first use in this function)
ventriloctrl.c:97: error: expected ‘;’ before ‘winRoot’
ventriloctrl.c:98: error: ‘winFocus’ undeclared (first use in this function)
ventriloctrl.c:113: error: ‘XEvent’ undeclared (first use in this function)
ventriloctrl.c:113: error: expected ‘;’ before ‘xev’
ventriloctrl.c:114: error: ‘XKeyEvent’ undeclared (first use in this function)
ventriloctrl.c:114: error: expected ‘;’ before ‘event’
ventriloctrl.c:116: warning: implicit declaration of function ‘XOpenDisplay’
ventriloctrl.c:122: warning: implicit declaration of function ‘XevieStart’
ventriloctrl.c:127: warning: implicit declaration of function ‘XevieSelectInput’
ventriloctrl.c:127: error: ‘KeyPressMask’ undeclared (first use in this function)
ventriloctrl.c:127: error: ‘KeyReleaseMask’ undeclared (first use in this function)
ventriloctrl.c:131: error: ‘winRoot’ undeclared (first use in this function)
ventriloctrl.c:131: warning: implicit declaration of function ‘XDefaultRootWindow’
ventriloctrl.c:132: warning: implicit declaration of function ‘find_window’
ventriloctrl.c:146: warning: implicit declaration of function ‘XNextEvent’
ventriloctrl.c:146: error: ‘xev’ undeclared (first use in this function)
ventriloctrl.c:150: warning: implicit declaration of function ‘XLookupKeysym’
ventriloctrl.c:158: error: ‘KeyPress’ undeclared (first use in this function)
ventriloctrl.c:160: error: ‘event’ undeclared (first use in this function)
ventriloctrl.c:160: warning: implicit declaration of function ‘createKeyEvent’
ventriloctrl.c:161: warning: implicit declaration of function ‘XSendEvent’
ventriloctrl.c:161: error: ‘True’ undeclared (first use in this function)
ventriloctrl.c:161: error: expected expression before ‘)’ token
ventriloctrl.c:162: warning: implicit declaration of function ‘XFlush’
ventriloctrl.c:165: error: ‘KeyRelease’ undeclared (first use in this function)
ventriloctrl.c:180: error: expected expression before ‘)’ token
ventriloctrl.c:186: warning: implicit declaration of function ‘XevieSendEvent’
ventriloctrl.c:186: error: ‘XEVIE_UNMODIFIED’ undeclared (first use in this function)
make: *** [all] Error 1


```

When I run the runctrl.sh I get this error:
```

boris@boris-desktop:~/Documents/ventriloctrl-0.4$ ./runctrl.sh
./ventriloctrl: 6: Syntax error: word unexpected (expecting ")")

```

---

### Post by quantum-positron on 2008-08-07
I am having the same problem anyone have a solution

---

### Post by carbon-14 on 2008-08-07
Me to this sucks

---

### Post by MAAnzz on 2008-08-12
> **quantum-positron said:**
> I am having the same problem anyone have a solution

Open the terminal and enter:
```
sudo apt-get install xorg-dev
```

---

