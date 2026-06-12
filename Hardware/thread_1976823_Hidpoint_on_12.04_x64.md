---
title: "Hidpoint on 12.04 x64"
date: 2012-05-09
forum: Hardware
---

### Post by bluelord_ro on 2012-05-09
Hi,
I have folowed this post [[link]]("http://www.ubuntuforums.org/showthread.php?t=1913356&highlight=hidpoint") but i still have libraries problems:
> Do you wish to continue with the Installation? [Y/n] and hit enter y
*****************************************************************************
*                                                                           *
* To run HIDPoint on a 64 bit OS, you first need to install 32 bit libraries*
*                                                                           *
*****************************************************************************
libtiff does not exist
Gathering System information and generating a log
chown: missing operand after `/home/bluelord/.hidpoint/'
Try `chown --help' for more information.
Launching HIDPoint Installer
./hidpointsetup: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory


> sudo apt-get install libpng3 libtiff4 ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtiff4 is already the newest version.
ia32-libs is already the newest version.
libpng3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


What i need more to install?

Thanks :)

---

### Post by ralmond on 2012-07-27
This appears to be a problem with ia32-libs not creating the proper symlink.  You should be able to fix it with the following steps:

$ cd /usr/lib/i386-linux-gun/
$ sudu ln -s /lib/i386-linux-gnu/libpng12.so.0 libpng.so.3

The installer then launched a graphical window, but mentioned that it was compiled against a different version of the kernel, so I didn't not install.  If you do and it works, let me know.

Good luck.

---

### Post by appalbarry on 2012-09-11
Typos in message above - should be:

$ cd /usr/lib/i386-linux-gnu/
$ sudo ln -s /lib/i386-linux-gnu/libpng12.so.0 libpng.so.3

Otherwise this worked - finally got HIDpoint installer to run!

---

### Post by garzaj on 2012-10-28
I got it to run on Ubuntu 12.10, but it doesn't really work.

---

### Post by johnaaronrose on 2013-06-21
> **appalbarry said:**
> Typos in message above - should be:

$ cd /usr/lib/i386-linux-gnu/
$ sudo ln -s /lib/i386-linux-gnu/libpng12.so.0 libpng.so.3

Otherwise this worked - finally got HIDpoint installer to run!

Just tried the above on Ubuntu 12.04 64 bit. When I did "sudo ./hidpoint", it no longer got the error message about libpng.so but it got "libpng does not exist". However, it did enter the hidpoint gui window & that finished OK. I then tried hidpoint from the Dash, which displayed the Hidpoint Configuration window but it did not show my connected Logitech Cordless Optical Trackman mouse as a connected device: I pressed the connect buttons on the mouse & wireless unit before & during this stage. 

PS before doing the above, I uninstalled the libpng package. Is that the cause?

Help!

---

