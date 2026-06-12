---
title: "Problem installing canon pixma ip1300 in 64 bit hardy."
date: 2008-08-29
forum: Hardware
---

### Post by immy123 on 2008-08-29
I tried to do what age6racer has told in this thread:
[http://ubuntuforums.org/showthread.php?t=563627](http://ubuntuforums.org/showthread.php?t=563627)

But, when I was in step 4 a error message appeared in the terminal.

-----------------------------------------------------------------
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: debian/cnijfilter-common/usr/lib/cups/filter/pstocanonij shouldn't be linked with libpopt.so.0 (it uses none of its symbols).
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cnijfilter-common-2.60: No such file or directory
-----------------------------------------------------------------

I assume that the instructions given by age6racer isn't for 64bit hardy. But, isn't there anything which can be done? And is it possible to use win printer drivers in hardy? :confused:

---

### Post by zrohtyzn on 2009-03-12
same problem :(

...bump.

---

