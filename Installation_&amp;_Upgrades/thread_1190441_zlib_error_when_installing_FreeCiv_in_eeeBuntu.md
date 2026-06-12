---
title: "zlib error when installing FreeCiv in eeeBuntu"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by bacchant on 2009-06-17
Hello all,

This was just posted on Beginner Talk but got no response, so I'm moving it here.

I've just recently installed eeeBuntu Standard on a eee 1000. Everything's great, except that I can't seem to create a makefile for a release version of FreeCiv 2.1.9. After running "./configure" from the game directory, the log finishes with:[INDENT]checking for gzgets in -lz... no
configure: error: Could not find zlib library.
[/INDENT]I did when you might expect and ran "aptitude search zlib", finding the following: [INDENT]i   libcompress-raw-zlib-perl
i   libcompress-zlib-perl 
i   libio-compress-zlib-perl 
v   libio zlib-perl 
i   zlib1g 
[/INDENT]Next ran "sudo apt-get install zlib1g" since this seemed the most likely suspect judging from lots of forum comments. Verified that zlib was installed, both via Synaptic and by grepping /usr. It's there and it's installed. Of course, I wouldn't be writing this if ./configure worked after all this, and it doesn't. Same error, no change, so no makefile, so no game install.

I understant that zlib is an old problem, especially it seems with Ubuntu. The Question posted a recent thread in April here at [http://ubuntuforums.org/showthread.php?t=1122275&highlight=zlib1g+freeciv](http://ubuntuforums.org/showthread.php?t=1122275&highlight=zlib1g+freeciv), but what worked for him doesn't for me.

Anyone have any solution to getting FreeCiv's config to recognize my zlib? Or is there a different zlib that needs to be installed?

Thanks in advance!

---

### Post by lemming465 on 2009-06-18
The April FreeCiv thread you referenced suggested **sudo apt-get install zlib1g-dev** to install the development files, which adds a static (non-shared) version of the library (/usr/lib/libz.a) and include files such as /usr/include/zlib.h.  Have you installed *both* the zlib1g and zlib1g-dev packages?

---

