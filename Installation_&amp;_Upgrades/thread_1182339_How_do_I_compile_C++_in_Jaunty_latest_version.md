---
title: "How do I compile C++ in Jaunty latest version??"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Noobuntu5 on 2009-06-08
Getting an error when I try to compile C++ using Jaunty latest ver. 

sudo apt-get install g++
[sudo] password for tuxorsauce: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any Idears?

---

### Post by amingv on 2009-06-09
That's not the compiler command, that would be for installing g++.
Apparently, two or more instances of apt are trying to run at the same time, wait for one to finish before you install your next program.

Instead of installing g++, install build-essential:
```
sudo aptitude install build-essential
```

and compile your c++ sources with this command:

```
g++ my_source.cpp -o my_binary
```

For more info, check the stickies in the programming talk subforum here:
[http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

---

