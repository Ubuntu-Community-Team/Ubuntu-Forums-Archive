---
title: "how does exactly sudo apt-get work?????"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by shobhitsharda on 2009-06-06
hi all,
this is a doubt i always have when i am installing any package using command "sudo apt-get install <pkg name>"?
let me explain it further...
every package is having dependencies......think of a situation where there is a cyclic dependencies.in this case how does ubuntu recover from it....i have heard about different package management policies?what is applied here to recover a cyclic dependencies????

take an example...
consider a situation where pkg1 dependent on pkg2 and none of them are not installed in ubuntu...now sudo apt-get install pkg1 solve this by installing both but i cant understand how??? 

thanx in advance......

---

### Post by zvacet on 2009-06-06
I believe you will find answere to your question [here.]("http://www.debian.org/doc/manuals/apt-howto/") And more than that ;)

---

### Post by cariboo on 2009-06-06
Apt-get reads the package info, and installs any of he dependencies that are specified in that information. Sometimes it is better to use Synaptic Package Manager to install packages, as the program will tell you what dependencies are going to be installed along with the package you want to install.

You can open a .deb file to see what is inside the package, and have a look at the scripts to see what is going to be done. Personally I use mc, but I'm sure you can do the same thing with file roller.

---

### Post by philcamlin on 2009-06-06
it finds the app you specefied and then downloads it for you

ie: sudo apt-get apache2
         ^ finds the app in senaptic and if its there it installs :popcorn:

---

