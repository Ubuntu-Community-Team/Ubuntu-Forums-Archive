---
title: "I don't even know where to start... KDevelop"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by terho on 2009-03-15
cd '/home/hudson/C++/helloworldprog/debug/./src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k helloworldprog
linking helloworldprog (g++)
../libtool: line 832: X--tag=CXX: command not found
../libtool: line 865: libtool: ignoring unknown tag : command not found
../libtool: line 832: X--mode=link: command not found
../libtool: line 999: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 1000: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
gcc: no input files
gcc: no input files
gcc: no input files
gcc: no input files
../libtool: line 2237: X-O0: command not found
../libtool: line 2237: X-g3: command not found
../libtool: line 2406: Xhelloworldprog: command not found
X: user not authorized to run the X server, aborting.
../libtool: line 2418: Xhelloworldprog: command not found
../libtool: line 2426: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make: *** [helloworldprog] Error 1
*** Exited with status: 2 ***


Any suggestions are welcome I tried to chown .Xauthority for my user didn't seem to help (I had read something about it in another post). I'll reverse the command. Unless I need it.

---

### Post by articfox on 2009-05-01
See this thread: [http://ubuntuforums.org/showthread.php?t=945424&highlight=kdevelop+libtool](http://ubuntuforums.org/showthread.php?t=945424&highlight=kdevelop+libtool)

---

