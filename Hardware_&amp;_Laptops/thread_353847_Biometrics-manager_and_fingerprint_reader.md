---
title: "Biometrics-manager and fingerprint reader"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by samba on 2007-02-05
Hi,

I've been trying to configure the fingerprint reader on my laptop (Toshiba Portege M405) for a while by now, following the usual howto's [http://www.thinkwiki.org/index.php?title=How_to_enable_the_fingerprint_reader&redirect=no](http://www.thinkwiki.org/index.php?title=How_to_enable_the_fingerprint_reader&redirect=no) and [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader) , but I've always ran into all sorts of problems and never managed to get it working.

Now I just noticed that a new version of the pam_bioapi module has come up (see [http://linuxbiometrics.com/modules/news/article.php?storyid=8](http://linuxbiometrics.com/modules/news/article.php?storyid=8) : the source files are at [http://download.savannah.gnu.org/releases/pam-bioapi/](http://download.savannah.gnu.org/releases/pam-bioapi/) ), with a Gnome graphical interface called biometrics-manager, so I got very excited! :-) But that didn't work either; it looks like I could install the pam-bioapi module (although I haven't managed to be able to use it yet), but I couldn't install the biometrics-manager, since ./configure complained about some packages missing, while these packages were actually installed, so i don't know what to do. 

So I was just wondering: has anyone managed to use this biometrics-manager on Ubuntu (Edgy)? If so, how did you do it? And does anyone know if there is a plan of creating some ubuntu packages for some sort of fingerprint manager? That would be awesome! Unfortunately i do not have the required knowledge to do it myself...

Thanks :-)
Vincent

---

### Post by dalonso on 2007-02-05
I don't have a fingerprint reader but followed the links you posted only for curiosity. In the downloads page of the site they have a deb for de manager, have you tried to install it?

---

### Post by samba on 2007-02-05
Well, as far as i could tell there's only a .deb file for a patch to GDM so that it uses the fingerprint reader I think; I couldn't find a .deb file for the actual biometrics-manager and pam-bioapi. I tried the .deb for GDM, but it doesn't change anything.

Maybe I missed something; where did you see that .deb?

Cheers
vincent

---

### Post by moldy86 on 2007-03-01
i have a a135 series toshiba.. I tried everything i could find via google to get the finger print reader to work.. gave up.. 

but then it kept bugging me and found thinkfinger... Its made for ibms but works with sonys and toshibas. the site gives you everthing you need in the 2 documents on how to build it from source then install it which is very easy.. make sure to install mods into /etc/security. 
i had a little problem with the tf-tool. just move the lib its asking for to /usr/lib and all goes by great! any questions just pm me k

kevin kricfalusi

 :)

---

### Post by moldy86 on 2007-03-01
[http://thinkfinger.sourceforge.net/download.php](http://thinkfinger.sourceforge.net/download.php)

sorry go here

---

### Post by IcemanV9 on 2007-03-13
I followed the [[COLOR="Orange"]**wiki**[/COLOR]]("https://wiki.ubuntu.com/ThinkFinger?highlight=%28thinkfinger%29") on ThinkFinger. It was a tricky one for Dapper. It will fail the first time (and many times) since 0.2.2 will work with libusb 0.1.12 or above (0.1.10a on Dapper). I've reported the bug to the developer.

Now, it worked beautifully. The developer is working on it. So, I do not know when it will be updated with a fix.

---

### Post by samba on 2007-03-21
Thanks a lot for the link to the wiki, it now works beautifully! This is great!

Well I followed the wiki, the only thing that didn't work was the step "sudo tf-tool --verify", it said something like it could not verify, but it doesn't matter, now I can use the fingerprint reader to login gnome! :-)

youppi! :-)
samba

---

### Post by Lorenz on 2007-05-13
Great, I followed that Wiki as well.
Workes like a charm on a IBM T60 :)

---

### Post by Zebedee18F on 2007-05-22
Iam planning to get a lenovo / IBM usb fingerprint reader andplan to use think finger,but have a question or two.

Are you able to use it in conjuction with firefox for website passwords etc?

TIA for your help!

---

### Post by protenniser on 2007-07-03
H&#304; all,

