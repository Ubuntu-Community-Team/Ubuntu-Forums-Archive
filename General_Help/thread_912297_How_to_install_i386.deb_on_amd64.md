---
title: "How to install i386.deb on amd64"
date: 2008-09-06
forum: General Help
---

### Post by G9M29 on 2008-09-06
How to install i386.deb on amd64 ???

---

### Post by forger on 2008-09-06
1) What are you trying to install? There might already be a 64-bit package in a third-party repository somewhere
2) You have to go "pro" in terminal :)
 a. Put your file on Desktop
 b. Head to Applications > Accessories > Terminal
 c. Execute this:
cd Desktop
```
sudo dpkg --force-architecture -i yourfilename.deb
```
Where you put the package file's name instead of **yourfilename.deb**

---

### Post by G9M29 on 2008-09-06
tenx man. Ur awesome

---

### Post by hyper_ch on 2008-09-06
you don't want to install a packages that was not compiled for your platform. Either get a 64bit version or compile it yourself.

---

### Post by G9M29 on 2008-09-06
I don't know how to compile it ???

---

### Post by Sycron on 2008-09-06
It's not hard. First install build-essential:
```
sudo apt-get install build-essential
```

and then untar the source.
```
tar -xf name_of_archive.tar.bz2
```
then change direcotory to the extracted folder and type.
```
./configure
make && sudo make install
```

---

### Post by forger on 2008-09-07
As I asked before, what are you trying to install? What's the name of the application/game/program ?

---

### Post by dannymichel on 2010-05-04
> **forger said:**
> As I asked before, what are you trying to install? What's the name of the application/game/program ?
i'm trying this with rezlooks.

i don't think it worked. still tells me i dont have rezlooks installed
```
danny@danny-desktop:~$ cd Desktop
danny@danny-desktop:~/Desktop$ sudo dpkg --force-architecture -i rezlooks-0.6_0.6-1_i386.deb
[sudo] password for danny: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 256567 files and directories currently installed.)
Preparing to replace rezlooks-0.6 0.6-1 (using rezlooks-0.6_0.6-1_i386.deb) ...
Unpacking replacement rezlooks-0.6 ...
Setting up rezlooks-0.6 (0.6-1) ...
danny@danny-desktop:~/Desktop$
```

---

### Post by crabsody on 2011-01-02
I have a similar problem. I'm trying to install a guitar pro demo version. It is a i386 deb file. But my architecture is x86_64

---

### Post by perspectoff on 2011-01-02
You also may need ia32-libs to run 32-bit programs on a 64-bit architecture.

 sudo apt-get install ia32-libs

If you don't have ia32-libs installed before you install your 32-bit .deb package, you may have to fix things with

 sudo apt-get install -f

or with 

 sudo dpkg --configure -a

---

### Post by psusi on 2011-01-02
You can't... 32 bit apps require 32 bit libs, so they won't work on a 64 bit system, unless they were explicitly packaged to link to 32 bit libs that were explicitly packaged to be installed on a 64 bit system, without conflicting.

---

### Post by perspectoff on 2011-01-02
> **psusi said:**
> You can't... 32 bit apps require 32 bit libs, so they won't work on a 64 bit system, unless they were explicitly packaged to link to 32 bit libs that were explicitly packaged to be installed on a 64 bit system, without conflicting.

Nonsense. See the previous post.

---

### Post by crabsody on 2011-01-02
But why synaptic fails? I mean it should be able to install a 32bit executable in a 64bit machine. Or not?

---

### Post by psusi on 2011-01-02
> **perspectoff said:**
> Nonsense. See the previous post.

Try actually running it.  It won't work.  There's a reason it doesn't let you normally.

---

### Post by crabsody on 2011-01-02
The solution from Guitar Pro site


> Here's how you can run Guitar Pro 6 on a 64-bit installation:

1) Download the latest .deb from Guitar Pro's website.
2) Goto [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and install getlibs-all.deb
3) Run this in terminal

Quote:
sudo dpkg -i --force-architecture Downloads/GuitarPro6-r7840.deb

You will get some errors but ignore.

4) Run this in terminal

Quote:
getlibs /opt/GuitarPro6/GuitarPro        

---

### Post by eekrazyk on 2011-03-16
This is driving me crazy.  I having a hell of a time getting ia32-libs installed on my Ubuntu Server 10.10 amd64 machine.

```
# sudo apt-get install ia32-libs
```

fails because it failed to fetch a few packages due to a size mismatch.  I manually downloaded and installed each of them and tried to install ia32-libs again using the command above.  It still fails, but only on one of the packages from before:  

```
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libasound2 amd64 1.0.23-1ubuntu2.1 [437kB]
Fetched 1B in 0s (8B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2_1.0.23-1ubuntu2.1_amd64.deb  Size mismatch

```

Tried manually downloading and installing it again:

```

# dpkg -i --force-architecture libasound2_1.0.23-1ubuntu2.1_amd64.deb
(Reading database ... 43520 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.12.1-0ubuntu10.2 (using libasound2_1.0.23-1ubuntu2.1_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...
Processing triggers for man-db ...

```

```
# dpkg --configure -a
```

Tried installing ia32-libs again and still get the same error.

What am I missing?

---

### Post by eekrazyk on 2011-03-16
quick update.  I tried grabbing the ia32-libs package and manually installing that.

```
# dpkg -i libasound2_1.0.23-1ubuntu2.1_amd64.deb
(Reading database ... 44964 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.12.1-0ubuntu10.2 (using libasound2_1.0.23-1ubuntu2.1_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...
Processing triggers for man-db ...

```

```

# dpkg -i ia32-libs_20090808ubuntu9_amd64.deb
(Reading database ... 44964 files and directories currently installed.)
Preparing to replace ia32-libs 20090808ubuntu9 (using ia32-libs_20090808ubuntu9_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32asound2; however:
  Package lib32asound2 is not installed.
dpkg: error processing ia32-libs (--install):
 dependency problems - leaving unconfigured
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 ia32-libs

```

```
# dpkg -i lib32asound2_1.0.23-1ubuntu2.1_amd64.deb
Selecting previously deselected package lib32asound2.
(Reading database ... 44964 files and directories currently installed.)
Unpacking lib32asound2 (from lib32asound2_1.0.23-1ubuntu2.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of lib32asound2:
 lib32asound2 depends on libasound2 (= 1.0.23-1ubuntu2.1); however:
  Package libasound2 is not installed.
dpkg: error processing lib32asound2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lib32asound2

```

huh.  I thought I just installed libasound2?  Now it's claiming it's not installed?

---

### Post by eekrazyk on 2011-03-16
Got it.  The libasound2 package really is too small.  It was showing up as about 227K on my machine and the dpkg install wasn't finishing.  I grabbed it from a different mirror and was able to install everything.

---

