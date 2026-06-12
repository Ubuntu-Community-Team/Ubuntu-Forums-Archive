---
title: "Installing Wine 1.1.13 on Ubuntu/no internet"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by TIMU-Is-My-Username on 2009-01-25
Person=n00b

Laptop OS: Ubuntu
Intrepid Ibex
I don't have internet access on my laptop.
Trying to install Wine 1.1.13

I got both Ubuntu and Wine by downloading from my desktop, which is Windows XP and saving on a flashdrive.  Ubuntu is on my laptop now, installed perfectly.  Wine... well, I moved the ".tar.bz2" file to my desktop and extracted it, so the "wine-1.1.13" folder is next to the ".tar.bz2" on my laptop.  Left both, just to be safe in case either worked.

I'm on the desktop, nothing's open.  I got to Applications > Accessories > Terminal.  I type in "sudo apt-get install wine".  It asks me for my password, and I type it in.

"steven@stevens-laptop:~$ sudo [COLOR="red"]apt-get[/COLOR] install wine
[sudo] password for steven:
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR="Lime"]E: Couldn't find package wine[/COLOR]
steven@stevens-laptop:~$"

That's what I get.  "E: Couldn't find package wine.

Now let's try...

"steven@stevens-laptop:~$ sudo [COLOR="Red"]aptitude[/COLOR] install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "wine"
Couldn't find any package whose name or description matched "wine"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

steven@stevens-laptop:~$"

Basically, whether I type "sudo apt-get install wine" or "sudo aptitude install wine" in Terminal, from the desktop, I get error messages telling me it won't comply.

Now I go to System > Administration > Software Sources.
In the Ubuntu Software tab: main, universe, restricted and multiverse are all checked; Source code is not.  The list tells me "Cdrom with Ubuntu 8.10 'Intrepid Ibex' is checked.  Great, I have Intrepid Ibex.  So... I still don't have Wine.

Third-Party Software tab, I've added the "Scott Ritchie.gpg" key, so "WineHQ - Ubuntu 8.10 "Intrepid Ibex" is checked.  I added the Scott Ritchie key from Ubuntu's website.  After all, I'm trying to install Wine on an Intrepid Ibex system.

Yeah, not sure what to do from here.  My Internet's not working and I'm having troubles with my CD-Rom, but I'm trying to install Wine.  Anybody know what to do in this situation?

---

### Post by taurus on 2009-01-25
You are trying to install wine from the repos with those commands which you can't since your machine is not connected to the internet.

Just post the output of this command from a terminal.

```
ls -la ~/Desktop/wine-1.1.13
```

---

### Post by TIMU-Is-My-Username on 2009-01-25
> **taurus said:**
> You are trying to install wine from the repos with those commands which you can't since your machine is not connected to the internet.

Just post the output of this command from a terminal.

```
ls -la ~/Desktop/wine-1.1.13
```

Hahaha... okay so basically, I was giving a fisherman a club and telling him to catch a shark.  Great!  :P

Okay, so like, I followed the code you gave me, and it gave me this huge sexy list that looks something like this:
"drwxr-xr-x 11 steven steven 4096 2009-01-25 03:39 .
drwxr-xr-x 4 steven steven 4096 2009-01-25 18:33 ..
-rw-rw-r 1 steven steven 8108 2009-01-16 08:28 aclocal.m4
etc
etc..."

But I really don't know what to do with it.  This is definitely the furthest I've been so far though, so I must admit, I love Linux experts!

---

### Post by taurus on 2009-01-25
```
cd ~/Desktop/wine-1.1.13
./configure
make depend && make
```

---

### Post by TIMU-Is-My-Username on 2009-01-25
> **taurus said:**
> ```
cd ~/Desktop/wine-1.1.13
./configure
make depend && make
```

I don't think it worked:

