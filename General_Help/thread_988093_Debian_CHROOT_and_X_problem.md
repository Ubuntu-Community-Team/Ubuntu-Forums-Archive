---
title: "Debian CHROOT and X problem"
date: 2008-11-20
forum: General Help
---

### Post by Efrain Valles on 2008-11-20
Hello all, 

I am Currently trying to set up X in a Chroot environment for DEBIAN SID to test some debian packages I have built in my Ubuntu Box, I have read many guides from which I have pulled information from and applied here and there. I am mainly using [http://viral.media.mit.edu/wiki/tiki-index.php?page=Debian+chroot+environment](http://viral.media.mit.edu/wiki/tiki-index.php?page=Debian+chroot+environment). as I try to start X as suggested by this guide. I get

Inside my chroot env I edited 

/etc/X11/xdm/Xservers

from  

:0 local /usr/bin/X vt7 -dpi 100 -nolisten tcp

to
:0 local /usr/bin/X vt9 -dpi 100 -nolisten tcp

for it to be displayed on tty 9

it fails to load

then I changed the display to see if it worked

:1 local /usr/bin/X vt9 -dpi 100 -nolisten tcp

but once I try to start X don't get any output and once I check var/log/xmd.log

Thu Nov 20 11:55:38 2008 xdm error (pid 19939): server for display :0 can't be started, session disabled
Thu Nov 20 11:55:38 2008 xdm info (pid 19939): exiting
Thu Nov 20 12:00:16 2008 xdm info (pid 20487): starting
Thu Nov 20 12:00:16 2008 xdm info (pid 20487): starting X server on :1
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running


root@felicia:/# tail /var/log/Xorg.0.log
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

any suggestions or things I am overlooking here?

Thanks

---

