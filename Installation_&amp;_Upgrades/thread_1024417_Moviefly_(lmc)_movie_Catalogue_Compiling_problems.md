---
title: "Moviefly (lmc) movie Catalogue: Compiling problems"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by tonybeccar on 2008-12-29
Hello, i'm trying to compile the Moviefly movie catalogue which is a Linux version of the Ant movie catalog.

Moviefly's page: [http://savannah.nongnu.org/projects/lmc/](http://savannah.nongnu.org/projects/lmc/)

The thing is i installed all the dependences that the instructions say, but when I run "./configure", y end getting the error that "cannot find python stringtemplate module". I googled this stringtemplate and i installed the pystringtemplate v3.1 and v2.2 after no succes. When i try to compile the moviefly i get the same error again. 

Anyone uses this movie catalog? Anyone knows how to fix this compiling problem? Anyone know anything about the module stringtemplate?

Any kind of help will be much appreciated.

Here is my output of the "./configure". Thank you!

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for perl... perl
checking for perl version greater than or equal to 5.8.4... ok
checking for perl module LWP::UserAgent... ok
checking for perl module URI::Escape... ok
checking for perl module POSIX... ok
checking for a Python interpreter with version >= 2.3.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for Python include path... /usr/include/python2.5
checking for Python library path... /usr/lib/python2.5/config
checking python extra libraries... 
checking python module: qt... yes
checking python module: stringtemplate... no
configure: error: failed to find required module stringtemplate



And if anyone suggests that i should use the Ant movie catalog with wine, i won't because it's not working very well under it :S. Again, thanks in advance!

---

### Post by kostkon on 2008-12-29
> **tonybeccar said:**
> Hello, i'm trying to compile the Moviefly movie catalogue which is a Linux version of the Ant movie catalog.

Moviefly's page: [http://savannah.nongnu.org/projects/lmc/](http://savannah.nongnu.org/projects/lmc/)

The thing is i installed all the dependences that the instructions say, but when I run "./configure", y end getting the error that "cannot find python stringtemplate module". I googled this stringtemplate and i installed the pystringtemplate v3.1 and v2.2 after no succes. When i try to compile the moviefly i get the same error again. 

Anyone uses this movie catalog? Anyone knows how to fix this compiling problem? Anyone know anything about the module stringtemplate?

Any kind of help will be much appreciated.

Here is my output of the "./configure". Thank you!

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for perl... perl
checking for perl version greater than or equal to 5.8.4... ok
checking for perl module LWP::UserAgent... ok
checking for perl module URI::Escape... ok
checking for perl module POSIX... ok
checking for a Python interpreter with version >= 2.3.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for Python include path... /usr/include/python2.5
checking for Python library path... /usr/lib/python2.5/config
checking python extra libraries... 
checking python module: qt... yes
checking python module: stringtemplate... no
configure: error: failed to find required module stringtemplate
Try installing the *python-dev* package.
> **tonybeccar said:**
> And if anyone suggests that i should use the Ant movie catalog with wine, i won't because it's not working very well under it :S. Again, thanks in advance!
No, but I would suggest you to give [*GCStar*]("http://www.gcstar.org/") and [*Griffith*]("http://www.griffith.cc/") a try.

They are already in the repos, so you don't need to compile them ;)

---

### Post by tonybeccar on 2008-12-29
Thank you so much for your reply!

I already have installed the python-dev package. I downloaded the pyStringTemplate tar file and tried to install it, i don't know if I succeded, but I have the stringtemplate folder inside /usr/lib/python2.5/site-packages. 

I already downloaded Griffith and I'm giving it a try, although I don't think it's gonna work out for me because I use to export a MySQL database which I import in a webpage template of mine. I'll try the first program you recommended.

Any other suggestions for the stringtemplate thing?

Again, a lot of thanks!

---

### Post by tonybeccar on 2008-12-29
I installed both of the catalogs you recommended but they are not too useful for ME.

I would really like to solve the problem of the stringtemplate library.

I downloaded the PyStringTemplate v3.1 and installed it according to the instructions, and it created a folder under /usr/lib/python2.5/site-packages names stringtemplate3 and it still says it can't find the module stringtemplate. 

In the dependences I read that the lmc used Python 2.3, I wonder if it has anything to do with anything. I can't find any dev in the repos that would work.

I attached a copy of the stringtemplate in this post. Please anyone has any suggestions for this problem?

---

### Post by JuanC on 2009-01-01
I am also like to run lmc (MovieFly) in ubuntu.

I have a catalog made from Ant Movie Catalog and i prefer to use native linux applications instead of use Wine.

I try to compile lmc and i get the same problems with stringtemplate.

---

### Post by CDN MILLWRIGHT32 on 2009-07-05
I also have a movie catalog of all my DVD's. I made it in XP with Ant.
I installed Ant with wine on Ubuntu 9.04 and it works fine.

Ant is here [http://www.antp.be/software/moviecatalog/download](http://www.antp.be/software/moviecatalog/download)

install it to your desktop and right click, select open with "Wine Windows Program Loader"

Cheers.

---