I have tried to follow the instruction in the wiki in order to install that fingerprint reader, however there is a place I am blocked. After I have installed the dependecy packages and untared the driver, when it says I must configure the driver by writing "/configure --with-securedir=/lib/security --with-birdir=/etc/pam_thinkfinger". I wrote that command and it starts configuring however after some point, I get an error: "checking for USB... configure: error: libusb missing". I have checked that the libusb-dev package is correctly installed but it keeps giving this error. I am a complete newbie in ubuntu, so all help is appreciated. 
Btw, my laptop is toshiba tecra m7, maybe it could help.

Thanks for all help, regards...

---

### Post by Scotty562 on 2007-07-03
Is there any chance any of this would work with my HP dv6500's fingerprint reader?

---

### Post by drocra on 2007-08-19
> **protenniser said:**
> H&#304; all,

I have tried to follow the instruction in the wiki in order to install that fingerprint reader, however there is a place I am blocked. After I have installed the dependecy packages and untared the driver, when it says I must configure the driver by writing "/configure --with-securedir=/lib/security --with-birdir=/etc/pam_thinkfinger". I wrote that command and it starts configuring however after some point, I get an error: "checking for USB... configure: error: libusb missing". I have checked that the libusb-dev package is correctly installed but it keeps giving this error. I am a complete newbie in ubuntu, so all help is appreciated. 
Btw, my laptop is toshiba tecra m7, maybe it could help.

Thanks for all help, regards...

Make sure you have all of these packages installed:

build-essential
libtool
pkg-config
libpam-dev
libusb-dev (you already have this one)

I was having the same problem, and that fixed it.

---

### Post by kiwioperator on 2007-09-19
I am having a problem not mentioned anywhere I looked on installing thinkfinger. 
When I plug in sudo tf-tool --add user <username> (with my actual username without the <>)
it says "tf-tool: error while loading shared libraries: libthinkfinger.so.0: cannot open shared object file: No such file or directory"
I have followed the instructions and everything else appeared to work.

Can anyone help?

I have a Toshiba Portege M405 with feisty.

Thanks,
Kiwi

---

### Post by pau on 2007-09-20
You have to update the necessary links and cache to  the shared libraries you just installed: 

```
man ldconfig
```

man is your friend... well, in linux it's not the best thing, I have to admit. In any case, run sudo ldconfig and that's it

---

### Post by kiwioperator on 2007-09-20
Hmmm

This is what I got after sudo ldconfig and going through the whole process again.

kiwi@kiwi-laptop:~$ sudo ldconfig
Password:
kiwi@kiwi-laptop:~$ ls /lib/security
pam_access.so      pam_limits.so       pam_securetty.so    pam_unix_passwd.so
pam_debug.so       pam_listfile.so     pam_selinux.so      pam_unix_session.so
pam_deny.so        pam_localuser.so    pam_shells.so       pam_unix.so
pam_env.so         pam_mail.so         pam_stress.so       pam_userdb.so
pam_filter.so      pam_mkhomedir.so    pam_succeed_if.so   pam_warn.so
pam_foreground.so  pam_motd.so         pam_tally.so        pam_wheel.so
pam_ftp.so         pam_nologin.so      pam_thinkfinger.so  pam_xauth.so
pam_group.so       pam_permit.so       pam_time.so
pam_issue.so       pam_rhosts_auth.so  pam_unix_acct.so
pam_lastlog.so     pam_rootok.so       pam_unix_auth.so
kiwi@kiwi-laptop:~$ sudo tf-tool --acquire
tf-tool: error while loading shared libraries: libthinkfinger.so.0: cannot open shared object file: No such file or directory
kiwi@kiwi-laptop:~$ sudo tf-tool --add user kiw
tf-tool: error while loading shared libraries: libthinkfinger.so.0: cannot open shared object file: No such file or directory

kiwi@kiwi-laptop:~$ cd Desktop
kiwi@kiwi-laptop:~/Desktop$ ls
thinkfinger-0.3
kiwi@kiwi-laptop:~/Desktop$ cd thinkfinger-0.3
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ ./configure --with-securedir=/lib/security --with-birdir=/etc/pam_thinkfinger
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether gcc and cc understand -c and -o together... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking whether to build with USB hooks for debugging... no
checking whether to build the pluggable authentication module (PAM)... yes
checking security/pam_appl.h usability... yes
checking security/pam_appl.h presence... yes
checking for security/pam_appl.h... yes
checking security/pam_modules.h usability... yes
checking security/pam_modules.h presence... yes
checking for security/pam_modules.h... yes
checking for pam_start in -lpam... yes
checking for pam_prompt in -lpam... no
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking for linux/uinput.h... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for USB... yes
checking for doxygen... no

 ThinkFinger 0.3
 =================

 + prefix:              /usr/local
 + libdir:              /usr/local/lib
 + bindir:              /usr/local/bin
 + sbindir:             /usr/local/sbin
 + mandir:              /usr/local/share/man

 + cflags:              -g -O2 -Wall -fno-common -fPIC -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Wdeclaration-after-statement
 + libusb:              -lusb  

 Debugging
 =========

 + enable USB hooks:    no


 Build PAM module:      yes

 + libpam:              -lpam
 + libpthread:          -lpthread
 + securedir:           /lib/security
 + birdir:              /etc/pam_thinkfinger

