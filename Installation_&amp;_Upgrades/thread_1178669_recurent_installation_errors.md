---
title: "recurent installation errors"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Zeroshin on 2009-06-04
everytime i try to install a .deb and stuff, it never works!

it always shows an error message in the package installer like these :
Error: Dependency is not satisfiable: krusader (= 2.0.0-ubuntu810-0intrepid0)
or
Error: Wrong architecture 'i386'
or
Error: some other thing that includes the python architecture...

i run ubuntu 9.04, i just downloaded it from the ubuntu website yesterday and im a complete n00b on linux

please someone help!

---

### Post by merlinus on 2009-06-04
If you are running 64-bit, that would cause Error: Wrong architecture 'i386'

Look for a 64-bit version of the software package.

Also, you might try updating your apt-get sources.

---

### Post by Zeroshin on 2009-06-04
and what if there's not 64 bits version of that thing?
like, flash player... there's no 64 bits version for that :S

---

### Post by merlinus on 2009-06-04
There is a long thread in the 64-bit forum about flash.

---

### Post by oldos2er on 2009-06-04
> **Zeroshin said:**
> and what if there's not 64 bits version of that thing?
like, flash player... there's no 64 bits version for that :S

 Yes there is: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

### Post by buzzmandt on 2009-06-04
I thought 386 would install on a 64 bit machine?

---

### Post by Zeroshin on 2009-06-04
the "Error: Dependency is not satisfiable: krusader (= 2.0.0-ubuntu810-0intrepid0)" is an error i get from a 64 bits application...
when i try any other installers, i get only the i386 error.

---

### Post by Partyboi2 on 2009-06-04
> **Zeroshin said:**
> the "Error: Dependency is not satisfiable: krusader (= 2.0.0-ubuntu810-0intrepid0)" is an error i get from a 64 bits application...
when i try any other installers, i get only the i386 error.
Install the missing dependency which is krusader
```
sudo apt-get install krusader 
```

---

### Post by Zeroshin on 2009-06-04
<=- iz n00b.

thanks, that did the trick for this one.

and like what buzzmant said, isn't 32bits stuff supposed to be working on 64 bits?

plus, how do you update your apt-get source?

---

### Post by merlinus on 2009-06-04
```

sudo apt-get update

```FWIW, I have found with a few apps that I could not run the 32-bit versions.  Examples include skype, opera, and rawtherapee.

---

### Post by Zeroshin on 2009-06-04
i found a thread treating of skype installation on 64bit :

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

and thanks again! :D

---

