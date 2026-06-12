---
title: "game installation help"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by r0k on 2009-03-13
i am trying to install BZflag! i have the game downloaded and the file is on my desktop! i am unsure how to install! PLEASE HELP!!

---

### Post by taurus on 2009-03-13
What format does it in?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by r0k on 2009-03-13
drwxrwxrwx 15 jake jake      4096 2009-03-13 03:10 bzflag-2.0.12

is all it says

---

### Post by taurus on 2009-03-13
Change to that directory and see what do you need to do to run it.

```
cd ~/Desktop/bzflag-2.0.12
ls -la
```

---

### Post by r0k on 2009-03-13
jake@jake-desktop:~/Desktop/bzflag-2.0.12$ ls -la
total 1836
drwxrwxrwx 15 jake jake   4096 2009-03-13 03:10 .
drwxr-xr-x  4 jake jake   4096 2009-03-13 03:01 ..
-rw-r--r--  1 jake jake 272814 2008-06-25 14:14 aclocal.m4
-rw-r--r--  1 jake jake   7234 2007-08-04 10:57 AUTHORS
-rw-r--r--  1 jake jake    704 2007-09-10 18:10 authors.xml
-rwxr-xr-x  1 jake jake  45148 2007-09-20 15:48 autogen.sh
-rw-r--r--  1 jake jake   6587 2007-08-04 10:57 BUGS
-rw-r--r--  1 jake jake   3111 2008-06-25 14:15 bzflag.info
-rw-r--r--  1 jake jake   3114 2008-04-06 01:31 bzflag.info.in
-rw-r--r--  1 jake jake    492 2008-06-25 14:15 bzflag.lsm
-rw-r--r--  1 jake jake    495 2007-08-04 10:57 bzflag.lsm.in
-rw-r--r--  1 jake jake   2191 2008-06-25 14:15 bzflag.spec
-rw-r--r--  1 jake jake   2194 2008-04-06 01:31 bzflag.spec.in
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 BZFlag.xcodeproj
-rw-r--r--  1 jake jake  50737 2008-06-25 13:59 ChangeLog
-rw-r--r--  1 jake jake  36177 2009-03-13 03:10 config.log
-rwxr-xr-x  1 jake jake 905246 2008-06-25 14:14 configure
-rw-r--r--  1 jake jake  27769 2008-06-25 14:00 configure.ac
-rw-r--r--  1 jake jake  26420 2007-08-25 19:54 COPYING
drwxrwxrwx  4 jake jake   4096 2008-06-25 14:16 data
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 debian
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 Dev-C++
-rw-r--r--  1 jake jake  17533 2008-06-20 18:05 DEVINFO
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 include
-rw-r--r--  1 jake jake   9416 2007-08-04 11:11 INSTALL
-rwxr-xr-x  1 jake jake 211618 2009-03-13 03:10 libtool
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 m4
-rw-r--r--  1 jake jake   1239 2008-06-21 16:52 Makefile.am
-rw-r--r--  1 jake jake    275 2008-04-06 01:31 Makefile.common
-rw-r--r--  1 jake jake  21821 2008-06-25 14:14 Makefile.in
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 man
drwxrwxrwx  3 jake jake   4096 2008-06-25 14:16 misc
-rw-r--r--  1 jake jake     31 2007-08-04 10:57 NEWS
drwxrwxrwx  6 jake jake   4096 2008-06-25 14:16 package
drwxrwxrwx 30 jake jake   4096 2008-06-25 14:16 plugins
-rw-r--r--  1 jake jake   3028 2007-08-04 10:57 PORTING
-rw-r--r--  1 jake jake  15788 2008-06-25 13:52 README
-rw-r--r--  1 jake jake    993 2007-09-20 15:48 README.BeOS
-rw-r--r--  1 jake jake   6919 2007-08-04 10:57 README.DEVC++
-rw-r--r--  1 jake jake   2719 2007-08-04 10:57 README.IRIX
-rw-r--r--  1 jake jake   2957 2007-08-04 10:57 README.Linux
-rw-r--r--  1 jake jake   2248 2007-09-20 15:48 README.MacOSX
-rw-r--r--  1 jake jake   6049 2007-09-20 15:48 README.MINGW32
-rw-r--r--  1 jake jake    803 2007-08-04 10:57 README.SDL
-rw-r--r--  1 jake jake   3287 2007-08-04 10:57 README.SOLARIS
-rw-r--r--  1 jake jake    238 2007-08-04 10:57 README.UNIX
-rw-r--r--  1 jake jake   3119 2008-04-06 01:31 README.WIN32
-rw-r--r--  1 jake jake   3150 2007-09-20 15:48 README.XMINGW
-rw-r--r--  1 jake jake     31 2007-08-04 10:57 RELNOTES
drwxrwxrwx 19 jake jake   4096 2008-06-25 14:16 src
-rw-r--r--  1 jake jake  13060 2007-12-07 18:20 TODO
drwxrwxrwx  5 jake jake   4096 2008-06-25 14:16 tools
drwxrwxrwx  4 jake jake   4096 2008-06-25 14:16 win32