configure: creating ./config.status
config.status: creating Makefile
config.status: creating README
config.status: creating INSTALL
config.status: creating docs/Makefile
config.status: creating docs/autodocs/Makefile
config.status: creating libthinkfinger/Makefile
config.status: creating libthinkfinger/libthinkfinger.pc
config.status: creating pam/Makefile
config.status: creating tf-tool/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ make
make  all-recursive
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3'
Making all in docs
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
Making all in autodocs
make[3]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[3]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[3]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
Making all in libthinkfinger
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
Making all in tf-tool
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
Making all in pam
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3'
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3'
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ sudo make install
Making install in docs
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
Making install in autodocs
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[3]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs/autodocs'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[3]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './tf-tool.1' '/usr/local/share/man/man1/tf-tool.1'
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './pam_thinkfinger.8' '/usr/local/share/man/man8/pam_thinkfinger.8'
make[3]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/docs'
Making install in libthinkfinger
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libthinkfinger.la' '/usr/local/lib/libthinkfinger.la'
/usr/bin/install -c .libs/libthinkfinger.so.0.0.0 /usr/local/lib/libthinkfinger.so.0.0.0
(cd /usr/local/lib && { ln -s -f libthinkfinger.so.0.0.0 libthinkfinger.so.0 || { rm -f libthinkfinger.so.0 && ln -s libthinkfinger.so.0.0.0 libthinkfinger.so.0; }; })
(cd /usr/local/lib && { ln -s -f libthinkfinger.so.0.0.0 libthinkfinger.so || { rm -f libthinkfinger.so && ln -s libthinkfinger.so.0.0.0 libthinkfinger.so; }; })
/usr/bin/install -c .libs/libthinkfinger.lai /usr/local/lib/libthinkfinger.la
/usr/bin/install -c .libs/libthinkfinger.a /usr/local/lib/libthinkfinger.a
chmod 644 /usr/local/lib/libthinkfinger.a
ranlib /usr/local/lib/libthinkfinger.a
libtool: install: warning: remember to run `libtool --finish /usr/lib'
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include"
 /usr/bin/install -c -m 644 'libthinkfinger.h' '/usr/local/include/libthinkfinger.h'
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'libthinkfinger.pc' '/usr/local/lib/pkgconfig/libthinkfinger.pc'
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/libthinkfinger'
Making install in tf-tool
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'tf-tool' '/usr/local/sbin/tf-tool'
libtool: install: warning: `../libthinkfinger/libthinkfinger.la' has not been installed in `/usr/lib'
/usr/bin/install -c .libs/tf-tool /usr/local/sbin/tf-tool
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/tf-tool'
Making install in pam
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/lib/security" || /bin/mkdir -p "/lib/security"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'pam_thinkfinger.so' '/lib/security/pam_thinkfinger.so'
libtool: install: warning: `../libthinkfinger/libthinkfinger.la' has not been installed in `/usr/lib'
/usr/bin/install -c .libs/pam_thinkfinger.so /lib/security/pam_thinkfinger.so
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3/pam'
make[1]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3'
make[2]: Entering directory `/home/kiwi/Desktop/thinkfinger-0.3'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3'
make[1]: Leaving directory `/home/kiwi/Desktop/thinkfinger-0.3'
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ sudo ldconfigkiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ sudo tf-tool --acquire
tf-tool: error while loading shared libraries: libthinkfinger.so.0: cannot open shared object file: No such file or directory
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ sudo tf-tool --add user kiwitf-tool: error while loading shared libraries: libthinkfinger.so.0: cannot open shared object file: No such file or directory
kiwi@kiwi-laptop:~/Desktop/thinkfinger-0.3$ 

What should I do in man ldconfig?

Thanks for your help
Kiwi

---

