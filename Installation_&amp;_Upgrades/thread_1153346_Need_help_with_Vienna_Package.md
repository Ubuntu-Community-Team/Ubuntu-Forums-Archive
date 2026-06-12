---
title: "Need help with Vienna Package"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by gear2d on 2009-05-08
This is long shot and was wondering if anyone can help here. I download this package called Vienna Package (used for RNA structrues found here: [http://www.tbi.univie.ac.at/~ivo/RNA/]("http://www.tbi.univie.ac.at/%7Eivo/RNA/")  and downloadable package here: [http://www.tbi.univie.ac.at/~ivo/RNA/ViennaRNA-1.8.2.tar.gz]("http://www.tbi.univie.ac.at/%7Eivo/RNA/ViennaRNA-1.8.2.tar.gz")   ).

Now I  was able to install the main program and run it great. But my problem is installing these small programs (that are not installed by default) when you initially install the main program. These optional programs are located in the "Utils" folder. There is Makefile, Makefile.am, Makefile.in in this folder in addition to the small programs. How can install these small programs? And, here is the list of the programs found here if it helps:

[http://www.tbi.univie.ac.at/~ivo/RNA/utils.html]("http://www.tbi.univie.ac.at/%7Eivo/RNA/utils.html")

---

### Post by menna.siam on 2009-07-01
I am new to linux, and I am trying to run the Vienna package main program but I don't know how? can u please tell me the steps to do that ASAP 

Thanks in advance

---

### Post by flomar on 2011-01-26
I just installed Vienna RNA Package & RNAz on Ubuntu 10.10 and what I needed to sucessfully compile the two source packages was the package called **med-bio**. Took me some while to figure it out, with this however it works smoothly.
```
sudo apt-get install med-bio
./configure
make
sudo make install
```
e voila, its done.
test later with
```
RNAz --version
```

---

