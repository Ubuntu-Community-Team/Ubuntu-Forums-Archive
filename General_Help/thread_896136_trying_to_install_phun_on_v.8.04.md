---
title: "trying to install phun on v.8.04"
date: 2008-08-20
forum: General Help
---

### Post by Cokemonkey on 2008-08-20
Hello there, I am trying to install phun on a x64 ubuntu 8.04 PC and I have been referred here.

I have downloaded and ran the latest 32 bit version of phun, as i've been told it works better than the 64 bit one.

When I navigate to the extracted directory in terminal and type './phun' I get this:

```

coke@emachinex642008:~/Desktop/Phun$ ./phun
workdir =  /home/coke/Desktop/Phun/
Loading language English...
Parsing /home/coke/Desktop/Phun/autoexec.cfg...
Parsing /home/coke/Desktop/Phun/config.cfg...
Creating window...
30 resources loaded
Window created.
Prefetching resources
Loading scene /home/coke/Desktop/Phun/scenes/welcome.phn
Running program...
Creating window...
122 resources loaded
Window created.
Segmentation fault
coke@emachinex642008:~/Desktop/Phun$

```

During this process it creates a blank (black) window and then after about 2 seconds it goes away and I see terminal again.

Here is the original thread on the phun forums:
[http://www.phunland.com/forum/viewtopic.php?pid=25989#p25989](http://www.phunland.com/forum/viewtopic.php?pid=25989#p25989)

Thank you for any help.

---

### Post by Vivaldi Gloria on 2008-08-21
If I remember correctly I did this:

> Solved! I download the 3.5 version that have libGLEW and  libboost_filesystem, and then I copy the files at usr\lib

See

[http://www.phunland.com/forum/viewtopic.php?id=1501](http://www.phunland.com/forum/viewtopic.php?id=1501)

Here's the location of the files in my 32 bit system:


```
vivaldi@narval:~$ locate libGLEW
/home/vivaldi/.Phun/libGLEW.so.1.3
/home/vivaldi/.Phun/lib/libGLEW.so.1.3
/usr/lib/libGLEW.so.1.3
/usr/lib/libGLEW.so.1.5
/usr/lib/libGLEW.so.1.5.0


vivaldi@narval:~$ locate libboost_filesystem
/home/vivaldi/.Phun/libboost_filesystem.so
/home/vivaldi/.Phun/lib/libboost_filesystem.so
/usr/lib/libboost_filesystem.so
```

---

