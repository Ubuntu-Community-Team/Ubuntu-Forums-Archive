---
title: "problem installing from source"
date: 2005-11-25
forum: General Help
---

### Post by tikal26 on 2005-11-25
I am trying to install kdvdbackup and get the following error when I type
./configure --prefix=`kde-config --prefix`
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
what is X includes? any help would be greatly appreciated

---

### Post by Xian on 2005-11-25
Try installing the x-window-system-dev package.

---

### Post by tikal26 on 2005-11-25
ok thanks now I am getting this Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation! For more details about this problem, look at the end of config.log. I installed qt but there are many packages and libraries with qt on it. anyone knows what I need
update:
I was able to run the config file but now when I make I get a error 2

---

### Post by LaSSarD on 2005-11-28
try installing the kdelibs4-dev metapack ;)

---

### Post by daller on 2005-12-07
I have another problem:

running make, I get this:

```

configure.in:43: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:48: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:51: error: possibly undefined macro: AC_CHECK_COMPILERS
configure.in:52: error: possibly undefined macro: AC_ENABLE_SHARED
configure.in:53: error: possibly undefined macro: AC_ENABLE_STATIC
configure.in:58: error: possibly undefined macro: AM_KDE_WITH_NLS
configure.in:61: error: possibly undefined macro: AC_PATH_KDE
configure.in:70: error: possibly undefined macro: AC_CHECK_KDEMAXPATHLEN

```

I think it's because of a buggy extraction (Ark complained about something!)

edit: I extracted it from commandline instead (tar xfv kdvdbackup-0.6.tar.gz) - Is that wrong?

...The problem persists!

---

### Post by Zaventh on 2005-12-07
If there is a file called "autogen.sh" in the path, run it first. Else, look for a Makefile.cvs. If the latter case, run "make -f Makefile.cvs" before running configure.

---

### Post by daller on 2005-12-07
Now it's totally ruined!

See the output of make in the attached file!

---

### Post by Zaventh on 2005-12-07
Found your problem. The makefile looks for the dvdread library in the wrong place. Do this:

```
sudo ln -s /usr/include/dvdnav/ /usr/local/include/dvdread
```

Good luck.

---

### Post by daller on 2005-12-13
Well, I didn't solve it...

I read through the make output, and it is still complaining about dvdread!

frmdvdinfo.h:24:30: error: dvdread/ifo_read.h: No such file or directory!

---

### Post by skyboy on 2005-12-13
I would suggest to restart from beginning, using
tar xzf xxxx.gz from command line.
then :
1. make -f Makefile.cvs
 2. ./configure --prefix=`kde-config --prefix`
 3. make
 4. and finally make install

make sure you also have the libdvdread, nav, css and their -dev (development)  version

---

### Post by daller on 2005-12-13
Did that and installed automake1.9, and now I get this:

daniel@ubuntu:~/downloads/kdvdbackup$ make
/bin/sh ./config.status --recheck
running /bin/sh ./configure  --prefix=/usr  --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 1379: syntax error near unexpected token `kdvdbackup,'
./configure: line 1379: `AM_INIT_AUTOMAKE(kdvdbackup, 0.4)'
make: *** [config.status] Fejl 2

---

### Post by Zaventh on 2005-12-13
[QUOTE=daller]Well, I didn't solve it...

I read through the make output, and it is still complaining about dvdread!

frmdvdinfo.h:24:30: error: dvdread/ifo_read.h: No such file or directory![/QUOTE]

Have you installed libdvdread-dev and libdvdnav-dev? or whatever they are called...

---

### Post by skyboy on 2005-12-13
>  frmdvdinfo.h:24:30: error: dvdread/ifo_read.h: No such file or directory
I modified the files to refer to /usr/include/dvdread/* or /usr/include/dvdnav/*
I made a .deb file of it. If you want it, email me.
otherwise, modify the *.h file that refers to the wrong directories.
good luck

---

### Post by pixelnate on 2006-02-01
I have been following the info in this thread and I am still stuck. When executing make, it dies with this:
> /usr/share/qt3/include/private/qucom_p.h: At global scope:
/usr/share/qt3/include/private/qucom_p.h:69: warning: ‘struct QUBuffer’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: ‘struct QUType’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: ‘struct QUType_Null’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: ‘struct QUType_enum’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: ‘struct QUType_ptr’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: ‘struct QUType_iface’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: ‘struct QUType_idisp’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: ‘struct QUType_bool’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: ‘struct QUType_int’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: ‘struct QUType_double’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: ‘struct QUType_charstar’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: ‘struct QUType_QString’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: ‘struct QUType_QVariant’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: ‘struct QUType_varptr’ has virtual functions but non-virtual destructor
make[2]: *** [frmmainform.o] Error 1
make[2]: Leaving directory `/home/pixelnate/Desktop/installs/kdvdbackup/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pixelnate/Desktop/installs/kdvdbackup'
make: *** [all] Error 2


Anybody have any thoughts? Thx, pixelnate.

---

### Post by pixelnate on 2006-02-02
Nevermind. I figured it out. I had to move the dvd_udf.h file to /usr/include/dvdread/ and then add the libacl (dev) and libattr (dev) libraries in adept. Then started the whole process over with Skyboy's step by step instrux, and voila, it works.

Man, what a pain in the butt to get this thing installed. I was about to give up when I got the messages about the missing libraries, but I am glad I didn't. Now I just have to figure out how to get it to work properly with DvdShrink and I will be solid.

Thanks all. \\:D/

---

