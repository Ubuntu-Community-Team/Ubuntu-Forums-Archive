---
title: "How to compile emacs in terminal"
date: 2008-09-07
forum: General Help
---

### Post by sheepop39 on 2008-09-07
I can't seem to compile emacs in Terminal. So in Terminal go to the directory in which emacs is in and I type ./configure as it said it the install manual, so I hit enter and I get this 

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

anyone have idea what to do?

---

### Post by schauerlich on 2008-09-07
Have you installed build-essentials?

---

### Post by sheepop39 on 2008-09-07
what do you mean? I am sort of a noob at stuff like this

---

### Post by schauerlich on 2008-09-07
In order to compile something, you need to have build-essential installed.

```

sudo apt-get install build-essential

```

Now try compiling it.

---

### Post by oldos2er on 2008-09-07
> **sheepop39 said:**
> what do you mean? I am sort of a noob at stuff like this

 Is there some particular reason you're not installing emacs from the repositories?

---

### Post by sheepop39 on 2008-09-07
the reason I'm not doing it form the repositories is I wanted to try it out I guess

---

### Post by MaxIBoy on 2008-09-07
Install it from the repositories. A repository is just a central server with a bunch of installers on it, so you can download any available programs you want and install them without having to compile manually. Also, this way updates to the software are handled for you.


If you don't like it, just use "sudo apt-get remove {nameOfPackage}"


And with emacs, don't be turned off to it right away, just read the help file. With emacs, everything is done through keyboard commands, and the commands are different than they usually are.

---

### Post by sheepop39 on 2008-09-09
I get it compiled in Terminal now and compiles it the src directory in the emacs folder and now when I double click the executable it doesn't load so I right click and click execute and it still doesn't load. Anyone have an idea what to do

---

### Post by whitethorn on 2008-09-09
Well normally when you want to compile a package there are 3 steps

1) Compiling
```
./configure
```
2) Making
```
sudo make
```
3) installing
```
sudo make install
```

Problem is, when you install it this way, it won't show up in Synaptic and removing it later is a bit of a hassle.  One way to get around this is to use a program called checkinstall.

```
sudo apt-get install checkinstall
```

This program installs the program you compiled and puts it into Synaptic so you can uninstall it using synaptic.  To use this program replace the third step with

3) ```
sudo checkinstall
```

The other way to uninstall it (sudo make install) is to keep the source file you compiled, and then when you want to uninstall you have to run
```
sudo make uninstall
``` 

See the problem with this, when you compile and install a lot of programs in this way, you have a problem of updating and keeping track of where everything is.  That's the big advantage of using Synaptic, which does everything for you.

---

### Post by sheepop39 on 2008-09-09
thanks for replying

when I type make I get this 

cd lib-src; make all  \
          CC='gcc' CFLAGS='-g -O2 -Wno-pointer-sign ' CPPFLAGS='-D_BSD_SOURCE  ' \
          LDFLAGS='-Wl,-znocombreloc' MAKE='make'
make[1]: Entering directory `/home/john/Downloads/emacs-22.2/lib-src'
make[1]: *** No rule to make target `/home/john/Downloads/emacs-22.2/lib-src/rcs2log', needed by `rcs2log'.  Stop.
make[1]: Leaving directory `/home/john/Downloads/emacs-22.2/lib-src'
make: *** [lib-src] Error 2

and when I type make install I get this

cd lib-src; make all  \
          CC='gcc' CFLAGS='-g -O2 -Wno-pointer-sign ' CPPFLAGS='-D_BSD_SOURCE  ' \
          LDFLAGS='-Wl,-znocombreloc' MAKE='make'
make[1]: Entering directory `/home/john/Downloads/emacs-22.2/lib-src'
make[1]: *** No rule to make target `/home/john/Downloads/emacs-22.2/lib-src/rcs2log', needed by `rcs2log'.  Stop.
make[1]: Leaving directory `/home/john/Downloads/emacs-22.2/lib-src'
make: *** [lib-src] Error 2



I wonder if I installed the build essentials incorrectly

---

### Post by whitethorn on 2008-09-10
I don't really know without trying myself, did you make sure you got the all the dependencies? You should read the README and follow the instructions in there.

---

### Post by gaussian on 2008-09-10
One hint: when trying to compile a package that has an existing Ubuntu package (e.g. "You Really Need the Newest Version"), best thing to do first is to do

```

apt-get build-dep nameofpackage

```

If you are lucky this is all you need to do for getting the right dependencies. If the newer version depends on libraries that are newer than the currently available ones then you could be into a very messy situation.

---

