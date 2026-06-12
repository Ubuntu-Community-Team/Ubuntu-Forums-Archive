---
title: "ROOT is now in the Ubuntu Repositories"
date: 2008-10-20
forum: General Help
---

### Post by es926 on 2008-10-20
Hello,

I noticed today that ROOT and a good selection of its plugins are available in the intrepid repositories (under universe). I'm happy to see this and I thought that I should mention it here for anybody who uses or in the future will use ROOT.

I've seen a number of posts discussing the relative merits of Octave, Sage, Scilab, etc and I rarely see ROOT mentioned. ROOT was developed as a tool for high energy physicists but it has a lot of great features that make it versatile enough for a wide range of scientific applications. At its heart is CINT, which is a c/c++ interpreter. You can run the interpreter interactively or use it to run scripts (or macros). Then there is a huge library of classes covering special math functions, wysiwyg gui design, histogramming, graphing, random number generation, fitting, root finding, and many many other things. Check out this link if you want to dig a little deeper: [http://root.cern.ch/root/doc/RootDoc.html](http://root.cern.ch/root/doc/RootDoc.html).

One of the plugins in the repository is pyROOT, which for any python or scipy fan is a must see. It brings all of the functionality of the ROOT class library into python (and lets you execute python code from ROOT as well).

Alright, there's my quick plug of ROOT. Hopefully this is enough info to pique the interest of anybody who might like to give it a shot.

Take care!

---

### Post by frausch on 2008-11-21
Hi,

thank you for porting root. 

However, I have some problems in setting up PyROOT. I set the PYTHONPATH and the LD_LIBRARY_PATH to /usr/lib/root/5.18 and tried an 'import ROOT' in python. Like this I always did it with my selfcompiled root. With the packages from the repository, I got an error 'ImportError: No module named ROOT'

Cheers

frausch

---

### Post by frausch on 2008-11-25
Hi,

I found it out myself. To use pyroot in python, the package 'libroot-python-dev' is needed.

Cheers

frausch

---

### Post by roadkillbunny on 2009-03-02
Does not seem to work anymore, with Jaunty... :(

>   libroot-python-dev: Depends: python (< 2.6) but 2.6.1-0ubuntu2 is installed.


---

### Post by frausch on 2009-11-30
Hi,

after installing libroot-python-dev, and doing a 'import ROOT' in python, I get the following error:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.6/ROOT.py", line 88, in <module>
    import libPyROOT as _root
ImportError: No module named libPyROOT

The file /usr/lib/python-support/root/python2.6/libPyROOT.so is present, and if works, if I set the PYTHONPATH to the proper directory. So some kind of python configuration seems to be missing.

Thanks for your Help!

Felix

---

