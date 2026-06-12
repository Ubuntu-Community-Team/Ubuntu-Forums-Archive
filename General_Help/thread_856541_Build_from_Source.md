---
title: "Build from Source"
date: 2008-07-11
forum: General Help
---

### Post by carl_pr on 2008-07-11
first i downloaded amsn source code because i try to install it using add/remove but they have a little more older version (0.97) 

so when i put in the terminal the ./configure it give me this error. what do i need to install and how for this to work.


[IMG]http://img141.imageshack.us/img141/1561/screenshotxs0.png[/IMG]

---

### Post by oldos2er on 2008-07-11
Type "sudo aptitude install build-essential" in a terminal. You need this package in order to compile source.

---

### Post by Elfy on 2008-07-11
Could you please use the manage attachments tool to link screenshots - some people don't have bb :)

---

### Post by carl_pr on 2008-07-11
ok thanks :KS

---

### Post by carl_pr on 2008-07-11
sorry for the screenshot lol too big, but now i try ./configure again and this is what i get


```

carlos@carlos-desktop:~/Downloads/amsn-0.97.1$ ./configure
checking for prefix by checking for wish... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev


```

---

### Post by atomkarinca on 2008-07-11
Try this:

```
sudo apt-get install tcl-dev
```

---

### Post by carl_pr on 2008-07-11
ok i did the previous command thanks but no i get this lol

blah im about to give up

```

checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... configure: error: Unable to find Tk directory or Tk package is not tk-dev

```

---

### Post by nikgare on 2008-07-11
Then you may need to follow the instructions here:
[http://www.amsn-project.net/forums/viewtopic.php?t=4958](http://www.amsn-project.net/forums/viewtopic.php?t=4958)

---

### Post by carl_pr on 2008-07-11
more crazy commands, blah i think ill give up

---

### Post by carl_pr on 2008-07-11
i solved the previous, now i get this


```

checking for png.h... yes
checking for jpeg_CreateDecompress in -ljpeg... no
configure: error: libjpeg is required


```

---

### Post by comandrei on 2008-07-11
```

sudo apt-get install libjpeg62-dev

```

---

### Post by mc4man on 2008-07-11
two things, amsn is available from synaptic if that version is okay you'll save some aggravation.
Otherwise I'd do this
First install amsn, that will satisfy your install dependencies, you can uninstall it right after and before you compile and install your built version.
Also run this from terminal, may fill in what your missing
```
sudo apt-get build-dep amsn
```

Edit : sorry didn't notice you had already installed and  made _dumb_ assumption your where on hardy. I'd still run the build-dep anyway

---

