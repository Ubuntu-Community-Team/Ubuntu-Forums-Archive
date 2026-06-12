---
title: "Numpy is unable to install"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by baba786 on 2009-05-03
Hi all,
It is my first post on the forum so sorry if I made any mistake. Today I install the ubuntu setup in my system(desktop). After completing the Installation installed the pyglet in my system using 

python setup.py install 

it installed successfully inside my system, then download the NUMPY-1.-3.0 ,after completing the download ,go for the installation to it but its showing an error and error is 


SystemError: Cannot compiler 'Python.h'. Perhaps you need to install python-dev|python-devel.

you can view how I did all the installation part here 

 [http://dpaste.com/40445/](http://dpaste.com/40445/)

---

### Post by agim on 2009-05-03
Welcome to the community.
When using linux, you will find that there are different ways of doing things. With most applications, you don't have to download and install it anymore.
If you want to install numpy, you open up synaptic, your package manager.
Go to System-Administration-Package Manager on the top panel, and search for numpy.
A few things will pop up, just check the box next to python-numpy and click install. It will take care of all of the dependencies for you (things like python.h)

Or, if you want to use the terminal. Open a terminal and type

sudo apt-get install python-numpy

Let me know if this works for you.

cheers

---

### Post by agim on 2009-05-03
Still here? Any luck?

---

### Post by baba786 on 2009-05-03
thanks a lot its working now

---

