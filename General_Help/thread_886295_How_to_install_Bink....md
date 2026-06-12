---
title: "How to install Bink..."
date: 2008-08-11
forum: General Help
---

### Post by deinonychai on 2008-08-11
While installing the Bink player here on my 8.04 machine, I came across a thread that wondered how to do so:

[http://ubuntuforums.org/showthread.php?t=314577](http://ubuntuforums.org/showthread.php?t=314577)

The thread was closed b/c of age, but with a fairly recent reply.  So, I thought I'd post what I tried, if only to see if I should have done something differently :)

The first step, of course, involves downloading the actual Bink file from:
[http://www.radgametools.com/bnkdown.htm](http://www.radgametools.com/bnkdown.htm)

Next, extract the file to your home directory.

Next, open up a terminal window, make sure you're in the home directory, and type: sudo chmod +x BinkPlayer.  

Finally, type: sudo mv BinkPlayer /usr/sbin/

After that, you should be able to type BinkPlayer <filename.bik> for any and all .bik files you want to view (NWN movies included!)

---

### Post by frankob on 2009-03-25
I got this error when I run Bink Player:

BinkPlayer: error while loading shared libraries: libmikmod.so.2: cannot open shared object file: No such file or directory

I have Ubuntu Intrepid 64 bit, I guess it is because I don't have libmikmod2 for 32 bit.. is there a way I can make run it anyway?

---

