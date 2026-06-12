---
title: "[SOLVED] how do I get caller id from a modem?"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by newlinux on 2007-03-29
I've got an external voice modem that I would like to use to get caller id. It's been detected at /dev/ttyS0. Anybody know how I can get caller id information from the modem?

---

### Post by newlinux on 2007-04-01
For anyone who cares:
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=4836&highlight=caller](http://mysettopbox.tv/phpBB2/viewtopic.php?t=4836&highlight=caller)
[www.bah.org/~greg/tivo](www.bah.org/~greg/tivo)  

I basically modified this to work with my modem and caller id formatting. I originally modified this to use mythtvosd, but that often crashed all of my frontends (even when run directly from the commandline) and you can only see it during watching program with myth internal viewer (not during menus). Then I ended up using the supplied xyac code, modified elseed code and xosd and now this shows up on all my linux computers whether I'm using myth or not...

 Works great on all my linux computers.

---

### Post by t4thfavor on 2007-05-30
Would it be possible for you to send me this modified source, I have so far been unsuccessful in my attempt to modify the sources provided.  I am not running a Tivo ov any kind(Ubuntu Feisty), but would like to get caller-ID off of an old USR modem. I have tried all kinds of stuff with no luck.
Thanks,
Chance

---

### Post by jdogzilla on 2007-09-11
Hi, I'm trying to compile xosd and am running into the following error:

# ./configure
....
....
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for X... no
checking for gtk-config... no
checking for GTK - version >= 1.2.2... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: WARNING: *** GTK+ >= 1.2.2 not found ***
checking for XInitThreads in -lX11... no
configure: error: *** X11 not threadsafe ***

Can anyone help me get this compiled and let me know what I need to install on feisty to make this work?  Thanks:confused:

---

### Post by newlinux on 2007-09-11
I don't remember how I did this (it was so long ago). But I basically followed the instructions on the first link for doing this in Linux.  I don't think I had to compile xosd. I just installed the libxosd-dev, libxosd2, and xosd-bin packages. Then I compiled xyac and elseed. This was on edgy.

---

### Post by newlinux on 2007-09-11
> **t4thfavor said:**
> Would it be possible for you to send me this modified source, I have so far been unsuccessful in my attempt to modify the sources provided.  I am not running a Tivo ov any kind(Ubuntu Feisty), but would like to get caller-ID off of an old USR modem. I have tried all kinds of stuff with no luck.
Thanks,
Chance

Sorry this is so late, but I haven't been monitoring this thread, until I did a search for myth threads so i can help where I can and this one showed up with the new post. I'm running elseed of an edgy machine with a hardware serial modem. I only modified elseed.c and elseed.h a bit. I think the key things I changed where the caller ID formatting and modem initialization string in elseed.h, and maybe some small changes in elseed.c for formatting and logging. It took  a bit of looking at the output to get this figured out and working for me with my modem.

What kinds of things have you tried?

Attached are my files. CRAP. I just accidently deleted my very latest source. Oh well, at least I have the executable. But these are close to the last ones I used... I think I only changed logging format in these...

BTW, this even works with the windows xyac client. It's great.

---

### Post by jdogzilla on 2007-09-18
How do I compile the 2 elseed files?  Where do they go?

---

### Post by newlinux on 2007-09-18
Those files are just modified versions of the file that come in the first link I sent to work with how my callerID comes in and to log like I want it to log. You just follow those instructions. You will need to get an account on those forums first, I believe. But basically you download and uncompress the files, make sure the proper libraries are installed on your machine and just "make" them. You can untar them anywhere and run the elseed executable from anywhere. It is standalone. You will need to setup up the configuration in elseed.conf. Take a look at elseed.h to see/change where it expects the log and configuration file to be.

---

### Post by jdogzilla on 2007-12-06
When I try to compile elseed, I get the following errors on Ubuntu Gutsy

gcc  -c -I/usr/include/linux/dvb/ -g -Wall -O2 elseed.c
elseed.c: In function ‘main’:
elseed.c:67: warning: implicit declaration of function ‘SetupTextOSD’
elseed.c:218: warning: implicit declaration of function ‘FreeTextOSD’
elseed.c: In function ‘osdit’:
elseed.c:354: warning: implicit declaration of function ‘ClearOSD’
elseed.c:356: error: ‘MAX_CHAR_X’ undeclared (first use in this function)
elseed.c:356: error: (Each undeclared identifier is reported only once
elseed.c:356: error: for each function it appears in.)
elseed.c:358: warning: implicit declaration of function ‘DrawString’
elseed.c:362: warning: implicit declaration of function ‘DrawOSD’
elseed.c: In function ‘send_to_all_listeners’:
elseed.c:512: warning: pointer targets in passing argument 5 of ‘getsockopt’ differ in signedness
make: *** [elseed.o] Error 1

Any suggestions on getting this to work?

---

### Post by jdogzilla on 2008-01-03
Anybody?  Any suggestions?

---

