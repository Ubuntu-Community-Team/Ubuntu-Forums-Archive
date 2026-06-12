---
title: "List packages not needed by other packages"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by executivul on 2009-09-06
Hello everybody,
this is my first post here but i"ve been reading the forums for a while now.
My question is: how can I get a list of all packages not needed by other packages?
Eg. xorg, firefox, vlc, icewm => firefox, vlc, icewm depend on xorg so xorg should not be listed but the other 3 should be as long as each can be removed without affecting other packages.
My objective is to make the smallest distro while keeping certain functionality.
Thanks.

---

### Post by executivul on 2009-09-10
still nobody?
i feel that even a command line system installed via the mini-cd can be further trimmed (460MB) so there must be a way to discover what are the packages that are not needed by other packages...

ps: the deborphan seems not to detect them, i've tried, or maybe i did'n use the right parameters

---

### Post by Vector_Matt on 2009-09-10
"deborphan --guess-all" is the proper command for deborphan (note that it's two dashes "guess" one dash "all")

There's also "apt-get autoremove"

If those turn up nothing then there are probably no spare packages left, except of course deborphan itself which won't list itself as superfluous.


If you're just looking to get a really small Linux distro you could try [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) I'm not sure what in particular you want to accomplish though, so I'm only guessing at this point.

---

### Post by wojox on 2009-09-10
Are you looking for something like this:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by executivul on 2009-09-10
What I'm trying to achive :) good question :)
I'm trying to build a distro for internal use, aprox 200 computers, pretty strong: Celerons 2Ghz, 2Gb RAM, no storage. They boot a pxelinux, a small loader, the loader gets the system itself, unpacks it into ram and boots it like a normal distro. 
Constraints: 
1)tmpfs can grow as big as 1/2 of ram, don't feel the need for tweaking that
2)boot time depends on the size of the compressed system image which is transferred via the 100mbit network (~30sec for a 350mb image) and the decompression time (~15sec)
Requirements:
-graphical interface :) (Openbox)
-2 web browsers (Firefox+Opera)
-Open Office
-PDF Reader 
-Multimedia support (vlc is ok)

Did all that, all works ok, BUT, the distro is a mix of Suse, SLAX and custom made packages, a reall mess and really complicated to upgrade or add more packages.
I fell in love with the "Ubuntu way" of dealing with packages (apt) so I paln on changing the "distro" part of the system to Ubuntu, and want to get the needed functionality with minimal disk(ram) needed. So packages that are never used (ppp, vim, etc) should be removed, and it's easier to choosefrom a list of the packages not needed by other packages, which provide direct funtionality, then to choose from a list containing all the installed packages.

thanks

LE: I'm thinking of using a script 
dpkg --get-selections > allpkg.txt
dpkg ???????? > neededpkg.txt  (something like list all dependencies for every package)
sort both of them
uniq the neededpkg.txt (a package might be needed by many)
diff allpkg.txt neededpkg.txt | grep only in all
:)

script will be used recursively, remove unneeded, rerun, remove, rerun, etc

---

