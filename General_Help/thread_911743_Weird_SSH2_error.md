---
title: "Weird SSH2 error"
date: 2008-09-05
forum: General Help
---

### Post by Nitroware on 2008-09-05
Hey all, Im trying to install ssh2 for php, and everything has run smoothly, until I get to the make part (yes i did ./configure):


```
make[3]: Entering directory `/root/Downloads/libssh2/example/simple'
if gcc -DHAVE_CONFIG_H  -I. -I../../include    -g -O2 -I/usr/local/ssl/include -MT ssh2.o -MD -MP -MF ".deps/ssh2.Tpo" -c -o ssh2.o ssh2.c; \
	then mv -f ".deps/ssh2.Tpo" ".deps/ssh2.Po"; else rm -f ".deps/ssh2.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2 -I/usr/local/ssl/include  -L/usr/local/ssl/lib -lcrypto -o ssh2  ssh2.o ../../src/libssh2.la 
mkdir .libs
gcc -g -O2 -I/usr/local/ssl/include -o .libs/ssh2 ssh2.o  -L/usr/local/ssl/lib -lcrypto ../../src/.libs/libssh2.so  -Wl,--rpath -Wl,/usr/local/lib
../../src/.libs/libssh2.so: undefined reference to `dlsym'
../../src/.libs/libssh2.so: undefined reference to `dlerror'
../../src/.libs/libssh2.so: undefined reference to `dlopen'
../../src/.libs/libssh2.so: undefined reference to `dlclose'
collect2: ld returned 1 exit status
make[3]: *** [ssh2] Error 1
make[3]: Leaving directory `/root/Downloads/libssh2/example/simple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/Downloads/libssh2/example/simple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Downloads/libssh2/example'
make: *** [all-recursive] Error 1

```

I looked it up on google, and nothing.  Any ideas?  IO think this is the problem:
../../src/.libs/libssh2.so: undefined reference to `dlclose'

THanks in advance!

---

### Post by tamoneya on 2008-09-05
this thread looks pretty similar.
[http://www.linuxquestions.org/questions/slackware-14/undefined-reference-to-dlopen-dlclose-dlsym-and-dlerror-350945/](http://www.linuxquestions.org/questions/slackware-14/undefined-reference-to-dlopen-dlclose-dlsym-and-dlerror-350945/)
Try this command:```
sudo apt-get install libdb-devel

```

---

### Post by Nitroware on 2008-09-06
> **tamoneya said:**
> this thread looks pretty similar.
[http://www.linuxquestions.org/questions/slackware-14/undefined-reference-to-dlopen-dlclose-dlsym-and-dlerror-350945/](http://www.linuxquestions.org/questions/slackware-14/undefined-reference-to-dlopen-dlclose-dlsym-and-dlerror-350945/)
Try this command:```
sudo apt-get install libdb-devel

```
nope, didnt do anything.  Same problem.  BTW, it didnt find libdb-devel, it found libdbi-devel though, but i already had it.  I still tried it, and no difference.

---

