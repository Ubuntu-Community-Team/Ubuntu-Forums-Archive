---
title: "Alien Error Installing ATI Fglrx"
date: 2005-03-03
forum: Hardware &amp; Laptops
---

### Post by kidrock on 2005-03-03
Total noob to Linux... encounter this error while converting the rpm to deb

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:/mnt/HDA-6 # sudo alien fglrx.rpm
mkdir: cannot create directory `fglrx_4_3_0-8.10.19': File exists
mkdir: cannot create directory `fglrx_4_3_0-8.10.19/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/fglrx-4-3-0
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
dh_gencontrol
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
dpkg-deb: building package `fglrx-4-3-0' in `../fglrx-4-3-0_8.10.19-2_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: fglrx_4_3_0-8.10.19: No such file or directory

Any help would be appreciated...

---

### Post by kidrock on 2005-03-03
Someone help please..................... :-({|=

---

### Post by alastair on 2005-03-04
Check :

a) when you are running the command above, no other package tool is running (apt,dpkg,synaptic etc.)

b) You are running as "root" i.e.

sudo ...<command>...

---

### Post by kidrock on 2005-03-04
Same error dude....

root@ubuntu:/mnt/HDA-6 # sudo alien -d fglrx.rpm
mkdir: cannot create directory `fglrx_4_3_0-8.10.19': File exists
mkdir: cannot create directory `fglrx_4_3_0-8.10.19/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/fglrx-4-3-0
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
dh_gencontrol
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
dpkg-deb: building package `fglrx-4-3-0' in `../fglrx-4-3-0_8.10.19-2_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: fglrx_4_3_0-8.10.19: No such file or directory

---

### Post by kidrock on 2005-03-04
Okay I made the deb package....problem...was convertng it in a fat32 partition :(

now another problem ....encounter following error during the make.sh process

root@ubuntu:/lib/modules/fglrx/build_mod # sudo sh make.sh
make.sh: line 1: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: line 1: gcc: command not found
/bin/sh: line 1: gcc: command not found
ln: `./libfglrx_ip.a.GCC': File exists
make: *** [libfglrx_ip.a.GCC] Error 1
build failed with return value 2
root@ubuntu:/lib/modules/fglrx/build_mod #

---

### Post by kidrock on 2005-03-04
this is the error now


root@ubuntu:/lib/modules/fglrx # sudo sh make_install.sh - creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.8.1-3-386/kernel/drivers/video/fg lrx.ko): Operation not permitted
failed.
root@ubuntu:/lib/modules/fglrx #

---

