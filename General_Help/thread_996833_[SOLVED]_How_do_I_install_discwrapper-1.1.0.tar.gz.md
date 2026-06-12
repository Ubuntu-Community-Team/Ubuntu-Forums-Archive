---
title: "[SOLVED] How do I install discwrapper-1.1.0.tar.gz"
date: 2008-11-29
forum: General Help
---

### Post by swotie on 2008-11-29
How do I install discwrapper-1.1.0.tar.gz

---

### Post by swotie on 2008-11-29
How do I install discwrapper-1.1.0.tar.gz

---

### Post by __Ryan__ on 2008-11-29
First you should make sure that this package doesn't exist in the repository already.  If it does then it will be a breeze to install.

Aside from that you will have to untar the file:

```
tar xvzf discwrapper-1.1.0.tar.gz
```

It will most likely spit out a bunch of files into another directory which it creates.  There should probably be a README file in there somewhere that will tell you what to do next.

---

### Post by davidbilla on 2008-11-29
What's the problem? 

Doesn't it work in the normal way? Can't you just untar and compile it? Is it the source, in the first place? Doesn't it have 'INSTALL.txt' or 'Installation.txt' inside?

---

### Post by taurus on 2008-11-29
Normally, you would open a terminal, Applications -> Accessories -> Terminal, and change to whichever directory that discwrapper-1.1.0.tar.gz is located.

```
cd ~/Desktop
```
Then, you need to unpack it.

```
tar xvzf discwrapper-1.1.0.tar.gz
```
That would create a new directory, probably called discwrapper-1.1.0, so you need to change to that new directory.

```
cd discwrapper-1.1.0
```
Hopefully, there is a README or INSTALL telling you what to do next.

```
more INSTALL
```

---

### Post by swotie on 2008-11-29
I have found the readme text, but I can't understand number II

II. Install DiscWrapper:
      ./configure
      make
      sudo make install

-----------------------------------------------------------------------------
Build and Installation
-----------------------------------------------------------------------------

 I. Install dependencies:
    1)  install the GNU C++ compiler

    2)  install wxWidgets 2.8.8 or above
       If you use a Debian based distro and your repo doesn't have it, I
       suggest to do the following:
        - In terminal:
	   wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -
        - Then add to Software sources:
	   deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) distname main
          DON'T forget to replace distname with the name of your distro like:
	   for Ubuntu Hardy: hardy-wx
	   for Debian Etch: etch-wx
        - Use Synaptic to install:
		  libwxbase2.8-0, libwxbase2.8-dev, libwxgtk2.8-0,
		  libwxgtk2.8-dev, wx2.8-headers

    3)  make sure coreutils is installed (I think it is by default)

 II. Install DiscWrapper:
      ./configure
      make
      sudo make install
    
      DiscWrapper now should be in Applications->Graphics

---

### Post by swotie on 2008-11-29
I have found the readme text, but I can't understand number II

II. Install DiscWrapper:
./configure
make
sudo make install

-----------------------------------------------------------------------------
Build and Installation
-----------------------------------------------------------------------------

I. Install dependencies:
1) install the GNU C++ compiler

2) install wxWidgets 2.8.8 or above
If you use a Debian based distro and your repo doesn't have it, I
suggest to do the following:
- In terminal:
wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -
- Then add to Software sources:
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) distname main
DON'T forget to replace distname with the name of your distro like:
for Ubuntu Hardy: hardy-wx
for Debian Etch: etch-wx
- Use Synaptic to install:
libwxbase2.8-0, libwxbase2.8-dev, libwxgtk2.8-0,
libwxgtk2.8-dev, wx2.8-headers

3) make sure coreutils is installed (I think it is by default)

II. Install DiscWrapper:
./configure
make
sudo make install

DiscWrapper now should be in Applications->Graphics

---

### Post by taurus on 2008-11-29
It just means that you have to build and install it from source code.  Before you build anything, you need to install the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
./configure
make
sudo make install
```

You probably need to install other dependencies first when you run the ./configure.  You can look for the name of those files in System -> Administration -> Synaptic Package Manager -> Search.

---

### Post by __Ryan__ on 2008-11-29
The installer wants you up install another package.  It does this by having you add another package repository to your system.  After it's added you can automatically install the package through aptitude or apt-get.

If you trust this package and the repository it wants you to add then you could go ahead and do it.  You should be careful as to which repositories you add as bad things can happen if you add one containing malicious packages.

---

### Post by swotie on 2008-11-29
ok - I understand, but it come with fault message when I try to run the code ... It can't find the source for the program .... error 404

---

### Post by swotie on 2008-11-29
ok - I understand, but it come with fault message when I try to run the code ... It can't find the source for the program .... error 404

---

### Post by binbash on 2008-11-29
[http://www.getdeb.net/app/DiscWrapper](http://www.getdeb.net/app/DiscWrapper)

---

