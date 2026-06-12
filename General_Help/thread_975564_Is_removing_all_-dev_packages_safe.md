---
title: "Is removing all -dev packages safe?"
date: 2008-11-08
forum: General Help
---

### Post by DaVince21 on 2008-11-08
Hello people,

I have an older model Eee PC with a 4G drive in it, and to conserve some space I was wondering if I can safely remove all -dev packages (provided they don't take any non-dev packages with them), and how beneficial this can be for freeing up some space (some source packages seem tiny!).

I'll probably have some of the packages reinstalled later when I need to compile something, but I'd like to "clean" the downloaded -dev packages I installed every once in a while because I probably won't be needing some of them anymore.

If there is a better or alternative solution it would be appreciated too (for example, somehow tracking which -dev packages I installed and quickly removing them again later with some sort of tool or script).

Thanks in advance.

---

### Post by cmnorton on 2008-11-08
There's a remove-old function -- do not know the syntax offhand -- but I would not remove these packages, unless you are not using what the package installed. Else, you're likely to get your updates out of synch.

The bottom line is I wouldn't do it.

---

### Post by geirha on 2008-11-08
I installed Intrepid on a small partition for testing recently, and on that install, the only -dev packages I have are linux-libc-dev and xutils-dev. xutils-dev got installed by ubuntu-restricted-extras and will uninstall java if you try to uninstall it. linux-libc-dev is kernel header files. Removing it should be safe I think, but I'd leave it be. All the other -dev packages are probably safe to remove. You can get a list of all installed -dev packages with ```
aptitude -F '%p' search '~i -dev$'
```
And this will also show the installed size
```
aptitude -F '%I %p' search '~i -dev$'
```

The options used here are explained in /usr/share/doc/aptitude/README.

---

### Post by DaVince21 on 2008-11-08
Thanks for the replies. I'll play it safe and only remove the -dev packages I know I installed at some point to compile something.

Geirha, those commands are quite useful! Didn't know I could look up installed packages in such a fashion. :)

---

### Post by jamesstansell on 2008-11-08
> xutils-dev got installed by ubuntu-restricted-extras and will uninstall java if you try to uninstall it

That's kind of weird.  I wonder if that's just because of untidy packaging?

---

