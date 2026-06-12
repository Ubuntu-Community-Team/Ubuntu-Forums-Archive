---
title: "Problems using &quot;make&quot;"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by intheory on 2005-12-27
I've recently made my first real foray into running a Linux server with Ubuntu. We needed an internal wiki setup and so I setup Apache/PHP/MySQL on an old Dell box, setup MediaWiki, and all seems to be okay so far.

I'm trying to add some additional packages to the wiki, namely a WYSIWYG HTML editor, which requires me to use the "make" command.*  When I ran this initially, it failed repeatedly but I wasn't sure why.  So just for grins, I did "apt-get install make", and lo and behold, apparently it wasn't installed before.  So it installed make, but still it doesn't work.  It just gives a generic error, and I don't know how to get more info about why it is failing, but I hope someone can give some advice.  If you need more info let me know and I'll hop over to that box and post it.  Thanks in advance...

(*[http://meta.wikimedia.org/wiki/WYSIWYG_editor](http://meta.wikimedia.org/wiki/WYSIWYG_editor) is what I'm following to install this add-on, in case that matters)

---

### Post by kaamos on 2005-12-27
Can't really give any specific help, but this is for sure a good idea
```
sudo apt-get install build-essential
```

---

### Post by intheory on 2005-12-28
Thanks for the suggestion kaamos.  I did that, which added another 8 packages or so, but still no dice. here's the error message (same message for various packages)

  CPAN.pm: Going to build K/KA/KANE/Archive-Tar-1.26.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

---

### Post by qbxk on 2005-12-29
I don't know how much experience you have with CPAN (the cmd-line tool, not the repository) - but i've found that it... how do i put this delicately? doesn't work sometimes.

..when that happens (not infrequently) I either get the tar.gz file myself or i cd into ~/.cpan/build/ and then into the module directory i'm going for and do the standard:
```
sudo perl Makefile.PL; sudo make; sudo make install;
```

(i like to sudo all three so that i can enter my password at the start and then go distract myself with something else until it's done (ALL done), rather than entering the password .. "later", and if you, reader, know: just how insecure is that? i'm curious, really)

and while CPAN would kindly go get any modules the one you're building, install them, and then fall back to that one - that' really only an ideal.  if it fails, you may have to do your dependancies in this same fashion, a tiresome and tedious process i know (but less so than writing the modules all yourself!)

---

### Post by intheory on 2005-12-29
Thanks for the tip qbxk: I tried that method and it worked.  Maybe something with CPAN rather than make. I think this will get me somewhere.  :)

---

### Post by roinge on 2006-01-09
I have been trying to install the [ X11::GUITest]("http://search.cpan.org/~ctrondlp/X11-GUITest-0.20/GUITest.pm") perl package without success...

First I tried the CPAN (I have successfully installed other CPAN-packages before):
```
 _cpan>_ install X11::GUITest 
```

Then I got this error message:
...
**/usr/bin/ld: kan inte hitta -lXtst           *(can't find -lXtst)***
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/X11/GUITest/GUITest.so] Fel 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
...

later when I tried to download it manually and do:
[QUOTE=qbxk]
..when that happens (not infrequently) I either get the tar.gz file myself or i cd into ~/.cpan/build/ and then into the module directory i'm going for and do the standard:
```
sudo perl Makefile.PL; sudo make; sudo make install;
```
[/QUOTE]

I still got the same error:

...
me@mycomp:~/X11-GUITest-0.20$ sudo perl Makefile.PL; sudo make; sudo make install;
Writing documentation for X11::GUITest
Checking if your kit is complete...
Looks good
Writing Makefile for X11::GUITest
cp GUITest.pm blib/lib/X11/GUITest.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  GUITest.xs > GUITest.xsc && mv GUITest.xsc GUITest.c
cc -c  -I/usr/X11R6/include -I/usr/X/include -Wall -O2   -DVERSION=\"0.20\" -DXS_VERSION=\"0.20\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -DNDEBUG GUITest.c
Running Mkbootstrap for X11::GUITest ()
chmod 644 GUITest.bs
rm -f blib/arch/auto/X11/GUITest/GUITest.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib GUITest.o  -o blib/arch/auto/X11/GUITest/GUITest.so   -L/usr/X11R6/lib -lX11 -lXtst -lXext
/usr/bin/ld: kan inte hitta -lXtst
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/X11/GUITest/GUITest.so] Fel 1
rm -f blib/arch/auto/X11/GUITest/GUITest.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib GUITest.o  -o blib/arch/auto/X11/GUITest/GUITest.so   -L/usr/X11R6/lib -lX11 -lXtst -lXext
**/usr/bin/ld: kan inte hitta -lXtst**     *(=can't find)*
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/X11/GUITest/GUITest.so] Fel 1
...

Are there any more nice Perl/CPAN/Ubuntu tricks to learn? I need this package to install the phone client in [Giantdisc]("http://www.giantdisc.org/concept/clients.php")

---

### Post by orengolan on 2007-06-28
I have similar problem when trying to Install X11::GUITest.

```

Writing Makefile for X11::GUITest
cp GUITest.pm blib/lib/X11/GUITest.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap GUITest.xs > GUITest.xsc && mv GUITest.xsc GUITest.c
cc -c -I/usr/X11R6/include -I/usr/X/include -Wall -O2 -DVERSION=\"0.21\" -DXS_VERSION=\"0.21\" -fPIC "-I/usr/lib/perl/5.8/CORE" -DNDEBUG -DX11_GUITEST_ALT_L_FALLBACK_META_L GUITest.c
GUITest.c: In function ‘XS_X11__GUITest_GetScreenDepth’:
GUITest.c:1715: warning: ‘scr_num’ may be used uninitialized in this function
GUITest.c: In function ‘XS_X11__GUITest_GetScreenRes’:
GUITest.c:1681: warning: ‘scr_num’ may be used uninitialized in this function
GUITest.c: In function ‘XS_X11__GUITest_GetRootWindow’:
GUITest.c:956: warning: ‘scr_num’ may be used uninitialized in this function
Running Mkbootstrap for X11::GUITest ()
chmod 644 GUITest.bs
rm -f blib/arch/auto/X11/GUITest/GUITest.so
cc -shared -L/usr/local/lib GUITest.o -o blib/arch/auto/X11/GUITest/GUITest.so \
-L/usr/X11R6/lib -lXtst -lXext -lX11 \

/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/X11/GUITest/GUITest.so] Error 1
/usr/bin/make -- NOT OK
Running make test
Can't test without successful make
Running make install
make had returned bad status, install seems impossible

```

Any ideas?

---

### Post by shotgunefx on 2007-07-20
I know this is ancient, but I had the same problem (which is how I found this post) so I'll answer for posterity ;)

On my system, libXtst was under /usr/lib/libXtst.so.6, I just symlinked to it as libXtst.so and changed the Makefile to look in /usr/lib as well as /usr/local/lib (where ld was looking) and it worked fine.

---

### Post by vsu91 on 2008-06-23
try:

sudo apt-get install xorg-dev libc6-dev make wacom-tools
sudo perl -e ‘$ENV{FTP_PASSIVE} = 1; shell’ -MCPAN
cpan> install Bundle::CPAN
cpan> force install X11::GUITest

---

