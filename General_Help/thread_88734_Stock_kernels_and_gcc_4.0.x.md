---
title: "Stock kernels and gcc 4.0.x"
date: 2005-11-10
forum: General Help
---

### Post by Malibyte on 2005-11-10
Hi all -

I'm running 5.10 with the stock 2.6.12-9-386 kernel at the moment.  Gcc 4.0.2 is also installed.

I need to install VMWare Workstation on this machine.  There is, of course, no precompiled module for this kernel included, so it needs to compile its own.  However, the stock kernel was compiled with gcc 3.4.x, and I have 4.0.2 installed.  The VMware install script barfs on this, giving me the choice of doing a full kernel recompile with gcc 4, or install gcc 3.4.x and trying again (can't find the latter in the repositories (at least, Synaptic can't)).

My question is...are the new kernels going to be compiled with gcc 4 anytime soon (there's no real urgency to my installing VMware, as it's running on my Mandrake box, and I really don't feel like going through and doing a make config and kernel recompile right now)?

Or...is there a way to fool the script into thinking that 4.0 is really 3.4...I think I remember having to do this when we went from 2.9 to 3.0....?  :D

Thanks - Bob

---

### Post by matthew on 2005-11-10
You could install gcc3.4 as it is also in the repositories and compile your modules with it...just a thought.

---

### Post by RAOF on 2005-11-10
It's unlikely that there will **be** new kernels anytime soon (for breezy), if there are, they'd still be compiled with gcc3.4.  Any new kernels will just contain security fixes, backported from the latest vanilla kernels.

You can install gcc-3.4 with ```
sudo apt-get install gcc-3.4
```, and the export CC=gcc-3.4.  That should make the VMWare installer use gcc3.4 as the default compiler.

---

### Post by Lambert on 2005-11-10
breezy is frozen with no upgrades accept security updates. the next release will have the latest stable kernel.

gcc 3.4 should be in the repositories though. Check and make sure you have universe and multiverse set up. sudo gedit /etc/apt/sources.list

---

### Post by Malibyte on 2005-11-11
Not new to Linux, but relatively new to the Debian distro tree; started with  RedHat 4.x and Mandrake since 6.x.

Anyway, I got gcc-3.4 installed and am past that hurdle, but the compile fails because it's missing "cc1plus". 

gcc-3.4: installation problem, cannot exec `cc1plus': No such file or directory
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

From what I can find (Google, and the VMware support forums), this should either be part of one of the gcc packages or gcc-c++ (it doesn't seem to be, as there are no such files anywhere on the system; I have gcc-c++ and all of the usual gcc-3.4 (and -4.0) packages installed).

Can somebody clue me in to which package contains it?  Tried apt-cache search, no joy either.

Thanks ... Bob

---

### Post by RAOF on 2005-11-11
The g++-3.4 package should contain it, I think.  I'm not quite sure why it wasn't installed with the rest of gcc-3.4.

---

### Post by Malibyte on 2005-11-11
[QUOTE=RAOF]The g++-3.4 package should contain it, I think.  I'm not quite sure why it wasn't installed with the rest of gcc-3.4.[/QUOTE]


Nope...this is what's in the g++-3.4 package:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gcc-3.4-base
/usr/share/doc/gcc-3.4-base/C++
/usr/share/doc/gcc-3.4-base/C++/README.C++
/usr/share/doc/gcc-3.4-base/C++/changelog.gz
/usr/share/man
/usr/share/man/man1
/usr/bin
/usr/bin/g++-3.4
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/3.4.5
/usr/lib/gcc/i486-linux-gnu/3.4.5/cc1plus
/usr/share/doc/g++-3.4
/usr/share/man/man1/g++-3.4.1.gz
/usr/share/man/man1/i486-linux-gnu-g++-3.4.1.gz
/usr/bin/i486-linux-gnu-g++-3.4

:confused:

---

### Post by RAOF on 2005-11-11
[QUOTE=Malibyte]Nope...this is what's in the g++-3.4 package:
...
/usr/lib/gcc/i486-linux-gnu/3.4.5
**/usr/lib/gcc/i486-linux-gnu/3.4.5/cc1plus**
/usr/share/doc/g++-3.4
...[/QUOTE]
There it is :)

---

### Post by Malibyte on 2005-11-11
[QUOTE=RAOF]There it is :)[/QUOTE]

oops...damn, it's been a long day.  :rolleyes:   Sorry 'bout that.

Compile worked.  Thanks for the help, guys.  :) 

Zzzzzzzzzzzzzzzzzzzz.  :cool:

---