---

### Post by taurus on 2009-03-13
You can have a look at the README.Linux and INSTALL 

```
more README.Linux
(Hit the Space key for the next 24 lines.)
more INSTALL
```
but looks like you have to build it first.

```
./configure
```

---

### Post by r0k on 2009-03-13
configure: error: libcurl is required. You must install it. See [http://curl.haxx.se/](http://curl.haxx.se/)

im at the site witch file type do i need??
 curl 7.19.4, Released on the 3rd of March 2009.

    curl-7.19.4.tar.gz (gpg) (mirror) (metalink)
    curl-7.19.4.tar.bz2 (gpg) (mirror) (metalink)
    curl-7.19.4.zip (gpg) (mirror) (metalink)
    curl-7.19.4.tar.lzma (gpg) (mirror) (metalink) 

Recommended libraries curl can or might use.

---

### Post by taurus on 2009-03-13
Fire up synaptic and type in _libcurl_ in **Search**.  Then, install it.

---

### Post by r0k on 2009-03-13
where do i find synaptic? just to let you know im not just relying on you to teacH me linux im reading a tutorial also! but i would like to get this game running so i can take breaks! so your help is apreciated!

---

### Post by r0k on 2009-03-13
i sucessfully installed libcurl without synaptic! i would still like to know about synaptic though

---

### Post by r0k on 2009-03-13
back to bz flag! i confugred it then typed make and this is what i got

jake@jake-desktop:~/Desktop/bzflag-2.0.12$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by r0k on 2009-03-13
jake@jake-desktop:~/Desktop/bzflag-2.0.12$ ls -la
total 1836
drwxrwxrwx 15 jake jake   4096 2009-03-13 14:58 .
drwxr-xr-x  5 jake jake   4096 2009-03-13 14:42 ..
-rw-r--r--  1 jake jake 272814 2008-06-25 14:14 aclocal.m4
-rw-r--r--  1 jake jake   7234 2007-08-04 10:57 AUTHORS
-rw-r--r--  1 jake jake    704 2007-09-10 18:10 authors.xml
-rwxr-xr-x  1 jake jake  45148 2007-09-20 15:48 autogen.sh
-rw-r--r--  1 jake jake   6587 2007-08-04 10:57 BUGS
-rw-r--r--  1 jake jake   3111 2008-06-25 14:15 bzflag.info
-rw-r--r--  1 jake jake   3114 2008-04-06 01:31 bzflag.info.in
-rw-r--r--  1 jake jake    492 2008-06-25 14:15 bzflag.lsm
-rw-r--r--  1 jake jake    495 2007-08-04 10:57 bzflag.lsm.in
-rw-r--r--  1 jake jake   2191 2008-06-25 14:15 bzflag.spec
-rw-r--r--  1 jake jake   2194 2008-04-06 01:31 bzflag.spec.in
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 BZFlag.xcodeproj
-rw-r--r--  1 jake jake  50737 2008-06-25 13:59 ChangeLog
-rw-r--r--  1 jake jake  35774 2009-03-13 14:58 config.log
-rwxr-xr-x  1 jake jake 905246 2008-06-25 14:14 configure
-rw-r--r--  1 jake jake  27769 2008-06-25 14:00 configure.ac
-rw-r--r--  1 jake jake  26420 2007-08-25 19:54 COPYING
drwxrwxrwx  4 jake jake   4096 2008-06-25 14:16 data
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 debian
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 Dev-C++
-rw-r--r--  1 jake jake  17533 2008-06-20 18:05 DEVINFO
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 include
-rw-r--r--  1 jake jake   9416 2007-08-04 11:11 INSTALL
-rwxr-xr-x  1 jake jake 211618 2009-03-13 14:58 libtool
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 m4
-rw-r--r--  1 jake jake   1239 2008-06-21 16:52 Makefile.am
-rw-r--r--  1 jake jake    275 2008-04-06 01:31 Makefile.common
-rw-r--r--  1 jake jake  21821 2008-06-25 14:14 Makefile.in
drwxrwxrwx  2 jake jake   4096 2008-06-25 14:16 man
drwxrwxrwx  3 jake jake   4096 2008-06-25 14:16 misc
-rw-r--r--  1 jake jake     31 2007-08-04 10:57 NEWS
drwxrwxrwx  6 jake jake   4096 2008-06-25 14:16 package
drwxrwxrwx 30 jake jake   4096 2008-06-25 14:16 plugins
-rw-r--r--  1 jake jake   3028 2007-08-04 10:57 PORTING
-rw-r--r--  1 jake jake  15788 2008-06-25 13:52 README
-rw-r--r--  1 jake jake    993 2007-09-20 15:48 README.BeOS
-rw-r--r--  1 jake jake   6919 2007-08-04 10:57 README.DEVC++
-rw-r--r--  1 jake jake   2719 2007-08-04 10:57 README.IRIX
-rw-r--r--  1 jake jake   2957 2007-08-04 10:57 README.Linux
-rw-r--r--  1 jake jake   2248 2007-09-20 15:48 README.MacOSX
-rw-r--r--  1 jake jake   6049 2007-09-20 15:48 README.MINGW32
-rw-r--r--  1 jake jake    803 2007-08-04 10:57 README.SDL
-rw-r--r--  1 jake jake   3287 2007-08-04 10:57 README.SOLARIS
-rw-r--r--  1 jake jake    238 2007-08-04 10:57 README.UNIX
-rw-r--r--  1 jake jake   3119 2008-04-06 01:31 README.WIN32
-rw-r--r--  1 jake jake   3150 2007-09-20 15:48 README.XMINGW
-rw-r--r--  1 jake jake     31 2007-08-04 10:57 RELNOTES
drwxrwxrwx 19 jake jake   4096 2008-06-25 14:16 src
-rw-r--r--  1 jake jake  13060 2007-12-07 18:20 TODO
drwxrwxrwx  5 jake jake   4096 2008-06-25 14:16 tools
drwxrwxrwx  4 jake jake   4096 2008-06-25 14:16 win32

---

### Post by taurus on 2009-03-13
> **r0k said:**
> back to bz flag! i confugred it then typed make and this is what i got

jake@jake-desktop:~/Desktop/bzflag-2.0.12$ make
make: *** No targets specified and no makefile found.  Stop.

Bet ./configure failed somewhere.  Can you post at least the last 20 lines of the output after you rerun ./configure from a terminal?

```
./configure
```

---

### Post by ubuntu27 on 2009-03-13
Hello rOk. Welcome to the Ubuntu Forums.

In Ubuntu and many other Linux distribution (distro in short) uses **repositories**. A repository is like a library of programs where many software are stores. All you have to do it to point or mark the package name that you want to install and it will automatically download from the repositories and install it.

There are many ways to do that. 

With the [Terminal]("http://www.psychocats.net/ubuntu/terminal") (Found in Applications/Accessories/Terminal]:

Type
**sudo apt-get install name** where "name" is the name of the package that you want to install.

By the way, bzflag is in the repository, so let's use that as an example:

```
sudo apt-get install bzflag
```

type your password and press enter.



Another way to install is using Synaptic Package Manager. 
It is located at System menu/Administration/Synaptic Package Manager

Once you open Synaptic, just look for the program that you want by clicking on search.

Mark the packages, and click on "Apply"


That's it :)


If you want more informaation, or you need steo by step instruction with screenshots. Visit:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

