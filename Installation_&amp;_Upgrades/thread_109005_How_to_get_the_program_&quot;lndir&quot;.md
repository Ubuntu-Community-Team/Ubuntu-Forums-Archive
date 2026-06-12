---
title: "How to get the program &quot;lndir&quot; ???"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by TTL on 2005-12-27
Hello,
how do I get the program lndir?
It seem it was avariable in Hoary
[http://packages.ubuntu.com/hoary/x11/xutils](http://packages.ubuntu.com/hoary/x11/xutils)
but not in Breezy
[http://packages.ubuntu.com/breezy/x11/xutils](http://packages.ubuntu.com/breezy/x11/xutils)
I think it would break a lot of dependencies if I remove the new and install the old package, so this would not be a solution.

I need lndir because the compile introduction for X.org 6.9 recomment it. And yes, without making a * virtual directory or whatever the program does * the compile run  removes some sourcefiles which it seems to need at a later moment :confused: 
[http://xorg.freedesktop.org/releases/X11R7.0/doc/html/BUILD3.html#3](http://xorg.freedesktop.org/releases/X11R7.0/doc/html/BUILD3.html#3)

Thank you

---

### Post by kaamos on 2005-12-27
The page talks about symbolic links so I guess a simple "ln -s directory_1 directory_2" should work.

There are also the instructions for compiling lndir
> If lndir is not already installed on your system, you can build it manually from the X11R6.9 sources by running the following commands:

    cd xc/config/util
    make -f Makefile.ini lndir
    cp lndir some directory in your PATH 

I think the last line could be like this "cp lndir /usr/local/bin". Hope this helps.

---

### Post by TTL on 2005-12-27
Thank you for your help, looks like I did not saw this part. ;)
After using lndir I now know what it is doing. It duplicates the directory structure and creates a link for every file pointing to the right file in the source directory.
So in my case it creates around 1000 real folders with 14000 links in it :eek:
Now I will start to compile, hope it will work now.

---