"steven@stevens-laptop:~$ ls -la ~/Desktop/wine-1.1.13
total 1208
drwxr-xr-x  11 steven steven   4096 2009-01-25 19:36 .
drwxr-xr-x   4 steven steven   4096 2009-01-25 18:33 ..
-rw-rw-r--   1 steven steven   8108 2009-01-16 08:28 aclocal.m4
-rw-rw-r--   1 steven steven  49250 2009-01-16 08:28 ANNOUNCE
-rw-rw-r--   1 steven steven  16104 2009-01-16 08:28 AUTHORS
-rw-r--r--   1 steven steven  11748 2009-01-25 19:36 config.log
-rwxrwxr-x   1 steven steven 872696 2009-01-16 08:28 configure
-rw-rw-r--   1 steven steven 107983 2009-01-16 08:28 configure.ac
-rw-rw-r--   1 steven steven  26434 2009-01-16 08:28 COPYING.LIB
drwxr-xr-x 284 steven steven  12288 2009-01-25 00:33 dlls
drwxr-xr-x   2 steven steven   4096 2009-01-25 00:33 documentation
drwxr-xr-x   2 steven steven   4096 2009-01-25 00:33 fonts
-rw-rw-r--   1 steven steven   6914 2009-01-16 08:28 .gitignore
drwxr-xr-x   5 steven steven  12288 2009-01-25 00:33 include
drwxr-xr-x   5 steven steven   4096 2009-01-25 00:33 libs
-rw-rw-r--   1 steven steven    824 2009-01-16 08:28 LICENSE
-rw-rw-r--   1 steven steven   1324 2009-01-16 08:28 LICENSE.OLD
drwxr-xr-x   2 steven steven   4096 2009-01-25 00:33 loader
-rw-rw-r--   1 steven steven   4459 2009-01-25 01:07 Makefile.in
-rw-rw-r--   1 steven steven   4441 2009-01-16 08:28 Makefile.in~
-rw-rw-r--   1 steven steven   9673 2009-01-16 08:28 Make.rules.in
drwxr-xr-x  48 steven steven   4096 2009-01-25 00:33 programs
-rw-rw-r--   1 steven steven   6384 2009-01-16 08:28 README
drwxr-xr-x   2 steven steven   4096 2009-01-25 00:33 server
drwxr-xr-x   9 steven steven   4096 2009-01-25 02:39 tools
-rw-rw-r--   1 steven steven     20 2009-01-16 08:28 VERSION
steven@stevens-laptop:~$ cd ~/Desktop/wine-1.1.13
steven@stevens-laptop:~/Desktop/wine-1.1.13$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for cpp... cpp
checking whether gcc -m32 works... no
configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.
steven@stevens-laptop:~/Desktop/wine-1.1.13$ make depend && make
make: *** No rule to make target `depend'.  Stop.
steven@stevens-laptop:~/Desktop/wine-1.1.13$"

---

### Post by TIMU-Is-My-Username on 2009-01-25
I also tried (after that one):

./configure # install
and
./configure # all

but I got the same exact error.  :(

---

### Post by TIMU-Is-My-Username on 2009-01-25
Bumpidy bumpidy bump bump bump.

---

### Post by TIMU-Is-My-Username on 2009-01-26
Bump.

---

### Post by mc4man on 2009-01-26
I'd say to build wine on an install that has no basic build packages installed will require 80 - 100 packages, plus wine, while not hard to build, may prove frustrating if you've no experience compiling.

Far easier would be to install from a .deb, then all you'll need to get is the run dependiences (and possibly some inter dependencies

There are many ways to do offline installs, here's one way that will work on any pc/Os with an internet connection, though you will need a live cd of the exact ubuntu release of the target machine. Other than that it's a piece of cake.

[http://ubuntuforums.org/showthread.php?p=6607018#post6607018](http://ubuntuforums.org/showthread.php?p=6607018#post6607018)

Otherwise search around, as mentioned there are several methods and some apps that can do this for you.

---

### Post by EXCiD3 on 2009-01-27
I would say try using [Keryx]("http://keryx.betaserver.org") to download straight from the proper Wine repositories to a flash drive. It can also grab all your updates and any other software easily just like you were using apt-get or Synaptic. It can run from any windows PC, linux or mac (the last two must have python installed and wxpython for now at least).

---

