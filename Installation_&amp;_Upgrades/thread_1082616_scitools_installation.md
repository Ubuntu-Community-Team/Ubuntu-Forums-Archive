---
title: "scitools installation"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by winzer on 2009-02-28
I tried to install scitools. I tested to see if it worked by typing 
```
from scitools.all import *
```
The output was not good:
```
from scitools.all import *
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:531: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:538: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:571: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:578: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:581: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:584: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:648: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:709: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:774: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/gnuplot_.py:831: Warning: 'with' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:750: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:751: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:773: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:773: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:775: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:775: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:776: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:777: Warning: 'as' will become a reserved keyword in Python 2.6
/opt/conduit/root/simula/scitools-0.4.0/python-site/scitools/easyviz/common.py:779: Warning: 'as' will become a reserved keyword in Python 2.6
sh: gnuplot: not found
sh: gnuplot: not found
scitools.easyviz backend is gnuplot

```

I followed directions from [http://code.google.com/p/scitools/wiki/Installation]("http://code.google.com/p/scitools/wiki/Installation")

It looks like i need gnuplot. Anything else?

---

### Post by Partyboi2 on 2009-02-28
The directions (the link you provided)  list what packages are required at the top of the page. Looking at what you have posted I would go ahead and install gnuplot and see if it complains about anything else. If you installed it by adding the repository provided  in the directions to your 3rd party list then that should pull in all the required dependencies.

---

### Post by Soti007 on 2009-05-17
I get the following errors when I try to install.

```
unpacking python-scitools (from .../python-scitools_0.4-1~gutsy1_all.deb) ...
Setting up python-scitools (0.4-1~gutsy1) ...
Compiling /usr/lib/python2.6/dist-packages/scitools/convergencerate.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/convergencerate.py', 203, 36, "                                with='points', title='data')\n"))

Compiling /usr/lib/python2.6/dist-packages/scitools/FuncDependenceViz.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/FuncDependenceViz.py', 211, 24, '                    with="line %d" % line_counter))\n'))

Compiling /usr/lib/python2.6/dist-packages/scitools/easyviz/common.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/easyviz/common.py', 750, 10, "        as = self._prop['arrowscale']\n"))

Compiling /usr/lib/python2.6/dist-packages/scitools/easyviz/gnuplot_.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/easyviz/gnuplot_.py', 531, 63, "                                title=item.getp('legend'), with=withstring,\n"))

/usr/lib/python2.6/dist-packages/scitools/odesolve.py:1446: SyntaxWarning: assertion is always true, perhaps remove parentheses?
  assert(T is not None, 'T must be given!')
pycentral: pycentral pkginstall: error byte-compiling files (60)
pycentral pkginstall: error byte-compiling files (60)
dpkg: error processing python-scitools (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-scitools (0.4-1~gutsy1) ...
Compiling /usr/lib/python2.6/dist-packages/scitools/convergencerate.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/convergencerate.py', 203, 36, "                                with='points', title='data')\n"))

Compiling /usr/lib/python2.6/dist-packages/scitools/FuncDependenceViz.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/FuncDependenceViz.py', 211, 24, '                    with="line %d" % line_counter))\n'))

Compiling /usr/lib/python2.6/dist-packages/scitools/easyviz/common.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/easyviz/common.py', 750, 10, "        as = self._prop['arrowscale']\n"))

Compiling /usr/lib/python2.6/dist-packages/scitools/easyviz/gnuplot_.py ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.6/dist-packages/scitools/easyviz/gnuplot_.py', 531, 63, "                                title=item.getp('legend'), with=withstring,\n"))

pycentral: pycentral pkginstall: error byte-compiling files (58 )
pycentral pkginstall: error byte-compiling files (58 )
dpkg: error processing python-scitools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-scitools
```
I try to install using "Synaptic Package Manager", is this an error in python-scitools package or is there something wrong with the way I try to do the installation ?  I am running Release 9.04  ,Kernel 2.6.28-11-generic

---

### Post by archeryguru2000 on 2009-05-26
Don't forget to try that particular code within your interactive python command line (i.e.)...

```

$: python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from scitools.all import *
scitools.easyviz backend is gnuplot
>>> _

```

Try this to see if you come up with any success.  Then repost your results.

~~archery~~

---

### Post by isabelpuchoc on 2010-03-11
hi well when i want to test if I installed scitools I do this one

>>> from scitools.all import *
scitools.easyviz backend is gnuplot

It is ok, or is bad i need to install  anything else

---

