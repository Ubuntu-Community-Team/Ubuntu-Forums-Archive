---
title: "[SOLVED] Install from source, please help!"
date: 2008-10-06
forum: General Help
---

### Post by status001 on 2008-10-06
[http://ubuntuforums.org/showthread.php?t=496132](http://ubuntuforums.org/showthread.php?t=496132)

[FONT="Century Gothic"][I]The above link gives simple way to install packages from source. But, every time I try to install any package from source the ./configure command shows an error. I tried to install many packages from their sources. But all I have the same error.
For example I download a source of a little game called jester from Ubuntu launchpad. I copied it into my home folder and tried to install. I paste here what my terminal says,[/I][/FONT]

status001@status001-desktop:~$ tar xvzf jester_1.0.orig.tar.gz 
jester-1.0/
jester-1.0/Makefile
jester-1.0/jester.c
jester-1.0/jester.h
jester-1.0/jester.6
jester-1.0/COPYING
jester-1.0/README
status001@status001-desktop:~$ cd jester-1.0/
status001@status001-desktop:~/jester-1.0$ ./configure
bash: ./configure: No such file or directory
status001@status001-desktop:~/jester-1.0$ 

[FONT="Century Gothic"]*What is my problem? I also tried using "auto-apt run ./configure" command. It gives me:*[/FONT]

status001@status001-desktop:~/jester-1.0$ auto-apt run ./configureEntering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
E: Exec ./configure failed, auto-apt failed
status001@status001-desktop:~/jester-1.0$ 

[FONT="Century Gothic"][I]
What is this problem with ./configure command at all!!! Please give a solution[/I][/FONT]

---

### Post by geirha on 2008-10-06
Not all source packages contain configure-scripts, and in this case it doesn't. Read the README file it contains, it should explain how to build and install for your system.

---

### Post by status001 on 2008-10-07
I download this game jester from
[https://launchpad.net/ubuntu/+source/jester/1.0-8](https://launchpad.net/ubuntu/+source/jester/1.0-8)
I'm posting here my terminal log here:

[FONT="Trebuchet MS"]status001@status001-desktop:~$ tar xvzf jester_1.0.orig.tar.gz 
jester-1.0/
jester-1.0/Makefile
jester-1.0/jester.c
jester-1.0/jester.h
jester-1.0/jester.6
jester-1.0/COPYING
jester-1.0/README
status001@status001-desktop:~$ cd jester-1.0/
status001@status001-desktop:~/jester-1.0$ gedit README &
[/FONT]

**README:**
[I]README file for jester 1.0

jester is an X-based board game similar to Othello.  It can be played
head-to-head on the console or by a single player against the
computer.  jester allows you to waste valuable time that could
otherwise be spent playing Solitaire.

REQUIREMENTS

jester requires only the basic X libraries (libX11); it does not use
any toolkits.  If you want to build jester you need an ANSI C
compiler, such as gcc.

INSTALLATION

Untar the distribution.  It should create the directory jester-1.0 and
create the files:

COPYING
README
Makefile
jester.6
jester.c
jester.h

Edit jester-1.0/Makefile for your site.

Type "make".  You should produce an executable named "jester".  Verify
that the program is working and then type "make install" as root.
This will install jester in /usr/local/bin/ and the man page in
/usr/local/man/man6.

If you have any problems or comments please mail [email]mattg@oz.net[/email]

jester 1.0 is Copyright (C) 1998 by Matthew Grossman and is
distributed under the terms of the GNU General Public License.  See
the file COPYING for further details.

Enjoy![/I]


**Terminal:**
status001@status001-desktop:~/jester-1.0$ gedit Makefile &

**_Makefile:_**
[I]# makefile for jester

CC = gcc -Wall -O2
#CC = gcc -Wall -g
LIBS = -L/usr/X11R6/lib -lX11
INSTALLDIR = /usr/local

jester: jester.c jester.h
	$(CC) -o jester jester.c $(LIBDIR) $(LIBS)

install: jester jester.6
	install jester $(INSTALLDIR)/bin/jester
	install -m 644 jester.6 $(INSTALLDIR)/man/man6/jester.6

clean:
	rm -f jester[/I]


**_Terminal:_**
status001@status001-desktop:~/jester-1.0$ make
gcc -Wall -O2 -o jester jester.c  -L/usr/X11R6/lib -lX11
jester.c: In function &#8216;handle_events&#8217;:
jester.c:107: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;proper_function&#8217;:
jester.c:133: error: label at end of compound statement
jester.c: In function &#8216;square_expose&#8217;:
jester.c:285: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;square_buttonpress&#8217;:
jester.c:445: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;clean_up_stuff&#8217;:
jester.c:537: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:542: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:545: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:548: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:551: warning: dereferencing type-punned pointer will break strict-aliasing rules
make: *** [jester] Error 1
status001@status001-desktop:~/jester-1.0$ 



What is my problem?

---

### Post by geirha on 2008-10-07
Apparently a bug in the source code ... Are there any reason why you want to build this yourself, instead of installing it from the repositories? 

That error you get is probably fixed by the patch jester_1.0-8.diff.gz . Either download and apply that, or use apt-get which will download the source and patch it for you.

```
apt-get source jester
```

---

### Post by status001 on 2008-10-07
*Ok, then what to do? Now I have 3 files: *.tar.gz, *.diff.gz, *.dsc. What'll I do with *.diff.gz? Please explain. Thanks.*

---

### Post by geirha on 2008-10-07
If you did ```
apt-get source jester
``` the diff is allready applied, and it should compile when you run ```
make
```

---

### Post by status001 on 2008-10-09
*Ok, I got the error msg, so I started from the begining. Here is my terminal log:*

```
ediamin@ediamin-desktop:~$ apt-get source jester 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 19.1kB of source archives.
Get:1 http://us.archive.ubuntu.com hardy/universe jester 1.0-8 (dsc) [674B]
Get:2 http://us.archive.ubuntu.com hardy/universe jester 1.0-8 (tar) [15.6kB]
Get:3 http://us.archive.ubuntu.com hardy/universe jester 1.0-8 (diff) [2881B]
Fetched 19.1kB in 2s (7127B/s)
gpg: Signature made Sun 12 Aug 2007 04:37:07 AM BDT using RSA key ID EBC11B01
gpg: Can't check signature: public key not found
dpkg-source: extracting jester in jester-1.0
dpkg-source: unpacking jester_1.0.orig.tar.gz
dpkg-source: applying ./jester_1.0-8.diff.gz

ediamin@ediamin-desktop:~$ tar xvzf jester_1.0.orig.tar.gz 
jester-1.0/
jester-1.0/Makefile
jester-1.0/jester.c
jester-1.0/jester.h
jester-1.0/jester.6
jester-1.0/COPYING
jester-1.0/README

ediamin@ediamin-desktop:~$ cd jester-1.0/

ediamin@ediamin-desktop:~/jester-1.0$ make
gcc -Wall -O2 -o jester jester.c  -L/usr/X11R6/lib -lX11
jester.c: In function &#8216;handle_events&#8217;:
jester.c:107: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;proper_function&#8217;:
jester.c:133: error: label at end of compound statement
jester.c: In function &#8216;square_expose&#8217;:
jester.c:285: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;square_buttonpress&#8217;:
jester.c:445: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c: In function &#8216;clean_up_stuff&#8217;:
jester.c:537: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:542: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:545: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:548: warning: dereferencing type-punned pointer will break strict-aliasing rules
jester.c:551: warning: dereferencing type-punned pointer will break strict-aliasing rules
make: *** [jester] Error 1
ediamin@ediamin-desktop:~/jester-1.0$ 
```

[I]
Any solution, please.[/I]

---

### Post by geirha on 2008-10-09
> **status001 said:**
> 
```

dpkg-source: extracting jester in jester-1.0
dpkg-source: unpacking jester_1.0.orig.tar.gz
dpkg-source: applying ./jester_1.0-8.diff.gz

```


Notice what apt-get source does here, it extracts the source and applies the diff/patch. When you extract it again after that, you overwrite the patch.

Don't mind the gpg warning.

---

### Post by status001 on 2008-10-09
[FONT="Comic Sans MS"][I]Thank you so much **[SIZE="5"]geirha[/SIZE]**. I've installed it. I followed your instruction and still get an error msg while trying to use  "sudo make install". I figured out that in README file there is an extra folder name "man6" which was not in my system. So, I followed that directory and create a new folder with that man6. Tried again, and this time it works.

Thanks a lot[/I][/FONT]

---

