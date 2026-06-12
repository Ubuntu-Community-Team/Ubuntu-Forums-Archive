---
title: "installing .tar plugin for UBuntu 9.04"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by brucezepplin on 2009-08-07
Hi, I am trying to install a .tar plugin onto my Ubuntu 9.04 Jaunty Jackalope system. I understand that the preferred file type for this system is a .deb file, but there are ways to convert ( Alien ) and alternative ways to install. I have gone into the terminal, then the directory in which the file is found ( I used an ls command to verify this ), and tried " make && sudo make install <filename> ". But this does not work, i get something like...

" make: *** No targets specified and no makefile found.  Stop. "

Here is the entire code I put in and I am trying to install a plugin called " atlantis "

arron@arron-laptop:~$ cd Downloads
arron@arron-laptop:~/Downloads$ ls
atlantis  earthandmoon.png
arron@arron-laptop:~/Downloads$ make && sudo make install atlantis
make: *** No targets specified and no makefile found.  Stop.
arron@arron-laptop:~/Downloads$ 

Is this method just not going to work at all, or would I have to use Alien to convert the .tar file into a .deb file?


any help would be much appreciated!

---

### Post by phillw on 2009-08-07
[SIZE=2]I'd suggest you start here ...

[http://ubuntuforums.org/showthread.php?t=244832](http://ubuntuforums.org/showthread.php?t=244832)

Hope it helps !!

Regards,

Phill.
[/SIZE]

---

### Post by Partyboi2 on 2009-08-07
> **brucezepplin said:**
> Hi, I am trying to install a .tar plugin onto my Ubuntu 9.04 Jaunty Jackalope system. I understand that the preferred file type for this system is a .deb file, but there are ways to convert ( Alien ) and alternative ways to install. I have gone into the terminal, then the directory in which the file is found ( I used an ls command to verify this ), and tried " make && sudo make install <filename> ". But this does not work, i get something like...

" make: *** No targets specified and no makefile found.  Stop. "

Here is the entire code I put in and I am trying to install a plugin called " atlantis "

arron@arron-laptop:~$ cd Downloads
arron@arron-laptop:~/Downloads$ ls
atlantis  earthandmoon.png
arron@arron-laptop:~/Downloads$ make && sudo make install atlantis
make: *** No targets specified and no makefile found.  Stop.
arron@arron-laptop:~/Downloads$ 

Is this method just not going to work at all, or would I have to use Alien to convert the .tar file into a .deb file?


any help would be much appreciated!
Hi, once you are in your Downloads directory you need to first enter the atlantis directory before trying to compile. So it should be
```
cd /Downloads/atlantis
```

---

### Post by wojox on 2009-08-07
You did unpack it right?
```
tar -xvf filename.tar
```
And
```
./configure
```

---

