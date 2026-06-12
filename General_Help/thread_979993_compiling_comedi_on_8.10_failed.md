---
title: "compiling comedi on 8.10 failed"
date: 2008-11-12
forum: General Help
---

### Post by huseyinkozan on 2008-11-12
according to /usr/share/doc/comedi-source/README.Debian
giving this command
/usr/src# module-assistant auto-install comedi

```

make: Nothing to be done for `kdist_clean'.
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/comedi'
make[1]: Nothing to be done for `kdist_clean'.
make[1]: Nothing to be done for `kdist_config'.
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-7-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-7-generic/g ;s/#KVERS#/2.6.27-7-generic/g ; s/_KVERS_/2.6.27-7-generic/g ; s/##KDREV##/2.6.27-7.16/g ; s/#KDREV#/2.6.27-7.16/$
  done
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.27-7-generic/comedi
# Build the module
#/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux KVERS=2.6.27-7-generic
# Install the module
libtoolize --copy --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
libtoolize: Remember to add `LT_INIT' to configure.ac.
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
CFLAGS="-Wall -g -O2 -O2" ./configure \
                --host=i486-linux-gnu \
                --build=i486-linux-gnu \
                --with-rtaidir=/usr/lib/realtime \
                --enable-pcmcia
configure: error: cannot run /bin/bash ./config.sub
make[1]: *** [binary-modules] Error 1
make[1]: Leaving directory `/usr/src/modules/comedi'
make: *** [kdist_build] Error 2

```

and i tried this:
[http://groups.google.com/group/comedi_list/browse_thread/thread/7a3c118bc59470cc]("http://groups.google.com/group/comedi_list/browse_thread/thread/7a3c118bc59470cc")

after this:
/usr/src/modules/comedi# ./autogen.sh 

i got this:
```

configure.ac:6: installing `./config.guess'
configure.ac:6: installing `./config.sub'
Makefile.am:41: `:='-style assignments are not portable
Makefile.am:41: shell find $(srcdir: non-POSIX variable name
Makefile.am:41: (probably a GNU make extension)

```

the result was the same


also i tried download and compile packages from comedi.org and i failed again. and i don't want to use comedi.org's package for the difficulties about management of installed programs.

any suggestions ?

---

### Post by kikazaru on 2008-12-08
Try these instructions:

[http://www.comedi.org/wiki/Installation_on_Ubuntu](http://www.comedi.org/wiki/Installation_on_Ubuntu)

If you are worried about having a neat package, use this:

sudo checkinstall --fstrans=no --install=no make install


-you need to install checkinstall, and you may also need to correct some parameters which are badly parsed -just re-enter them without newlines. Anyway, it will build a package file which you can install with dpkg -i. Remember to run depmod -a when you've installed the kernel module package.

---

### Post by kakila on 2008-12-10
Hi,
Thanks for the suggestion, but still when running 'sh autogen.sh' there is an error. Anyway, I kept going....
I am using Xubuntu 8.10
After following those instructions complemented with this ones
[http://sorasora.wordpress.com/2007/11/05/install-comedi-on-kubuntu-710/](http://sorasora.wordpress.com/2007/11/05/install-comedi-on-kubuntu-710/)

I can modprobe comedi but comedi_config generates a segmentation fault.

Any solution

There is an issue that is probably related but I do not understand why the say is solved when it is not.
[https://bugs.launchpad.net/ubuntu/+source/comedi/+bug/5989](https://bugs.launchpad.net/ubuntu/+source/comedi/+bug/5989)

Thanks...

---

### Post by kikazaru on 2008-12-10
I got some errors from "sh autogen.sh", but it worked after that. Although there is a bug it seems: I can't get asynchronous output to work.

---

