---
title: "Problem installing kzenexplorer-0.6"
date: 2008-11-11
forum: Hardware
---

### Post by bluehousemikie on 2008-11-11
I'm running Ubuntu 8.04 and am the proud owner of a new Zen Creative media player (4MB).

Like many other I've had difficulties getting Ubuntu to connect to it/mount it/talk to it.

I trawled the forums.  gnomad2 got me half way there: will connect to the Zen and can transfer files, but they don't appear on the Zen menus - the Zen can't find them.

So I tried installing kzenexplorer-0.6

I'm a beginner with Ubuntu, but used to work with Unix mainframes in a past life, so have a head start in playing in Terminal.

./configure gave me the following error:
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

So I try 

./configure --x-includes=//usr/include --x-libraries=//usr/lib
(as suggested in the installer readme)
and get

configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either

which is surprising because //usr/lib contains:
libXext.so.6
libXext.so.6.4.0

Any suggestions?

Alternatively is there a way that I can get kzenexplorer to appear in the list of applications available for adding under the Add/Remove button on the Applications menu?

:confused:

---

